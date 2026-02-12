Operator_D für KSODI-Standard-Eval und KSODI-Full 01/2026




🟦 KSODI-Standard-Eval

Operator D₀ – Observable Clarity

1) Annahmen

    Wir sehen nur: Text (Chunks), eigenen Systemprompt/Tool-Instruktionen, Retrieval-Set.
    Keine Intention, keine Person, keine “Tone-of-voice”-Bewertung.
    D₀ ist eine technische Verständlichkeits-/Eindeutigkeitsmetrik im beobachtbaren Signal.

2) Beschreibung

D₀ misst, wie eindeutig referenzierbar und operational anschlussfähig ein Chunk ist – relativ zu einem expliziten Referenzraum (\mathcal{R}).
Kernidee: Ein Text kann informationsreich sein (I₀ hoch) und trotzdem undeutlich (D₀ niedrig).

3) Mathematische Formulierung (minimal & erklärbar)

Wir zerlegen D₀ in drei beobachtbare Komponenten:

    Referenz-Kohärenz (passt der Chunk überhaupt zum sichtbaren Kontext?)
    [
    C(q\mid\mathcal{R})=\cos(\vec e(q),\vec e(\mathcal{R}))
    ]
    Ambiguitäts-Strafe (wie “schwammig” ist der Chunk in sich?)
    Pragmatischer, embedding-basierter Proxy über Streuung von Satz-Embeddings:

    Splitte (q) in Sätze (s_i), berechne (\vec e(s_i))
    Varianz/Dispersion (\mathrm{Var}({\vec e(s_i)})) als Mehrdeutigkeits-/Sprungmaß

[
A(q)=\mathrm{clip}(\mathrm{Var}({\vec e(s_i)}),0,1)
]

    Operationalitäts-Score (enthält der Chunk handhabbare Anker?)
    Minimaler, erklärbarer Heuristik-Score (ohne Person):

    zählt beobachtbare “Anker”: Zahlen, eindeutige Entitäten, konkrete Constraints, eindeutige Verben (z. B. liste, berechne, definiere), explizite Outputs (Tabelle, Formel, JSON)
    [
    O(q)=\mathrm{clip}\left(\frac{n_{\text{anker}}}{n_{\text{token}}},0,1\right)
    ]

Gesamtformel:
[
D_0(q\mid\mathcal{R})=
\alpha\cdot C(q\mid\mathcal{R})
+\beta\cdot O(q)
-\gamma\cdot A(q),
\quad \alpha+\beta+\gamma=1,;\alpha,\beta,\gamma\ge 0
]

4) Semantische Erklärung

    (C) sorgt dafür, dass “klar” nicht heißt “sprachlich hübsch”, sondern kontextpassend.
    (A) bestraft Sprünge/Mehrdeutigkeit innerhalb des Chunks (ohne Wahrheit zu bewerten).
    (O) belohnt konkrete Arbeitsfähigkeit des Texts.

5) Erwartetes Ergebnis

    (D_0 \in [0,1])
    hoch: eindeutig, referenzierbar, anschlussfähig
    niedrig: vage, sprunghaft, schwer operationalisierbar

6) Vergleichbares erwartetes Ergebnis

Vergleichbar:

    verschiedene Chunks gegen denselben (\mathcal{R})
    Q vs A (User vs Assistant) in einem Turn
    verschiedene Modelle in identischer Retrieval-/Prompt-Lage

Nicht vergleichbar:

    unterschiedliche Referenzräume (andere Systemprompt-/Retrieval-Konfiguration)



________


D₀ in der Annahme-Strecke: Wo rein, wann, welche Inputs/Outputs?

1) Wo sitzt D₀?

Nach der Antwort (oder nach jedem Turn), genau wie I₀.

    n8n orchestriert Capture → Retrieval → LLM → Store
    Danach ruft n8n Python Eval Service auf:
        compute_I0(...)
        compute_D0(...)
    Ergebnis wird als Eval-Record zurück in DB geschrieben

👉 D₀ ist nicht im Prompting und nicht im Modell, sondern in der Beobachtungsschicht.


2) Minimale Daten, die D₀ braucht (Standard-Eval-konform)

Inputs (pro Turn):

    q_text (User-Chunk)
    a_text (Assistant-Chunk)
    system_prompt_id oder Text (besser ID + Lookup)
    tool_profile_id oder Tool-Instruktions-Text (kurz, normiert)
    retrieved_docs: Liste von {doc_id, doc_text} für genau diesen Turn (Top-k)

Optional (aber okay):

    chunk_id, turn_id, session_id (random, nicht personenbezogen)

Keine Zeit nötig. Kein Userprofil. Keine Historie.


3) Was ist der Referenzraum (\mathcal{R}) für D₀ (konkret)?

Für D₀ denselben Referenzbaukasten wie bei I₀, damit alles auditierbar bleibt:

[
\mathcal{R} = SP \oplus TC \oplus RET_k(q)
]

In Code/Infra heißt das:

    R_text = concat(system_prompt_text, tool_profile_text, join(retrieved_docs_texts))
    Embedding davon: e_R

👉 Wichtig: D₀ ist relativ zu dem, was das System tatsächlich sichtbar bereitstellt.


4) D₀ Komponenten — implementierbar & erklärbar



(A) Kontextkohärenz (C)

Was: passt der Chunk semantisch zur sichtbaren Grundlage?

    e_q = embed(q_text)
    e_a = embed(a_text)
    e_R = embed(R_text)
    C_q = cosine(e_q, e_R)
    C_a = cosine(e_a, e_R)

Erklärung: “Wie gut passt der Text zur bekannten Aufgaben-/Wissensbasis?”


(B) Ambiguität/”Sprunghaftigkeit” (A) — ohne fancy NLP

Robust und simpel ist:

MVP-Proxy (empfohlen): Satz-Embeddings und Streuung.

    splitte Text in Sätze s_i (simple Regex reicht fürs MVP)
    embed jeden Satz: e_i
    berechne mittlere Kosinus-Ähnlichkeit zum Satzmittel:
        e_mean = mean(e_i)
        dispersion = mean(1 - cosine(e_i, e_mean))
    normiere in [0,1] (clip)

Das ist transparent: “Wie stark springt der Text in verschiedene semantische Richtungen?”

Vorteil: keine Personenmerkmale, keine Stilfeatures, kein Fingerprint.
Nachteil: sehr kurze Texte können noisy sein → dann fallback: A=0 oder A=small.


(C) Operationalität (O) — als erklärbarer „Anker“-Score

Hier gibt’s zwei Wege:

MVP (heuristisch, super erklärbar):

    zähle “Anker” im Text:
        Zahlen/Datumsformate (\d, ISO-Date)
        Aufzählungsmarker (1., -, •)
        explizite Output-Wörter (Tabelle, JSON, Liste, Schritte, Formel)
        Constraints (“mindestens”, “maximal”, “genau”, “Format:”)
    O = clip( anchors / tokens , 0, 1) (oder anchors / (anchors + k))

Noch besser (aber optional):
Extrahiere aus Systemprompt/Toolprofil erwartete Outputform (z.B. JSON) und prüfe einfache “conformance”. Das gehört eigentlich eher zu S₀, daher MVP reicht.


5) Die D₀-Formel als MVP

Keine 100 Parameter. Ich nehme drei Gewichte, die man erklären kann:

[
D_0 = \mathrm{clip}\left(
\alpha C + \beta O - \gamma A,; 0,1
\right)
]

Startwerte (pragmatisch):

    (\alpha=0.5) (Kohärenz ist Hauptsache)
    (\beta=0.3) (Operationalität)
    (\gamma=0.2) (Ambiguität-Strafe)

👉 Frage: “zu heuristisch”?
D₀ ist Standard-Eval, erklärbar, auditierbar; Heuristiken sind gewollt.
Und man kann später empirisch justieren.


6) Outputs speichern (für Audit / Debug)

Pro Turn (für q und a getrennt):

    D0_user, D0_assistant
    C_user, O_user, A_user
    C_assistant, O_assistant, A_assistant
    reference_ids (retrieval doc ids)
    system_prompt_id, tool_profile_id
    optional: sentence_count (nur zur Stabilitätsprüfung)

So kann man im Dashboard sehen, warum D₀ so ausfiel.


7) Edge Cases (damit einem nichts um die Ohren fliegt)

    Sehr kurzer Text (≤ 1 Satz): setze A=0 oder A=small (sonst “Streuung” unsinnig)
    Kein Retrieval (RET leer): R_text = SP + TC (noch immer definierter Referenzraum)
    Tool-Output sehr technisch: entscheidet, ob Tool-Output in R darf; sonst nur SP+TC+RET.


8) n8n Integration (Payload)

n8n schickt an Python-Eval:

{

  "turn_id": "...",

  "q_text": "...",

  "a_text": "...",

  "system_prompt_id": "...",

  "tool_profile_id": "...",

  "retrieved_docs": [{"id":"d1","text":"..."}, {"id":"d2","text":"..."}]

}

Python antwortet:

{

  "D0_user": 0.62,

  "D0_assistant": 0.71,

  "components": {

    "user": {"C":0.58,"O":0.31,"A":0.05},

    "assistant": {"C":0.66,"O":0.42,"A":0.09}

  }

}


✅ Kurz:

    vollständig beobachtbar
    auditierbar bis zur Referenz-ID
    keine Person, kein Stilfingerprint
    technisch implementierbar mit Embeddings + einfachem Textsplit
    die “Heuristik” ist nicht Schwäche, sondern Transparenz-Design







🟧 KSODI-Full

Operator D – Dynamic Clarity

1) Annahmen (zusätzlich)

    Zugriff auf Sequenzen (Turns), optional Zeit/Takt/Voice-Marker
    Modellierung von Drift, Rückfragen, Korrekturen, Selbstwiderspruch
    Ziel: Deutlichkeit als Verlaufseigenschaft, nicht nur Momentaufnahme

2) Beschreibung

D(t) misst die Stabilität von Bedeutungsankern über Zeit:

    bleiben Referenten stabil?
    werden Begriffe konsistent verwendet?
    führen Nachfragen zu Präzisierung (D steigt) oder zu Drift (D fällt)?

3) Mathematische Formulierung (Full)

Wir nutzen wieder Grundstruktur, aber mit Verlauf:

[
D(t)=
\alpha\cdot C(t)
+\beta\cdot O(t)
-\gamma\cdot A(t)
-\delta\cdot \Delta_{\text{drift}}(t)
]

mit Drift-Term über Änderung der semantischen Richtung:

[
\Delta_{\text{drift}}(t)=
1-\cos(\vec R_{t-1},\vec R_t)
]

Optional: Korrektur-/Rückfrage-Bonus (wenn Klarheit durch Nachfrage steigt):
[
B(t)=\max(0, D(t)-D(t-1))
]

4) Erwartetes Ergebnis

    Deutlichkeit als Kurve über Zeit
    sichtbar: “präzisiert sich” vs “zerfasert”

5) Vergleichbarkeit

Nur in kontrollierten Umgebungen (gleiches Prompting, gleiches Tooling, gleiche Gewichtungen).


🔧 Mini-Check: Warum D als nächster Operator?

Weil D₀ in deinem Python/RAG-Setting sofort andockt:

    basiert auf Embeddings + Retrieval + simple Heuristiken
    keine Person
    sehr erklärbar (Audit: “Anker, Kohärenz, Ambiguität”)


Nächster Schritt (deine Wahl, ohne Rückfrage-Orgie)

Wir können danach entweder:

    O₀ (Objektivität) als “Beleg-/Grounding-Grad relativ zu Retrieval” bauen, oder
    S₀ (Struktur) als “Format-/Gliederungs-/Constraint-Erfüllung”, oder
    direkt K₀ (Kontext) als “Vollständigkeit der bereitgestellten Rahmenbedingungen”.

Wenn du im I→K-Flug bleibst, wäre die Reihenfolge meist:
I₀ → D₀ → O₀ → S₀ → K₀.







D₀ in der Annahme-Strecke: Wo rein, wann, welche Inputs/Outputs?

1) Wo sitzt D₀?

Nach der Antwort (oder nach jedem Turn), genau wie I₀.

    n8n orchestriert Capture → Retrieval → LLM → Store
    Danach ruft n8n Python Eval Service auf:
        compute_I0(...)
        compute_D0(...)
    Ergebnis wird als Eval-Record zurück in DB geschrieben

👉 D₀ ist nicht im Prompting und nicht im Modell, sondern in der Beobachtungsschicht.


2) Minimale Daten, die D₀ braucht (Standard-Eval-konform)

Inputs (pro Turn):

    q_text (User-Chunk)
    a_text (Assistant-Chunk)
    system_prompt_id oder Text (besser ID + Lookup)
    tool_profile_id oder Tool-Instruktions-Text (kurz, normiert)
    retrieved_docs: Liste von {doc_id, doc_text} für genau diesen Turn (Top-k)

Optional (aber okay):

    chunk_id, turn_id, session_id (random, nicht personenbezogen)

Keine Zeit nötig. Kein Userprofil. Keine Historie.


3) Was ist der Referenzraum (\mathcal{R}) für D₀ (konkret)?

Für D₀ nehmt ihr denselben Referenzbaukasten wie bei I₀, damit alles auditierbar bleibt:

[
\mathcal{R} = SP \oplus TC \oplus RET_k(q)
]

In Code/Infra heißt das:

    R_text = concat(system_prompt_text, tool_profile_text, join(retrieved_docs_texts))
    Embedding davon: e_R

👉 Wichtig: D₀ ist relativ zu dem, was das System tatsächlich sichtbar bereitstellt.


4) D₀ Komponenten — implementierbar & erklärbar

(A) Kontextkohärenz (C)

Was: passt der Chunk semantisch zur sichtbaren Grundlage?

    e_q = embed(q_text)
    e_a = embed(a_text)
    e_R = embed(R_text)
    C_q = cosine(e_q, e_R)
    C_a = cosine(e_a, e_R)

Erklärung: “Wie gut passt der Text zur bekannten Aufgaben-/Wissensbasis?”


(B) Ambiguität/”Sprunghaftigkeit” (A) — ohne fancy NLP

Du brauchst hier etwas, das robust und simpel ist.

MVP-Proxy (empfohlen): Satz-Embeddings und Streuung.

    splitte Text in Sätze s_i (simple Regex reicht fürs MVP)
    embed jeden Satz: e_i
    berechne mittlere Kosinus-Ähnlichkeit zum Satzmittel:
        e_mean = mean(e_i)
        dispersion = mean(1 - cosine(e_i, e_mean))
    normiere in [0,1] (clip)

Das ist transparent: “Wie stark springt der Text in verschiedene semantische Richtungen?”

Vorteil: keine Personenmerkmale, keine Stilfeatures, kein Fingerprint.
Nachteil: sehr kurze Texte können noisy sein → dann fallback: A=0 oder A=small.


(C) Operationalität (O) — als erklärbarer „Anker“-Score

Hier gibt’s zwei Wege:

MVP (heuristisch, super erklärbar):

    zähle “Anker” im Text:
        Zahlen/Datumsformate (\d, ISO-Date)
        Aufzählungsmarker (1., -, •)
        explizite Output-Wörter (Tabelle, JSON, Liste, Schritte, Formel)
        Constraints (“mindestens”, “maximal”, “genau”, “Format:”)
    O = clip( anchors / tokens , 0, 1) (oder anchors / (anchors + k))

Noch besser (aber optional):
Extrahiere aus Systemprompt/Toolprofil erwartete Outputform (z.B. JSON) und prüfe einfache “conformance”. Das gehört eigentlich eher zu S₀, daher MVP reicht.


5) Die D₀-Formel als MVP

Ihr wollt keine 100 Parameter. Ich nehme drei Gewichte, die man erklären kann:

[
D_0 = \mathrm{clip}\left(
\alpha C + \beta O - \gamma A,; 0,1
\right)
]

Startwerte (pragmatisch):

    (\alpha=0.5) (Kohärenz ist Hauptsache)
    (\beta=0.3) (Operationalität)
    (\gamma=0.2) (Ambiguität-Strafe)



6) Outputs, die ihr speichern solltet (für Audit / Debug)

Pro Turn (für q und a getrennt):

    D0_user, D0_assistant
    C_user, O_user, A_user
    C_assistant, O_assistant, A_assistant
    reference_ids (retrieval doc ids)
    system_prompt_id, tool_profile_id
    optional: sentence_count (nur zur Stabilitätsprüfung)


7) Edge Cases (damit euch nichts um die Ohren fliegt)

    Sehr kurzer Text (≤ 1 Satz): setze A=0 oder A=small (sonst “Streuung” unsinnig)
    Kein Retrieval (RET leer): R_text = SP + TC (noch immer definierter Referenzraum)
    Tool-Output sehr technisch: entscheidet, ob Tool-Output in R darf; sonst nur SP+TC+RET.


8) n8n Integration (Payload)

n8n schickt an Python-Eval:

{

  "turn_id": "...",

  "q_text": "...",

  "a_text": "...",

  "system_prompt_id": "...",

  "tool_profile_id": "...",

  "retrieved_docs": [{"id":"d1","text":"..."}, {"id":"d2","text":"..."}]

}

Python antwortet:

{

  "D0_user": 0.62,

  "D0_assistant": 0.71,

  "components": {

    "user": {"C":0.58,"O":0.31,"A":0.05},

    "assistant": {"C":0.66,"O":0.42,"A":0.09}

  }

}


✅ Kurz: Warum das “renommée-sicher” ist

    vollständig beobachtbar
    auditierbar bis zur Referenz-ID
    keine Person, kein Stilfingerprint
    technisch implementierbar mit Embeddings + einfachem Textsplit
    die “Heuristik” ist nicht Schwäche, sondern Transparenz-Design


Wenn du sagst: “Passt, weiter mit O₀”, dann gehe ich als nächstes genauso vor:

    O₀ Standard (Grounding relativ zu Retrieval)
    O Full (Quellen-/Wahrheitsarbeit, Drift, externe Checks)
    und wieder mit konkreter Einbau-Idee für eure RAG/n8n-Strecke. 





⸻


Dev-Annex I


Implementing Operator I₀ (Observable Information Impulse)


Geltungsbereich:

Dieser Dev-Annex beschreibt eine minimale, realistisch umsetzbare Implementierung von Operator I₀ in API-basierten Agentensystemen, ohne Zugriff auf interne Modellzustände und ohne personenbezogene Auswertung.


⸻


DI.1 Architekturposition von I₀


I₀ ist kein Modell-Feature.

I₀ ist eine Beobachtungs- und Evaluationsfunktion, die nach der Modellantwort berechnet wird.


Position im Stack:


User / Tool Input

        ↓

Systemprompt + RAG + Tools

        ↓

LLM API Call

        ↓

LLM Output

        ↓

───────────────

I₀ Evaluation

───────────────

        ↓

Logging / Reporting / Monitoring


I₀ darf nicht:

	•	im Prompt stehen

	•	das Modell steuern

	•	zur Online-Optimierung verwendet werden


⸻


DI.2 Trigger: Wann wird I₀ berechnet?


Standard-Trigger (empfohlen)

	•	pro Turn, sobald folgende Artefakte vorliegen:

	•	User-Chunk

	•	Assistant-Chunk

	•	Retrieval-IDs (Top-k)

	•	Systemprompt-ID


Optional

	•	pro Chunk (Streaming / Long-Form Answers)

	•	sinnvoll bei Drift- oder Ausscheren-Analysen


⸻


DI.3 Minimal erforderliche Daten (Standard-Eval)


Feld	Zweck

session_id	zufällig / rotierend (nicht personenbezogen)

turn_id	technische Zuordnung

role	user / assistant

text	beobachtbarer Chunk

system_prompt_id	Referenz auf bekannten Prompt

tool_profile_id	optional (Policy-Kontext)

retrieval_ids	IDs der tatsächlich verwendeten RAG-Chunks

embedding_model_id	Reproduzierbarkeit

timestamp	optional (nicht für Bewertung genutzt)


👉 Explizit ausgeschlossen:

User-IDs, IPs, Style-Features, Langzeitprofile.


⸻


DI.4 Technischer Referenzraum \mathcal R


Für die Implementierung gilt:


\mathcal R_t = SP \oplus TP \oplus RET_k(q_t)


Technische Umsetzung:


R_text = concat(

    system_prompt_text,

    tool_profile_summary,   # optional

    retrieved_chunk_texts   # genau die Top-k

)


Für Embeddings:


e(R) = mean(

    e(system_prompt),

    e(tool_profile),        # optional

    mean(e(retrieved_chunks))

)



⸻


DI.5 Berechnung der Teilkomponenten


DI.5.1 Embeddings

	•	API-Embedding (z. B. OpenAI, Gemini, etc.) oder

	•	lokales Embedding-Modell

	•	einheitliches Modell pro Vergleich (sonst nicht vergleichbar)


e_q = embed(q_text)

e_R = embed(R_text)



⸻


DI.5.2 Richtungsimpuls J


J = 1 - cosine(e_q, e_R)


J = 1.0 - cosine_similarity(e_q, e_R)



⸻


DI.5.3 Informationsgehalt G (MVP-Proxy)


Für Standard-Eval wird kein Konzept-Mining vorausgesetzt.


G = 1 - max_d cosine(e_q, e_d)


G = 1.0 - max(

    cosine_similarity(e_q, embed(doc))

    for doc in retrieved_docs

)


Interpretation:

	•	Hohe Überlappung mit Retrieval → geringer Informationsimpuls

	•	Geringe Überlappung → hoher Neuheitsimpuls relativ zur Wissensbasis


⸻


DI.5.4 Gesamtwert I₀


I_0 = η · G + (1 - η) · J


I0 = eta * G + (1 - eta) * J


Empfohlene Startwerte:

	•	eta = 0.5 (neutral)

	•	eta = 0.6 (mehr Gewicht auf Neuheit)


⸻


DI.6 Output-Schema (Eval-Record)


{

  "session_id": "...",

  "turn_id": 7,

  "role": "assistant",

  "I0": 0.42,

  "G": 0.55,

  "J": 0.29,

  "system_prompt_id": "sp_v3",

  "tool_profile_id": "tools_basic",

  "retrieval_ids": ["doc12", "doc91", "doc07"],

  "embedding_model_id": "text-embedding-3-large"

}



⸻


DI.7 Vergleichbarkeit & Reproduzierbarkeit


Vergleichbar nur wenn identisch:

	•	Referenzraum-Definition

	•	Embedding-Modell

	•	Gewichtung \eta


Nicht vergleichbar:

	•	unterschiedliche Retrieval-Strategien

	•	implizite Historien

	•	personenbasierte Aggregation


⸻


DI.8 Explizite Nicht-Ziele (wichtig für Devs)


I₀ ist nicht:

	•	ein Quality-Score

	•	ein Reward-Signal

	•	ein Ranking-Kriterium für Nutzer

	•	ein Ersatz für Human Evaluation


I₀ ist:


ein erklärbarer Messwert für semantische Abweichung relativ zu sichtbarem Kontext


⸻


DI.9 Typische Einsatzpunkte

	•	Agenten-Monitoring

	•	Drift-Erkennung

	•	Vergleich von Modellantworten

	•	Analyse von Tool-Einfluss

	•	Forschung / Evaluation


⸻


Ergebnis (Dev-Annex)


Operator I₀ ist technisch leichtgewichtig,

auditierbar,

API-only implementierbar

und bewusst nicht steuernd.

