Operator_O für KSODI-Standard-Eval und KSODI-Full 01/2026




🟦 KSODI-Standard-Eval

Operator O₀ – Observable Objectivity (Grounding relativ zu Retrieval)

1️⃣ Annahmen (explizit & restriktiv)

    LLM ist Black Box; Hersteller-Prompts unbekannt.
    Beobachtbar sind: User/Assistant-Text, eigener Systemprompt, Toolprofile, Retrieval-Set (Top-k), Tool-Outputs (falls im Kontext genutzt).
    Keine Wahrheitsprüfung in der Welt (keine Web-Recherche als Bestandteil von O₀).
    Objektivität bedeutet hier nicht “wahr”, sondern:
    „Aussagen sind im sichtbaren Kontext belegbar / ableitbar“.

2️⃣ Beschreibung (funktional)

O₀ misst, wie stark ein Chunk (typisch: die Assistant-Antwort) auf beobachtbaren, bereitgestellten Quellen basiert:

    passt semantisch zu Retrieval?
    enthält nachvollziehbare Ableitung?
    vermeidet “freie” Behauptungen ohne Stütze?

O₀ ist damit ein Grounding-Score – kein Wahrheits- oder Qualitätsurteil.

3️⃣ Mathematische Formulierung (MVP, erklärbar)

Wir zerlegen O₀ in drei Teile:

(A) Retrieval-Alignment (A_{\text{ret}})

Wie gut passt der Chunk zu den gelieferten Retrieval-Dokumenten?

    embed Antwort (a) → (\vec e(a))
    embed jedes Retrieval-Doc (d_i) → (\vec e(d_i))

[
A_{\text{ret}}(a)=\max_i \cos(\vec e(a), \vec e(d_i))
]

Interpretation:
hoch = Antwort ist inhaltlich eng am Retrieval,
niedrig = Antwort driftet weg.


(B) Attribution/Traceability (T) (transparent, heuristisch)

Wie stark zeigt der Text Beleg-/Ableitungssignale?

MVP-Heuristik (ohne Fingerprint, ohne Stilwertung): Zähle Attributionsmarker:

    „laut“, „gemäß“, „im Dokument“, „in Abschnitt“, „Quelle“, „siehe“, „steht in…“
    Zitate/Referenzen (z. B. „…“ oder [1], (Kap. 2))
    explizite Verweisstrukturen (“wie oben”, “aus den Punkten 1–3 folgt”)

[
T(a)=\mathrm{clip}\left(\frac{n_{\text{attrib}}}{n_{\text{sent}}+1}, 0, 1\right)
]

Wichtig: T ist kein Sprachstil-Score, sondern “gibt der Text eine Spur?”.


(C) Unsupported-Claim Penalty (U) (keine Weltprüfung, nur Kontextprüfung)

Wir bestrafen behauptungsartige Sätze, die weder

    semantisch im Retrieval verankert sind noch
    eine Ableitungsspur enthalten.

Operationalisierung (MVP):

    Splitte Antwort in Sätze (s_j)
    Für jeden Satz:
        (align_j = \max_i \cos(\vec e(s_j), \vec e(d_i)))
        (attrib_j = 1) wenn Satz Attributionsmarker hat, sonst 0
    “Unsupported” wenn (align_j < \tau) und (attrib_j=0)

[
U(a)=\frac{#{j:, align_j<\tau \land attrib_j=0}}{n_{\text{sent}}}
]

mit z. B. (\tau = 0.35) (startwert; später empirisch kalibrieren).


Gesamtformel

[
O_0(a\mid RET)=\mathrm{clip}\left(
\alpha A_{\text{ret}}(a)

    \beta T(a)
    \gamma U(a),
    ,0,1\right)
    ]

Startgewichte (pragmatisch, erklärbar):

    (\alpha=0.6) (Grounding ist Kern)
    (\beta=0.2) (Traceability)
    (\gamma=0.2) (Penalty)

4️⃣ Semantische Erklärung

    (A_{\text{ret}}): “Ist die Antwort thematisch gestützt?”
    (T): “Kann man im Text sehen, worauf sie sich stützt?”
    (U): “Wie viel wirkt wie freie Behauptung relativ zum sichtbaren Material?”

5️⃣ Erwartetes Ergebnis

    (O_0 \in [0,1])
    hoch: retrieval-basiert, nachvollziehbar, wenig freie Behauptungen
    niedrig: driftig, unbelegt (im Kontext), viele “freie” Sätze

6️⃣ Vergleichbares erwartetes Ergebnis

Vergleichbar:

    verschiedene Antworten bei gleichem Retrieval-Set
    Modelle bei gleicher Retrieval-Konfiguration
    dieselbe Frage mit anderem Retrieval (zeigt “Grounding-Qualität” des RAG)

Nicht vergleichbar:

    Antworten mit völlig unterschiedlichem Retrieval und ohne Dokumentation des RET
    Setups, in denen Tool-Output im Kontext ist, aber nicht in (\mathcal{R}) einfließt



_______



🧩 Implementierungsidee (eure n8n/RAG/Python-Strecke)

Inputs:

    a_text
    retrieved_docs[] (id + text)
    optional: tool_outputs[] (falls als Kontext genutzt → dann als zusätzliche docs behandeln)

Compute:

    embeddings für a_text und für alle retrieved_docs
    Satzsplit für a_text, Satz-Embeddings für s_j (für U)

Store:

    O0_assistant
    Komponenten: A_ret, T, U
    retrieval_doc_ids
    Parameter: tau, weights, embedding_model_id

Audit ist damit sofort möglich.



______


Damit du sicher bist, hier die Developer-Checkliste “O₀ in 30 Minuten verstanden”:


O₀ Implementierung – Minimal klar

Inputs (pro Turn)

    a_text (Assistant Output)
    retrieved_docs[] = {id, text} (Top-k, exakt dieses Turn)
    optional: tool_outputs[] wie zusätzliche docs (nur wenn sie im Prompt-Kontext waren)
    embedding_model_id, tau, weights

Schritte

    Embeddings

    e_a = embed(a_text)
    e_di = embed(doc_text) für jedes Retrieval-Doc
    Satzsplit a_text -> s_j und e_sj = embed(s_j) (nur für U)

    A_ret (Grounding)

    A_ret = max_i cosine(e_a, e_di)

    T (Traceability)

    Regex-Zähler für Attributionsmarker (kleine Wortliste reicht)
    T = clip(n_attrib / (n_sent + 1), 0, 1)

    U (Unsupported Penalty)

    pro Satz:
        align_j = max_i cosine(e_sj, e_di)
        attrib_j = 1 if marker_in_sentence else 0
        unsupported wenn align_j < tau AND attrib_j == 0
    U = unsupported_count / n_sent

    O0

    O0 = clip(alpha*A_ret + beta*T - gamma*U, 0, 1)

Store (für Audit!)

    O0, plus A_ret, T, U
    retrieval_doc_ids
    tau, weights, embedding_model_id

Startwerte

    tau = 0.35
    weights = (0.6, 0.2, 0.2)

Edge Cases

    wenn retrieved_docs leer → O0 nicht berechnen oder A_ret=0 und kennzeichnen
    bei n_sent=0 → T=0, U=0


KRITIK: (und wie man es abfängst):

    „T ist heuristisch“ → ja, bewusst: Transparenz. Später optional LLM-Classifier, aber Standard-Eval bleibt erklärbar.
    „tau ist willkürlich“ → Startwert, wird empirisch kalibriert. tau+weights werden versioniert gespeichert.





🟧 KSODI-Full

Operator O – Dynamic Objectivity (über Zeit, Quellen, Checks)

1️⃣ Annahmen (zusätzlich)

    Sequenzen von Turns verfügbar
    optional externe Checks (Web, interne Wissensdatenbanken, Tools)
    Ziel: Objektivität als Stabilität unter Prüfung
    (Konsistenz, Korrekturfähigkeit, Quellenqualität, Drift-Resistenz)

2️⃣ Beschreibung

O(t) bewertet, ob Aussagen

    konsistent bleiben,
    sich bei Gegenbelegen korrigieren,
    in belastbare Quellen eingebettet sind,
    unter Variation des Kontextes stabil bleiben.

3️⃣ Mathematische Formulierung (Full)

Wir nehmen O₀ als Grundbaustein und ergänzen:

    Cross-turn Consistency (C_{\text{turn}}(t))
    Correction Responsiveness (R_{\text{corr}}(t))
    External Verification (V_{\text{ext}}(t)) (optional)

[
O(t)=\mathrm{clip}\Bigl(
w_0 O_0(t)

    w_1 C_{\text{turn}}(t)
    w_2 R_{\text{corr}}(t)
    w_3 V_{\text{ext}}(t)
    \lambda \Delta_{\text{drift}}(t),
    ,0,1\Bigr)
    ]

Semantische Erklärung:

    (C_{\text{turn}}): Widerspruchsfreiheit über Zeit
    (R_{\text{corr}}): Fähigkeit zur Selbstkorrektur bei neuen Belegen
    (V_{\text{ext}}): Abgleich mit externen Quellen (wenn erlaubt)
    Drift-Term wie gehabt

4️⃣ Erwartetes Ergebnis (Full)

    Objektivitätskurve + “Prüf-Events”
    sichtbar: robust vs. fragil; korrigiert vs. verteidigt Halluzination

5️⃣ Vergleichbarkeit (Full)

Nur in kontrollierten Setups (gleiche Prüfregeln, gleiche Toolzugriffe).


🔧 Mini-Review (damit Patrick/Benjamin happy sind)

    O₀ ist Grounding relativ zu RET, keine “Wahrheit”.
    Nur beobachtbar: Embeddings + Retrieval + Textmarker.
    Parameter (tau, weights) werden gespeichert → reproduzierbar.
    Keine Person, kein Fingerprinting.
