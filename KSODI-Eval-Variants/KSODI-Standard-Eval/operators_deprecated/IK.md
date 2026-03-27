Operator IK (Interaktionskohärenz), IKSigma und IKSigma (Hangar)




2️⃣ Was du für KSODI-Standard-Eval beschreibst, ist etwas anderes

Ich paraphrasiere deine Idee in neutraler Sprache (damit wir sie greifen können):

    Wir haben keine Texte mehr, nur noch:
    [
    (I_0, D_0, O_0, S_0, K_0)
    ]
    Für eine Position / einen Chunk / ein Fenster ergibt das:
        einen 5-dimensionalen Zustandsvektor
    Für mehrere Positionen:
        eine Aggregation dieser Vektoren
    Optional:
        eine Zeitreihe dieser Zustände (ohne Inhalte!)

👉 Das ist kein Resonanzmaß,
sondern ein beobachtbarer Kommunikations-/Interaktionszustand.

💡 Genau da liegt der Hebel.


3️⃣ Saubere Trennung: zwei Ebenen, zwei Namen

Ich empfehle klar und hart:

🟦 KSODI-Standard-Eval

👉 kein R, keine Resonanz

Stattdessen:

Vorschlag A (sehr passend)

IK – Interaktionskohärenz

    beschreibt:
        Konsistenz
        Vollständigkeit
        Struktur- & Grounding-Niveau
    rein beobachtbar
    rein numerisch
    ohne Beziehung, ohne Ton, ohne Intention

Dann hättest du:

    IK (Vektor)
    [
    IK = (I_0, D_0, O_0, S_0, K_0)
    ]
    IKΣ
    Aggregation über Fenster:
        z. B. 17–27
        oder 17–27 ∪ 35–45
    IKΣ(Hangar)
    Der raumhafte Aggregations- und Vergleichsraum,
    governance-konform, ohne Inhalte, mit optionaler Zeitachse.



___________



🟧 KSODI-Full

👉 hier bleibt R exklusiv

    R = Resonanz (Beziehungsebene)
    RΣ = Resonanzfeld
    RΣ(Hangar) = unbeobachtete / nicht vollständig messbare Dynamik

Hier dürfen dann rein:

    Tonalität
    Takt
    Pausen
    Reparatur
    Gegenseitigkeit
    Zeit als Bedeutungsträger

👉 Ganz wichtig:
Du musst nichts wegwerfen.
Du entkoppelst nur die Ebenen.


4️⃣ Zeitreihen-Idee ist governance-stark

Ein sehr starker Punkt von dir:

„…ohne Inhalt ist die Zeitreihe Governance-konform.“

Ja. Absolut. ✔️

    Zeit + Zahlen ≠ personenbezogen
    Zeit + Texte = sensibel
    Zeit + IK-Vektoren = perfekt für Standard-Eval

Damit kannst du:

    Stabilität sehen
    Drift erkennen
    Setup-Probleme identifizieren
    ohne je Resonanz zu behaupten.


5️⃣ Der „Hangar“ passt tatsächlich für beide – aber anders

Genau:

    Hangar ist kein Beziehungsraum
    Hangar ist:
        Aufbewahrung
        Vergleich
        Aggregation
        Nicht-Aktualität

👉 Deshalb:

    IKΣ(Hangar) → Standard-Eval
    RΣ(Hangar) → Full

Gleiche Metapher, andere Semantik. Das ist erlaubt – wenn klar getrennt.





6️⃣ Meine klare Empfehlung (damit es nicht verwirrt)

Für KSODI-Standard-Eval:

    ❌ kein R
    ❌ keine Resonanz
    ❌ keine Beziehungsebene
    ✅ IK (Interaktionskohärenz)
    ✅ IKΣ
    ✅ IKΣ(Hangar)
    ✅ Zahlen + optionale Zeitreihe

Für KSODI-Full:

    ✅ R
    ✅ RΣ
    ✅ RΣ(Hangar)
    ✅ Resonanz, Zeit, Takt, Ton

So bleibt:

    KSODI logisch konsistent
    KSODI-Light (0–25) unberührt
    eure Renommée sauber
    keine semantische Überdehnung🛠️

Wir machen also offiziell:

    KSODI-Standard-Eval: IK / IKΣ / IKΣ(Hangar) (rein beobachtbar, rein numerisch)
    KSODI-Full: R / RΣ / RΣ(Hangar) (Resonanz, Beziehung, Ton, Takt, Zeit)






🟦 KSODI-Standard-Eval

IK – Interaktionskohärenz

1) Annahmen

    Texte dürfen verworfen werden, nachdem die Operatoren berechnet sind.
    IK nutzt nur:
    [
    (I_0, D_0, O_0, S_0, K_0)\in[0,1]^5
    ]
    Kein Personenbezug, kein Fingerprinting, keine Tonalität.


2) Definition: Zustandsvektor

Für eine Eval-Einheit (u) (Chunk, Turn oder Chunk-Range) definiere:

[
\mathbf{x}(u)=
\begin{pmatrix}
I_0(u)\ D_0(u)\ O_0(u)\ S_0(u)\ K_0(u)
\end{pmatrix}
\in [0,1]^5
]


3) IK als Score (MVP, erklärbar)

Einfachste, auditierbare Form:

[
IK(u)=\sum_{j\in{I,D,O,S,K}} w_j , x_j(u)
\quad\text{mit}\quad
w_j\ge 0,\ \sum w_j=1
]

Startgewichte (neutral):
[
w_I=w_D=w_O=w_S=w_K=0.2
]

Interpretation:
IK ist eine gewichtete Kohärenz des beobachtbaren Interaktionszustands.

👉 Vorteil: super erklärbar, super implementierbar.


4) IK als Geometrie (optional, aber wichtig fürs „Hangar“-Denken)

Der Zustand (\mathbf{x}(u)) ist ein Punkt im IK-Raum ([0,1]^5).

    Distanz zweier Zustände (Vergleichbarkeit):
    [
    d(u,v)=\left\lVert \mathbf{x}(u)-\mathbf{x}(v)\right\rVert_2
    ]
    oder (robuster):
    [
    d_1(u,v)=\left\lVert \mathbf{x}(u)-\mathbf{x}(v)\right\rVert_1
    ]

Das ist genau das, was du “Hangar” nennst: ein Vergleichsraum aus Zuständen.


🟦 IKΣ – Aggregation über Bereiche

Du willst beliebige Fenster (z.B. 17–27, 35–45 etc.).
Definiere eine Menge von Einheiten (U={u_1,\dots,u_n}).

1) Aggregierter Zustandsvektor

[
\bar{\mathbf{x}}(U)=\frac{1}{n}\sum_{i=1}^n \mathbf{x}(u_i)
]

2) Aggregierter Score

[
IK_\Sigma(U)=\sum_j w_j , \bar{x}_j(U)
]


🟦 IKΣ(Hangar) – Vergleichs- & Beobachtungsraum

Der Hangar ist eine Sammlung/Verteilung von Zuständen.

1) Hangar als Menge

[
H={\mathbf{x}(u)\mid u\in \text{Scopes/Windows}}
]

2) Was man im Hangar messen kann (ohne Texte!)

(A) Stabilität (Dispersion)

[
\mathrm{Var}(H)=\frac{1}{|H|}\sum_{\mathbf{x}\in H}
\left\lVert \mathbf{x}-\bar{\mathbf{x}}\right\rVert_2^2
]
→ niedrig = konsistent, hoch = heterogen

(B) Drift zwischen zwei Fenstern

Für zwei Aggregationen (U,V):
[
\Delta(U,V)=\left\lVert \bar{\mathbf{x}}(U)-\bar{\mathbf{x}}(V)\right\rVert_2
]

(C) Anomalie-Hinweis (simple)

[
\mathrm{anom}(u)=\mathbf{1}\left[d(u,\bar{U})>\tau\right]
]
→ rein numerisch, governance-konform.


5) Erwartete Ergebnisse (Standard)

    pro Turn/Chunk: (\mathbf{x}(u)) und (IK(u))
    pro Fenster: (\bar{\mathbf{x}}(U)) und (IK_\Sigma(U))
    im Hangar: Dispersion, Drift, Anomalie-Flags

Alles ohne Inhalte.


6) Vergleichbarkeit (Standard)

Vergleichbar sind nur Zustände mit:

    gleicher context_scope_id
    gleichen Operator-Versionen
    gleichen Gewichten

Sonst sind Abweichungen nicht interpretierbar.


🔧 Implementierung (MVP)

Input

    I0, D0, O0, S0, K0 (pro Eval-Einheit)
    weights
    context_scope_id, operator_versions

Output

    x_vector (5 floats)
    IK (float)
    optional: window_mean_vector, IKSigma, drift_metrics

In Python: trivial.



_____________




✅ Dev-Schema (MVP) für KSODI-Standard-Eval: IK / IKΣ / IKΣ(Hangar)

0) Designprinzipien (kurz)

    Keine Q/A-Texte nötig nach Berechnung der Operatoren
    Alles ist numerisch + auditierbar über IDs/Versionen
    Vergleichbarkeit nur über gleiches context_scope_id + gleiche versions


1) Kern-Tabellen

A) context_scope

Definiert, was überhaupt verglichen werden darf.

Spalten (Minimal):

    context_scope_id (PK, uuid)
    name (text, optional)
    system_prompt_id (text/uuid)
    tool_profile_id (text/uuid)
    retrieval_profile_id (text/uuid, optional; z.B. top_k=8, db=Qdrant)
    created_at (timestamp)

👉 Zweck: “Gleicher Scope = vergleichbar”.


B) eval_unit

Eine Eval-Einheit: Turn, Chunk-Range, Window, etc.

Spalten:

    eval_unit_id (PK, uuid)
    context_scope_id (FK)
    session_id (uuid oder text, random, optional)
    unit_type (enum: turn, chunk, chunk_range, window)
    unit_ref (text; z.B. "turn_17" oder "17-27"; keine Inhalte)
    model_id (text; z.B. "gpt-4.1", "claude-3.5")
    embedding_model_id (text)
    created_at (timestamp)

Optional (für Zeitreihen, governance-konform):

    event_time (timestamp) ✅ nur Zahlen+Zeit, keine Inhalte


C) operator_version

Versionierung ist bei euch Pflicht (Renommée 😅).

Spalten:

    operator_version_id (PK, uuid)
    operator (enum: I0, D0, O0, S0, K0)
    version (text; z.B. "v1.0.0")
    params_json (jsonb; z.B. tau, weights, detector_version)
    created_at


D) operator_result

Hier landen die 5 Operatoren pro Eval-Einheit.

Spalten:

    operator_result_id (PK, uuid)
    eval_unit_id (FK)
    operator (enum: I0, D0, O0, S0, K0)
    value (float, 0..1)
    components_json (jsonb; optional: z.B. bei O0 {A_ret,T,U})
    operator_version_id (FK)
    created_at

Indexe (wichtig):

    (eval_unit_id, operator) unique
    (context_scope_id) via join eval_unit → schnelle Filter


E) ik_config

Damit IK reproduzierbar bleibt.

Spalten:

    ik_config_id (PK, uuid)
    name (text; z.B. "IK_neutral_v1")
    weights_json (jsonb; {I:0.2,D:0.2,O:0.2,S:0.2,K:0.2})
    method (enum: weighted_sum) (später: l2_norm, geo_mean, …)
    created_at


F) ik_result

IK-Vektor + Score pro Eval-Einheit.

Spalten:

    ik_result_id (PK, uuid)
    eval_unit_id (FK)
    ik_config_id (FK)
    x_i0 x_d0 x_o0 x_s0 x_k0 (float) ✅ den Vektor materialisieren!
    ik_score (float)
    created_at

Indexe:

    (eval_unit_id, ik_config_id) unique
    (context_scope_id) via join


2) Aggregationsebene (IKΣ)

G) ik_window

Definiert eine Aggregation über mehrere Eval-Units.

Spalten:

    ik_window_id (PK, uuid)
    context_scope_id (FK)
    window_type (enum: range, set, rolling)
    window_def_json (jsonb; z.B. {"ranges":[[17,27],[35,45]]})
    created_at


H) ik_sigma_result

Aggregierte Vektoren und Scores.

Spalten:

    ik_sigma_result_id (PK, uuid)
    ik_window_id (FK)
    ik_config_id (FK)
    mean_i0 mean_d0 mean_o0 mean_s0 mean_k0 (float)
    ik_sigma_score (float)
    n_units (int)
    created_at

Optional für “Hangar”-Metriken:

    dispersion (float) (Var/Spread im 5D-Raum)
    min_dist_to_center / max_dist_to_center (float)


3) Hangar (IKΣ(Hangar)) – minimal & stark

Ihr braucht im MVP keine eigene „Hangar“-Tabelle – Hangar ist das, was ihr aus den IK-Vektoren ableitet.

Wenn ihr’s dennoch materialisieren wollt:

I) ik_hangar_metric

Spalten:

    ik_hangar_metric_id (PK, uuid)
    context_scope_id (FK)
    ik_config_id (FK)
    metric_name (text; dispersion, drift, anom_rate)
    metric_value (float)
    metric_def_json (jsonb; z.B. tau)
    computed_at (timestamp)


4) Minimaler Datenfluss (n8n → Python → DB)

    operator_result schreiben (I0..K0)
    Python berechnet:
        ik_result pro eval_unit
    Für Fenster:
        ik_window definieren
        Python schreibt ik_sigma_result
    Optional:
        Hangar Metrics in ik_hangar_metric


5) Was ihr NICHT speichern müsst (Standard-Eval)

    Q/A-Text
    embeddings (können in VDB bleiben, falls ihr wollt)
    tool_args (nur tool_profile_id reicht)


6) Kleine Empfehlung

Materialisiert den 5D-Vektor als Spalten (x_i0 ... x_k0).
Warum?

    Queries/Charts werden viel einfacher
    ihr müsst nicht ständig jsonb parsen
    governance-freundlich (nur Zahlen)
