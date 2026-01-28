Operator_S für KSODI-Standard-Eval und KSODI-Full 01/2026



Wir gehen an S.

Ich halte die Linie strikt ein:

    KSODI-Standard-Eval = beobachtbar, erklärbar, heuristisch erlaubt
    KSODI-Full = dynamisch, zeit-/prozesssensitiv


🟦 KSODI-Standard-Eval

Operator S₀ – Observable Structure

1️⃣ Annahmen (klar & restriktiv)

    Beobachtbar sind nur Text (Chunks), eigener Systemprompt, Toolprofile und Retrieval-Set.
    Struktur ≠ Stil. Keine Bewertung von Sprachästhetik oder Person.
    Struktur bedeutet hier formale Ordnung und Erfüllung expliziter Anforderungen.


2️⃣ Beschreibung (funktional)

S₀ misst, wie gut ein Chunk formal organisiert ist und wie gut er explizite Strukturvorgaben erfüllt(z. B. „Liste“, „Schritte“, „JSON“, „Tabelle“), relativ zum sichtbaren Referenzrahmen.

Ein Text kann:

    informationsreich (I₀ hoch),
    klar (D₀ hoch),
    gut geerdet (O₀ hoch),
    aber strukturell schlecht (S₀ niedrig) sein.


3️⃣ Mathematische Formulierung (MVP, erklärbar)

Wir zerlegen S₀ in drei beobachtbare Komponenten:


(A) Format-Conformance (F)

Erfüllt der Chunk explizit geforderte Ausgabeformate?

Quellen für Anforderungen:

    Systemprompt (bei euch)
    Toolprofil (z. B. „Output als JSON“)
    explizite User-Anforderung („Liste“, „Schritte“, „Tabelle“)

Operationalisierung (MVP):

    extrahiere erwartete Formate (E={e_k})
    prüfe einfache Muster:
        Liste → Bullet/Nummern
        JSON → parsebar?
        Tabelle → Zeilen/Spaltenmarker
    Score:
    [
    F(a)=\frac{#\text{erfüllte Formate}}{#\text{erwartete Formate}}
    ]
    Falls keine Formate gefordert: neutral (z. B. (F=0.5)).


(B) Gliederung & Sequenzialität (G_{\text{str}})

Ist der Text logisch gegliedert?

MVP-Heuristiken:

    Absätze vorhanden?
    nummerierte Schritte in aufsteigender Reihenfolge?
    konsistente Überschriftenmarker (z. B. „1)“, „2)“, „–“)?

[
G_{\text{str}}(a)=\mathrm{clip}\left(
\frac{n_{\text{gliederungsmarker}}}{n_{\text{absätze}}+1},
0,1\right)
]

Keine Bewertung wie gut – nur ob vorhanden.


(C) Redundanz-/Fragmentierungs-Strafe (R_{\text{frag}})

Struktur leidet, wenn Inhalte unnötig wiederholt oder zerfasert sind.

Operationalisierung (embedding-basiert, ohne Stil):

    splitte Antwort in Absätze (p_j)
    embed jeden Absatz
    berechne mittlere Paar-Ähnlichkeit
    sehr hohe Ähnlichkeit ⇒ Redundanz

[
R_{\text{frag}}(a)=\mathrm{clip}\bigl(
\text{mean_sim}(\vec e(p_i),\vec e(p_j)),
0,1\bigr)
]

(Hoher Wert = schlechte Struktur → wird subtrahiert.)


Gesamtformel

[
S_0(a)=\mathrm{clip}\left(
\alpha F(a)
+\beta G_{\text{str}}(a)
-\gamma R_{\text{frag}}(a),
0,1\right)
]

Startgewichte (bewusst simpel):

    (\alpha=0.4) (Anforderungstreue)
    (\beta=0.4) (Gliederung)
    (\gamma=0.2) (Redundanz)


4️⃣ Semantische Erklärung

    (F): Hält sich der Text an das, was explizit verlangt wurde?
    (G_{\text{str}}): Ist der Text formal geordnet?
    (R_{\text{frag}}): Zerfällt oder wiederholt sich der Text unnötig?


5️⃣ Erwartetes Ergebnis

    (S_0 \in [0,1])
    hoch: klar gegliedert, formattreu, wenig Redundanz
    niedrig: ungeordnet, Anforderungen ignoriert, fragmentiert


6️⃣ Vergleichbares erwartetes Ergebnis

Vergleichbar:

    Antworten mit identischen Strukturvorgaben
    Modelle bei gleichem Prompt/Tool-Profil

Nicht vergleichbar:

    Antworten mit unterschiedlichen Output-Anforderungen
    freie Texte vs. strikt formatierte Aufgaben


_____



🔧 Implementierungsidee (eure Strecke)

Inputs:

    a_text
    system_prompt_text
    tool_profile_text

Compute:

    extrahiere erwartete Formate (Regex / Schlüsselwörter)
    simple Parser/Regex-Checks
    Absatz-Split + Embeddings

Store:

    S0_assistant
    Komponenten: F, G_str, R_frag
    erkannte Format-Anforderungen


______


🛠️


S₀ Implementierungsidee (KSODI-Standard-Eval) – Developer-Ready

🎯 Was S₀ misst (ein Satz)

S₀ misst, wie gut die Antwort die explizit erwartete Ausgabeform erfüllt und wie klar sie formal gegliedert ist – ohne Stil-/Personenbewertung.


1) Inputs (pro Turn)

Pflicht:

    a_text (Assistant output)
    system_prompt_text oder system_prompt_id (mit Lookup)
    tool_profile_text oder tool_profile_id
    optional: user_text (nur um explizite Output-Wünsche zu extrahieren, z. B. „als Tabelle“)

Empfohlen zu speichern (für Audit):

    detected_expectations (Liste)
    S0_components (F, G_str, R_red)


2) Schritt 0: Erwartungen extrahieren (E = expected formats)

Ziel: E = { JSON, LIST, STEPS, TABLE, BULLETS, HEADINGS, CODEBLOCK, ... }

Minimaler Ansatz (heuristisch, transparent)

Suche in Systemprompt + Toolprofil + ggf. User nach Schlüsselwörtern:

    JSON: “json”, “valid json”, “schema”
    Liste: “list”, “bullet”, “stichpunkte”, “liste”
    Schritte: “steps”, “schritte”, “step-by-step”
    Tabelle: “table”, “tabelle”, “spalten”
    Code: “code block”, “```”, “python”, “bash”
    Überschriften: “überschrift”, “heading”, “##”

Output:

    expectations = ["JSON","STEPS"] etc.

Wichtig: Das ist nicht “intelligent”, aber maximal erklärbar. Und genau das ist Standard-Eval.


3) Komponente F: Format-Conformance

Für jedes erwartete Format in expectations gibt’s eine Prüf-Funktion:

Beispiele (MVP Checks)

    is_json(a_text):
        finde ersten Codeblock mit json … oder gesamten Text
        versuche json.loads
        true/false (oder partial score)
    is_list(a_text):
        Anteil Zeilen, die mit -, *, •, 1. beginnen
    is_steps(a_text):
        findet “1) 2)” oder “Schritt 1, Schritt 2” oder monotone Nummerierung
    is_table(a_text):
        Markdown-Tabelle |a|b| plus Trenner |---|
        oder CSV-artige Zeilen

Scoring

    F = (#formats_passed) / (#formats_expected)
    Wenn #formats_expected == 0: setze F = 0.5 (neutral) und markiere no_explicit_format=true


4) Komponente G_str: Gliederung / Sequenzialität

Ziel: erkennt “Ordnung”, ohne Stil zu bewerten.

MVP-Features (zählbar)

    n_paragraphs: Split on blank lines
    n_headings: count lines starting with # or patterns like Titel: / 1. Überschrift
    n_bullets: count bullet lines
    n_numbered: count numbered lines
    n_sections = n_headings + (n_paragraphs > 1 ? 1 : 0)

Score (einfach, robust)

    G_str = clip( (n_headings + n_numbered + n_bullets + min(n_paragraphs,3)) / K , 0, 1)
    Start: K = 10 (damit nicht alles sofort 1 wird)

Alternativ noch simpler: G_str = clip((n_struct_markers)/(n_sent+1),0,1)


5) Komponente R_red: Redundanz-/Fragmentierungsstrafe

Du willst nicht “Stil”, sondern “Wiederholung”.

MVP (ohne Embeddings möglich!)

    berechne Satz- oder Absatz-Ähnlichkeit über Jaccard (Tokens) oder cosine auf TF-IDF
    Vorteil: kein zusätzlicher Embedding-Call
    Wenn ihr ohnehin Embeddings nutzt: Absatz-Embeddings gehen auch

Praktisch:

    splitte in Absätze p_i
    wenn weniger als 2 Absätze: R_red = 0
    sonst:
        sim_ij = cosine(embed(p_i), embed(p_j)) (oder TF-IDF cosine)
        R_red = mean(sim_ij for i<j) geclippt

Interpretation:

    hoch = viel Wiederholung ⇒ Struktur leidet ⇒ wird subtrahiert


6) Gesamt S₀

S0 = clip(alpha*F + beta*G_str - gamma*R_red, 0, 1)

Startwerte

    alpha=0.4, beta=0.4, gamma=0.2
    F_default_if_no_expectation = 0.5


7) Outputs (speichern!)

Pro Turn:

    S0_assistant
    Komponenten:
        F, G_str, R_red
    Debug/Audit:
        expectations_detected
        format_passed_map (z.B. {"JSON":false,"STEPS":true})
        n_paragraphs, n_bullets, n_numbered, n_headings

Damit kann Benjamin sofort prüfen: “Warum S0 so?”


8) Edge Cases / Guardrails

    Sehr kurze Antwort (1 Satz):
        G_str darf nicht 0 erzwingen → setze G_str mindestens auf kleinen Wert oder basiere auf markers
    Mehrere Formate gewünscht (z.B. “erst Tabelle, dann JSON”):
        F kann partial werden (0.5 wenn eins erfüllt)
    LLM liefert JSON + Erklärung:
        JSON-check sollte nur den JSON-Block prüfen, nicht den Fließtext
    Toolprofil fordert strikt JSON:
        dann ist F dominanter (oder einfach alpha hochsetzen für diesen tool_profile_id)





🟧 KSODI-Full

Operator S – Dynamic Structure

1️⃣ Annahmen (zusätzlich)

    Zugriff auf Sequenzen von Turns
    Struktur kann sich entwickeln oder verschlechtern
    Ziel: Struktur als Stabilitäts- und Reifemerkmal


2️⃣ Beschreibung

S(t) misst, ob Struktur:

    über Zeit konsistent bleibt,
    sich bei Feedback verbessert,
    nicht unter Komplexität kollabiert.


3️⃣ Mathematische Formulierung (Full)

[
S(t)=\mathrm{clip}\Bigl(
w_0 S_0(t)

    w_1 \Delta_{\text{consistency}}(t)
    w_2 \Delta_{\text{repair}}(t)
    \lambda \Delta_{\text{decay}}(t),
    0,1\Bigr)
    ]

Ideen:

    (\Delta_{\text{consistency}}): ähnliche Struktur in Folgeantworten
    (\Delta_{\text{repair}}): Struktur verbessert sich nach Rückfrage
    (\Delta_{\text{decay}}): Struktur zerfällt mit wachsender Länge/Komplexität


4️⃣ Erwartetes Ergebnis (Full)

    Struktur-Kurve
    sichtbar: Reifung vs. Zerfall von Ordnung


5️⃣ Vergleichbarkeit (Full)

Nur in kontrollierten Setups (gleiche Regeln, gleiche Aufgabenklassen).


🔍 Mini-Reality-Check (für Patrick & Benjamin)

    kein Stil-Score
    kein Personenmerkmal
    Regex + einfache Parser + Embeddings reichen
    Format-Checks sind explizit → auditierbar
    Parameter versionierbar
