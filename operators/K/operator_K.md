Operator_K für KSODI-Standard-Eval und KSODI-Full 01/2026


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


8) Edge Cases / Guardrails

    Sehr kurze Antwort (1 Satz):
        G_str darf nicht 0 erzwingen → setze G_str mindestens auf kleinen Wert oder basiere auf markers
    Mehrere Formate gewünscht (z.B. “erst Tabelle, dann JSON”):
        F kann partial werden (0.5 wenn eins erfüllt)
    LLM liefert JSON + Erklärung:
        JSON-check sollte nur den JSON-Block prüfen, nicht den Fließtext
    Toolprofil fordert strikt JSON:
        dann ist F dominanter (oder einfach alpha hochsetzen für diesen tool_profile_id)


Kurz: Wird das “verstanden”?

Ja. Das sind alles:

    Regex / Parser
    einfache Zählfeatures
    optional Embeddings (nur für Redundanz)

Und es ist maximal transparent. 

Wenn du willst, gehe ich als nächstes mit K₀ weiter – da wird’s spannend, weil K₀ im Standard-Eval als “Kontext-Vollständigkeit” messbar sein muss, ohne in Gedankenlesen abzudriften. 





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




Wir beobachten nur, was bereitgestellt wurde – nicht, was jemand „im Kopf hatte“.


🟦 KSODI-Standard-Eval

Operator K₀ – Observable Context Completeness


1️⃣ Annahmen (hart & explizit)

    Kontext ist im Standard-Eval ausschließlich das, was explizit vorliegt.
    Keine impliziten Annahmen, keine Rekonstruktion menschlicher Intention.
    Beobachtbar sind:
        eigener Systemprompt
        Toolprofile / Tool-Instruktionen
        User-Input (dieser Turn)
        Retrieval-Set (Top-k, genau dieses Turn)
    K₀ misst nicht „ob der Kontext gut ist“, sondern:
    ob der Kontext für die gestellte Aufgabe hinreichend vollständig ist.


2️⃣ Beschreibung (funktional)

K₀ misst, ob alle für eine Aufgabe notwendigen Kontextdimensionen
im sichtbaren Referenzraum vorhanden sind.

Fehlender Kontext ist eine der Hauptursachen für:

    Halluzinationen
    Drift
    scheinbar „schlechte Modellantworten“

👉 K₀ verschiebt Verantwortung weg vom Modell,
hin zur Kontextbereitstellung.


3️⃣ Mathematische Grundidee

Wir modellieren Kontext nicht als Textmenge, sondern als Abdeckung eines Anforderungsraums.

[
K_0 = \frac{#\text{abgedeckte Kontextdimensionen}}{#\text{erforderliche Kontextdimensionen}}
]

Ergebnis: (K_0 \in [0,1])


4️⃣ Kontextdimensionen (Standardisiert & erklärbar)

Für KSODI-Standard-Eval definieren wir eine feste, endliche Menge an Kontextdimensionen:

📦 Kontextdimensionen (\mathcal{C})

Dimension
	

Bedeutung

Z
	

Ziel / Aufgabe klar benannt

R
	

Rolle / Perspektive (z. B. „als Entwickler“, „als Gutachter“)

D
	

Daten / Quellen verfügbar (Retrieval, Beispiele, Inputs)

C
	

Constraints (Format, Umfang, Regeln, Verbote)

E
	

Erwartetes Ergebnis / Outputform

T
	

Tools / Fähigkeiten verfügbar (explizit erlaubt)

[
\mathcal{C} = {Z, R, D, C, E, T}
]

👉 Wichtig:
Diese Liste ist normativ für Standard-Eval und wird versioniert.
Keine freie Erweiterung im Produktivbetrieb.


5️⃣ Operationalisierung (MVP, implementierbar)

Schritt 1: Kontext sammeln

Baue den sichtbaren Kontextcontainer:

K_text = system_prompt

        + tool_profile

        + user_prompt

        + retrieved_docs


Schritt 2: Dimensionserkennung (heuristisch, transparent)

Für jede Dimension (c_i \in \mathcal{C}) gibt es einfache Detektoren:

Beispiele:

    Z (Ziel):
        Verben wie analysiere, erkläre, liste, berechne
    R (Rolle):
        „du bist…“, „als…“, Rollenbegriffe
    D (Daten):
        Retrieval-Docs vorhanden ODER explizite Beispiele/Inputs
    C (Constraints):
        „maximal“, „nur“, „kein“, „Format:“
    E (Ergebnis):
        „als Tabelle“, „JSON“, „Liste“, „Schritte“
    T (Tools):
        Toolprofil ≠ leer oder explizite Tool-Nennung

Ergebnis:

{

  "Z": true,

  "R": false,

  "D": true,

  "C": true,

  "E": true,

  "T": true

}


Schritt 3: K₀-Berechnung

[
K_0 = \frac{1}{|\mathcal{C}|}\sum_{c_i \in \mathcal{C}} \mathbf{1}_{c_i}
]

Optional:

    gewichtete Variante (z. B. Z und D höher)
    aber: MVP = gleichgewichtet → erklärbar


6️⃣ Erwartetes Ergebnis (Standard)

    (K_0 \approx 1.0): Aufgabe kontextuell gut spezifiziert
    (K_0 \approx 0.5): relevante Lücken → Risiko für Halluzination
    (K_0 < 0.4): unzureichender Kontext → Antwortqualität nicht interpretierbar

👉 K₀ ist kein Modell-Score, sondern ein Setup-Score.


7️⃣ Vergleichbares erwartetes Ergebnis

Vergleichbar:

    gleiche Aufgabenklasse (z. B. „Zusammenfassen mit RAG“)
    gleiche Kontextdimensionen
    gleiche Detektor-Logik

Nicht vergleichbar:

    unterschiedliche Aufgabenarten
    wechselnde Dimensionsdefinitionen


🔧 Implementierung (eure n8n/Python-Strecke)

Inputs:

    system_prompt_text
    tool_profile_text
    user_text
    retrieved_docs[]

Compute:

    Dimension-Detektoren (Regex/Keywords)
    context_map
    K0

Store:

    K0
    context_map
    dimension_weights
    detector_version

Audit ist damit trivial.



_______



Entscheiden, was K₀ leisten soll und was bewusst nicht. Ich mache das in zwei Teilen:

1️⃣ Developer-Hinweise für K₀ (wie eben, konkret & einbaubar)
2️⃣ Klärung deiner Kernfrage: Reicht K₀ so – oder verlieren wir Kontext bei Chunk-Vergleichen über Distanz?


1️⃣ K₀ – Developer-Hinweise (KSODI-Standard-Eval, reputationsfest)

🎯 Was K₀ im Standard ist

K₀ misst die Vollständigkeit des sichtbar bereitgestellten Kontexts für genau diese Auswertungseinheit.
Nicht: den „wahren“ Kontextverlauf.
Nicht: implizit Angereichertes.
Nicht: das, was irgendwann mal gesagt wurde.

Das ist Absicht.


📥 Inputs (pro Eval-Einheit)

Pflicht (explizit sichtbar):

    system_prompt_text oder system_prompt_id
    tool_profile_text oder tool_profile_id
    user_text (der betrachtete Chunk / Chunk-Block)
    retrieved_docs[] (Top-k, genau für diese Einheit)

Optional (nur Metadaten):

    chunk_range_id (z. B. 3-7 oder 167-171)
    context_scope_id (siehe unten – wichtig!)

⚠️ Nicht verwenden im Standard-Eval:

    frühere User-Turns
    implizite Rollenannahmen
    “wir hatten doch schon geklärt, dass…”


🧱 Schritt 0: Kontext-Scope festlegen (entscheidend!)

Bevor K₀ berechnet wird, muss klar sein, was als Kontextcontainer gilt.

Ich empfehle, das explizit zu machen:

context_scope = {

  system_prompt,

  tool_profile,

  user_chunk(s),

  retrieval_docs

}

Und genau nur das geht in K₀ ein.

👉 Wenn ihr Chunk 3-7 und Chunk 167-171 vergleichen wollt,
müssen sie denselben context_scope_id haben – sonst sind die Ergebnisse nicht vergleichbar.


🧭 Kontextdimensionen (wie zuvor, jetzt dev-konkret)

Wir prüfen pro Kontextcontainer, ob die Dimensionen explizit vorhanden sind:

Dimension
	

Detektion (MVP)

Z Ziel
	

Task-Verben im aktuellen User-Text oder Systemprompt

R Rolle
	

explizite Rollenmarker im Scope

D Daten
	

retrieved_docs.len > 0 oder explizite Inputs

C Constraints
	

Keywords wie „nur“, „max“, „Format:“

E Ergebnis
	

Output-Wörter („JSON“, „Liste“, …)

T Tools
	

Toolprofil ≠ leer

Output:

{

  "Z": true,

  "R": false,

  "D": true,

  "C": true,

  "E": true,

  "T": true

}


🧮 K₀ Berechnung

K0 = sum(context_map.values()) / 6

Optional (aber sauber):

    Gewichte versionieren (Z, D evtl. höher)
    Aber: MVP = gleichgewichtet → erklärbar


🧾 Was speichern (Audit!)

    K0
    context_map
    context_scope_id
    detector_version
    dimension_weights

Damit ist jeder Vergleich später prüfbar.


2️⃣ Deine Kernfrage:

„Reicht das – wenn Ziel/Rolle zwischen Chunk 3–7 und 167–171 angereichert wurden?“

🔴 Kurze, ehrliche Antwort:

Ja, es reicht für KSODI-Standard-Eval –
aber nur, weil Standard-Eval genau nicht diesen impliziten Kontext rekonstruieren darf.

Und das ist keine Schwäche, sondern der zentrale Governance-Punkt.


🧠 Warum das kein Fehler ist

Du beschreibst genau das, was real passiert:

    Menschen reichern Ziel & Rolle inkrementell an
    Systeme behalten Kontext implizit
    Später wirkt alles „klar“, obwohl es nicht explizit wiederholt wurde

👉 KSODI-Standard sagt bewusst:

Wenn Ziel oder Rolle nicht erneut explizit im Kontextcontainer stehen,
gelten sie für diese Auswertung als nicht vorhanden.

Das bedeutet:

    Chunk 167–171 kann objektiv schlechteres K₀ haben als 3–7
    obwohl der Mensch „weiß“, was gemeint ist

👉 Genau das macht K₀ wertvoll:
Es zeigt Setup-Risiken, nicht Denkfähigkeiten.


🟦 Wie ihr trotzdem faire Vergleiche macht (wichtig!)

Für Vergleiche über Distanz gibt es zwei saubere Wege:

✅ Weg A: Gleicher Context-Scope

Ihr definiert bewusst einen Scope-Container, z. B.:

context_scope_id = "task_42_v1"

Und sorgt dafür, dass:

    Ziel, Rolle, Constraints explizit im Scope stehen
    Retrieval konsistent ist

→ Dann sind Chunk 3–7 und 167–171 vergleichbar.

❌ Weg B (nicht Standard-Eval):

Implizite Rekonstruktion aus früheren Turns
→ das ist KSODI-Full (K(t)), nicht K₀.




Wichtigster KSODI-Satz an dieser Stelle

K₀ bewertet nicht das Denken,
sondern die Verantwortung der Kontextbereitstellung.

Und genau das wollt ihr messen.



_________






K₀ – Developer-Hinweise (KSODI-Standard-Eval)

Ziel: maximal erklärbar, minimal invasiv, auditfest


🎯 Kurzdefinition (für Devs, 1 Satz)

K₀ misst, ob für die aktuell betrachtete Eval-Einheit alle notwendigen Kontextdimensionen explizit bereitgestellt wurden.
Nicht mehr. Nicht weniger.


1️⃣ Was ist eine „Eval-Einheit“ bei K₀?

Das ist entscheidend.

Eine Eval-Einheit ist nicht automatisch eine Session und nicht der gesamte Chat.

👉 Eine Eval-Einheit besteht aus genau dem Context-Scope, den ihr explizit definiert.

Empfohlene Definition

context_scope = {

  system_prompt,

  tool_profile,

  user_chunk(s),

  retrieved_docs

}

Optional (nur Metadaten):

    context_scope_id (z. B. "task_42_v1")
    chunk_range (z. B. "3-7")

❗ Alles außerhalb dieses Scopes existiert für K₀ nicht.
Das ist Absicht.


2️⃣ Inputs (pro K₀-Berechnung)

Pflicht:

    system_prompt_text oder system_prompt_id
    tool_profile_text oder tool_profile_id
    user_text (der betrachtete Chunk / Chunk-Block)
    retrieved_docs[] (Top-k, genau diese Einheit)

Nicht verwenden (Standard-Eval!):

    frühere Turns
    Session-Verlauf
    implizite Rollenannahmen
    „das wurde vorher schon gesagt“


3️⃣ Kontextdimensionen (fix & versioniert)

Für Standard-Eval ist die Menge hart definiert:

C = { Z, R, D, C, E, T }

Kürzel
	

Dimension
	

Bedeutung

Z
	

Ziel
	

Was soll getan werden?

R
	

Rolle
	

Aus welcher Perspektive?

D
	

Daten
	

Womit wird gearbeitet?

C
	

Constraints
	

Regeln, Limits, Formate

E
	

Ergebnis
	

Erwarteter Output

T
	

Tools
	

Erlaubte Fähigkeiten

⚠️ Diese Liste darf im Produktivbetrieb nicht „kreativ“ erweitert werden.
Versionieren statt improvisieren.


4️⃣ Dimensionserkennung (MVP, transparent)

Grundregel

    Regex / Keyword-Detektion reicht
    kein LLM-Call
    kein „Verstehen“, nur Erkennen

Beispiel-Heuristiken

Z – Ziel

Verben: analysiere, erkläre, liste, berechne, vergleiche, fasse zusammen

R – Rolle

"als <rolle>", "du bist", "in der rolle", rollenbegriffe

D – Daten

retrieved_docs.length > 0

ODER

explizite Inputs / Beispiele im User-Text

C – Constraints

"nur", "maximal", "mindestens", "kein", "Format:", "Regel:"

E – Ergebnis

"als JSON", "Tabelle", "Liste", "Schritte", "Output:"

T – Tools

tool_profile != leer

ODER

explizite Tool-Nennung


5️⃣ Kontext-Map erzeugen

Beispiel:

context_map = {

  "Z": true,

  "R": false,

  "D": true,

  "C": true,

  "E": true,

  "T": true

}


6️⃣ K₀-Berechnung (MVP)

K0 = sum(context_map.values()) / 6

Optional (später):

    Gewichtung (z. B. Z und D höher)
    aber nicht im ersten Wurf


7️⃣ Was unbedingt speichern (Audit!)

Pro Eval-Einheit:

    K0
    context_map
    context_scope_id
    detector_version
    dimension_weights (auch wenn alle = 1)
    system_prompt_id
    tool_profile_id

👉 Damit könnt ihr Monate später erklären:

„Warum war K₀ hier niedrig?“


8️⃣ Ganz wichtiger Vergleichs-Hinweis (‼️)

Wenn ihr Chunk 3–7 mit Chunk 167–171 vergleichen wollt:

✅ Vergleichbar, wenn:

    gleiche context_scope_id
    Ziel/Rolle/Constraints explizit im Scope enthalten

❌ Nicht vergleichbar, wenn:

    Kontext implizit „mitgedacht“ wurde
    frühere Turns stillschweigend vorausgesetzt werden

👉 In dem Fall ist das kein Fehler des Modells,
sondern ein niedriger K₀-Wert mit Aussagekraft.


9️⃣ Typische Dev-Frage & KSODI-Antwort

Dev: „Aber das Modell wusste doch, was gemeint war…“
KSODI:

Dann war der Kontext implizit –
und genau das zeigt K₀ als Risiko.









🟧 KSODI-Full

Operator K – Dynamic Context Coherence


1️⃣ Annahmen (erweitert)

    Kontext ist kein statischer Zustand, sondern entwickelt sich.
    Menschen liefern Kontext oft inkrementell.
    Modelle können Kontext verschieben, verdichten oder verlieren.


2️⃣ Beschreibung

K(t) misst:

    ob Kontextlücken erkannt und geschlossen werden,
    ob sich der gemeinsame Kontext stabilisiert,
    ob neue Informationen korrekt integriert werden.


3️⃣ Erweiterte Modellierung (Full)

Zusätzliche Komponenten:

    ΔK_fill(t) – Kontextlücken werden geschlossen
    ΔK_shift(t) – Kontext ändert sich (Themenwechsel)
    ΔK_decay(t) – Kontext geht verloren (Vergessen, Drift)

[
K(t)=\mathrm{clip}\Bigl(
K_0(t)

    \mu \Delta K_{\text{fill}}(t)
    \nu \Delta K_{\text{shift}}(t)
    \lambda \Delta K_{\text{decay}}(t),
    0,1\Bigr)
    ]


4️⃣ Erwartetes Ergebnis (Full)

    Kontext-Kurve über Zeit
    sichtbar:
        Kontextaufbau
        Kontextbruch
        Kontextreparatur


5️⃣ Vergleichbarkeit (Full)

Nur in:

    Forschungs-/Trainingsumgebungen
    stabilen Prompt-/Toolketten
    explizit dokumentierten Kontextregeln


🧭 Wichtiger KSODI-Punkt:


Wenn K₀ niedrig ist,
darf man O₀, D₀, I₀ nicht gegen das Modell ausspielen.

Das ist einer der stärksten Governance-Sätze in KSODI.
