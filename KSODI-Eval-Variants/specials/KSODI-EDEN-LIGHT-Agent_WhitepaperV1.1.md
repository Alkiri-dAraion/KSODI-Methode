# KSODI & EDEN  
**Ein Reifegradansatz zur Prompt-Optimierung in Unternehmen**

---

## Geplantes Tool  
**KSODI-Light Agent mit EDEN-Mapping (PoC)**

---

## Zielsetzung

Dieses Whitepaper skizziert eine minimalistische Agentenstruktur zur Beobachtung und Bewertung von KI-Prompting in Unternehmen. Die Grundlage bildet die Open-Source-Methode **KSODI** ([CC BY 4.0 Lizenz](https://creativecommons.org/licenses/by/4.0/)) zur Optimierung der Mensch-Maschine-Interaktion.  

Erweitert wird diese Methodik durch das etablierte **EDEN-Reifegradmodell**, das eine anschlussfähige Systematik für Unternehmensentwicklung und Prozessreife liefert.

Ziel ist ein leichtgewichtiges **Proof-of-Concept (PoC)**, das ohne aufwendige Infrastruktur realisiert werden kann – mit Perspektive auf spätere Skalierung entlang der gesamten Wertschöpfungskette (z. B. Schulung, Auditing, Governance, Automatisierung).

---

## 1. Was ist das „Reifegradmodell EDEN“ – und wo wird es eingesetzt?

Das **EDEN-Reifegradmodell** ist ein etabliertes Framework zur strukturierten Bewertung von Prozessorientierung und Organisationskompetenz in Unternehmen.  

Ursprünglich von **BPM&O** entwickelt, analysiert EDEN Prozesse, Strukturen und Fähigkeiten entlang definierter Entwicklungsstufen und ermöglicht gezielte Verbesserungen.

Ein zentrales Merkmal von EDEN ist die **bildhafte Stufenlogik**, die über fünf Metaphern die Reife von Bereichen oder Organisationen einordnet:

- **Sumpf**: impulsive, unstrukturierte Arbeitsweise  
- **Wiese**: erste Strukturansätze  
- **Hain**: zielorientierte, systematische Entwicklung  
- **Garten**: reflektiertes, komplexes Zusammenspiel  
- **Garten mit System**: kreative Integration in die tägliche Arbeit

**Typische Anwendungsfelder von EDEN:**

- Prozessmanagement & Organisationsentwicklung  
- Digitalisierung und Automatisierung  
- Einführung neuer Technologien (z. B. KI, RPA, ERP)  
- ISO-Zertifizierung & Auditierung  
- Change Management & Kulturentwicklung  
- Benchmarking & kontinuierliche Verbesserung

---

## Das Beste aus zwei Welten

Durch die Kombination von **EDEN** und **KSODI** entsteht ein neuartiger, praxistauglicher Bewertungsansatz:

- **EDEN** liefert die Reifestufenstruktur für Organisationen,  
- **KSODI** bringt eine differenzierte, KI-spezifische Bewertungsmethodik für Prompting ein.

Ein **KSODI-EDEN-Light-Agent** unterstützt Unternehmen dabei, ihre **KI-Readiness** und **Prompt-Kompetenz** zu erfassen, zu vergleichen und gezielt weiterzuentwickeln – messbar, nachvollziehbar und anschlussfähig an bestehende Standards.

---

## 2. Was ist KSODI – und was bringt es mir als Unternehmen?

### 2.1 Was ist KSODI?

**KSODI-light** ist ein Open-Source-Modell zur Bewertung der Prompt-Qualität in der Mensch-KI-Interaktion.  
Es basiert auf fünf klar definierbaren Dimensionen:

1. **K – Kontextklarheit**  
2. **S – Struktur**  
3. **O – Objektivität**  
4. **D – Deutlichkeit**  
5. **I – Informationsgehalt**

Jede Dimension wird auf einer Skala von 0 (sehr gut) bis 5 (nicht verwertbar) bewertet. Die Methode erlaubt eine granulare Analyse von Prompts und deren Entwicklung über Zeit – ohne Modellanpassung, ohne Fine-Tuning.

🧠 *Theoretischer Bezug:*  
Aktuelle Forschung zeigt, dass große Sprachmodelle durch strukturierte Prompts und Kontexte **implizit lernen**, auch ohne Training im klassischen Sinne.  
Ein Prompt kann im Transformer-Modell intern dynamische Anpassungen auslösen (z. B. low-rank updates in MLP-Blöcken), die das Modellverhalten während der Laufzeit beeinflussen.  
→ Siehe: [Dherin et al., 2025 – *Learning without training*](https://arxiv.org/pdf/2507.16003)

Dies unterstreicht die Relevanz klar formulierter, qualitativ hochwertiger Prompts – wie sie durch KSODI bewertet werden.

---

### 2.2 Was bringt der Einsatz von KSODI-light im Unternehmen?

#### ✅ *Konkrete Vorteile:*

- **Transparenz & Vergleichbarkeit:**  
  Promptqualität wird messbar – auch über Zeit.

- **Gezielte Verbesserung:**  
  Stärken und Schwächen werden sichtbar, Schulung wird gezielt steuerbar.

- **Effizienzsteigerung:**  
  Hochwertige Prompts führen zu besseren Antworten – und senken den Tokenverbrauch.

- **Compliance & Governance:**  
  Die Methode ist anschlussfähig an KI-Regularien (z. B. EU AI Act, ISO 42001) und Auditing-Strukturen.

- **Skalierbarkeit & Modularität:**  
  KSODI-light kann in bestehende Toolchains (z. B. LangSmith, n8n, Copilot Studio) integriert werden.

- **Kultureller Hebel:**  
  Durch strukturierte Reflexion entsteht eine **bewusstere KI-Nutzung** im Unternehmen – mit positiver Wirkung auf Innovations- und Lernkultur.

---

## 3. Bewertungsmodell nach KSODI: die „KSODI-Skala“

Im KSODI-Light-Modell bewertet die KI jede Nutzerfrage (Prompt) entlang der fünf KSODI-Dimensionen:

- **K – Kontextklarheit**  
- **S – Struktur**  
- **O – Objektivität**  
- **D – Deutlichkeit**  
- **I – Informationsgehalt**

Jede Dimension erhält einen Score von **0 (optimal)** bis **5 (nicht verwertbar)**.  
Der maximale KSODI-Score pro Prompt beträgt 25 Punkte.

Zusätzlich kann – je nach Konfiguration – für jede Dimension eine Einzelbewertung mit kurzer Begründung erfolgen.  
Prompts mit einer Bewertung **> 3 in einer beliebigen Dimension** werden vom Agenten nicht direkt beantwortet.  
Stattdessen erhalten Nutzende strukturierte Hinweise zur Verbesserung der jeweiligen Dimension(en), z. B. durch:

- Kontextnachforderung  
- Strukturvorschläge  
- Klarheits- oder Objektivitäts-Hinweise

Diese formative Rückmeldung ermöglicht ein unmittelbares Lernen durch Dialog – ganz im Sinne des Konzepts **Learning without Training** (Dherin et al., 2025).  
→ Das Modell „lernt“ nicht – aber der Mensch tut es, durch Resonanz mit dem System.

---

## 4. Zeitbasierte Aggregation

Zur Beobachtung von Entwicklungen im Promptverhalten werden die Bewertungen **zeitlich aggregiert**, z. B. über Wochen, Monate oder Projektphasen.  

Dabei werden weder konkrete Promptinhalte gespeichert noch personenbezogene Daten erhoben – lediglich die **Bewertungsskalen je Dimension** dienen als Grundlage für die Analyse.

Die zeitbasierte Aggregation erlaubt:

- **Erkennung von Fortschritt oder Rückfall** einzelner Teams  
- **Messung von Schulungseffekten**  
- **Langzeitbeobachtung von Promptkompetenz**  
- **EDEN-kompatibles Mapping auf Reifegrade**

Beispielhafte Mittelwertberechnung über Zeit:

```latex
\bar{K} = \frac{1 + 2 + 2}{3} = 1{,}67


_____

Wird z. B. der Dimension „Kontext“ in fünf Interaktionen folgende Durchschnittswerte zugeordnet:
4.1, 3.5, 2.2, 2.1, 1.6

…dann ergibt sich über Zeit:
\Sigma \bar{K} = \frac{4{,}1 + 3{,}5 + 2{,}2 + 2{,}1 + 1{,}6}{5} = 2{,}7


_____


⏳ Erweiterung: Evaluation-Loop

Um Lernfortschritte langfristig sichtbar zu machen, empfiehlt sich ein strukturierter Evaluationszyklus:

📈 Beispielhafte Taktung:
	•	T0 – Baseline-Messung vor Schulung
	•	T1 – Erste Re-Evaluation (z. B. 2 Wochen nach Schulung)
	•	T2 – Follow-up nach 6–8 Wochen
	•	T3+ – Turnusmäßige Wiederholung alle 3–6 Monate

Diese Zeitpunkte können im KSODI-System konfiguriert oder extern getrackt werden (z. B. via Excel, Dashboard, LangSmith oder Power BI).

💡 Vorteil: Die Kombination aus quantitativer Messung (KSODI-Scores) und qualitativer Reflexion (Prompt-Feedback) erlaubt eine ganzheitliche Bewertung – mit geringem Implementierungsaufwand.

⸻

🧠 Wissenschaftlicher Bezug

Die Idee, dass Promptqualität direkten Einfluss auf das Modellverhalten hat, wird durch aktuelle Forschung gestützt:

„Prompt tokens act as low-rank updates to the internal representations of the model – enabling learning without training.“
(Dherin et al., 2025)

Das bedeutet: Hochwertig strukturierte Prompts erzeugen modellinterne Dynamiken, die qualitativ bessere Antworten fördern – ohne dass das Modell feingetuned werden muss.
→ Für Unternehmen ist das zentral: Statt aufwendiger LLM-Optimierung genügt eine systematische Promptqualitätsentwicklung beim Menschen.

Diese Erkenntnis stärkt den strategischen Fokus von KSODI–EDEN-Light:
„Nicht das Modell ist das Bottleneck – sondern die Fähigkeit, mit ihm zu sprechen.“



_____

## 5. Mathematische Herangehensweise im „Light-Agenten“

### 5.1 Durchschnittswerte der fünf KSODI-Dimensionen berechnen

Jede Nutzeranfrage (Prompt) wird entlang der fünf KSODI-Dimensionen bewertet:

- **K – Kontextklarheit**  
- **S – Struktur**  
- **O – Objektivität**  
- **D – Deutlichkeit**  
- **I – Informationsgehalt**

Jede Bewertung erfolgt auf einer Skala von 0 bis 5.  
Zur Beobachtung von Entwicklungstendenzen werden für jede Dimension die Mittelwerte berechnet:

Beispiel – Drei Prompts mit Kontextbewertungen:

```latex
K_1 = 1,\quad K_2 = 2,\quad K_3 = 2


_____

Dann ergibt sich der Durchschnitt:

\bar{K} = \frac{K_1 + K_2 + K_3}{3} = \frac{1 + 2 + 2}{3} = 1{,}67


Diese Berechnung erfolgt für alle fünf Dimensionen separat:

\bar{K},\quad \bar{S},\quad \bar{O},\quad \bar{D},\quad \bar{I}


Optional kann zusätzlich der Gesamtwert für einen Prompt berechnet werden:

KSODI_\text{Total} = K + S + O + D + I


_____

5.2 Berechnung über Zeit

Wird eine größere Anzahl an Prompts über mehrere Zeitpunkte hinweg ausgewertet, kann ein temporaler Mittelwert gebildet werden – z. B. für die Dimension Kontext über fünf Interaktionen:

\bar{K}_\text{T} = \frac{4{,}1 + 3{,}5 + 2{,}2 + 2{,}1 + 1{,}6}{5} = 2{,}7


Dieser Wert kann genutzt werden, um Veränderungen in der Prompt-Qualität über Zeit zu messen – insbesondere im Vergleich vor und nach gezielten Schulungen oder KI-Einführungsmaßnahmen.

💬 Hinweis: Die Aggregation erfolgt anonymisiert und personenbezogen neutral – nur die bewerteten Skalenwerte werden für die Analyse herangezogen, nicht die Inhalte der Prompts.

⸻

6. KSODI-Mapping zu EDEN-Reifegraden


>> Tabelle









Die aggregierten KSODI-Mittelwerte ermöglichen eine Zuordnung zu Reifegraden im Sinne des EDEN-Modells.

🔢 Beispiel:
\bar{K} = 2{,}3,\quad \bar{S} = 1{,}4,\quad \bar{O} = 1{,}7,\quad \bar{D} = 3{,}2,\quad \bar{I} = 2{,}8

→ Der kombinierte KSODI-Ø-Wert über alle Dimensionen:

KSODI_\text{Ø} = \frac{\bar{K} + \bar{S} + \bar{O} + \bar{D} + \bar{I}}{5} = 2{,}28


🗺️ Zuordnung zur EDEN-Stufe

| KSODI Ø-Wert   | EDEN-Stufe         | Bedeutung                                                        |
|----------------|--------------------|-------------------------------------------------------------------|
| 3.0 – 5.0      | Sumpf              | Impulsive, unstrukturierte Nutzung von Prompts                   |
| 2.5 – <3.0     | Wiese              | Erste Strukturansätze im Prompting                               |
| 1.7 – <2.5     | Hain               | Systematische Entwicklung, Zielorientierung                      |
| 0.8 – <1.7     | Garten             | Reflektierte, strukturierte Nutzung für komplexe Aufgaben        |
| 0.0 – <0.8     | Garten mit System  | Kreative, professionelle Integration von KI durch konsistentes Prompting |


📊 Beispielhafte Agentenmeldung:

„Abteilung A befindet sich derzeit auf EDEN-Stufe 3 (Hain).
Stärken: Objektivität (Ø 1,8)
Potenzial: Struktur (Ø 2,6)
Empfehlung: Schulung zu Promptstruktur, Follow-up in 6–8 Wochen empfohlen.“

💡 Die Bewertung erfolgt automatisiert durch den KSODI-Light-Agenten, kann aber zusätzlich in Dashboards, Reports oder Copilot-Systeme eingebunden werden.

⸻

🧠 Wissenschaftlicher Bezug (Vertiefung):

Die Zuordnung zu EDEN-Stufen basiert auf der Annahme, dass Promptqualität über Zeit verbesserbar ist – nicht nur durch Lernen am Menschen, sondern auch durch Resonanzverhalten im Dialog mit dem System.

Das Paper Learning without training (Dherin et al., 2025) unterstützt diese Annahme:

„Prompt tokens induce low-rank internal updates, effectively modifying model behavior during inference.“
→ Hochwertige Prompts erzeugen implizite Anpassungen im Modell.

Für Unternehmen bedeutet das:
Selbst ohne eigenes LLM-Training kann über Promptentwicklung eine reale Qualitätssteigerung in der Mensch-KI-Kommunikation erreicht werden – messbar durch KSODI, sichtbar im Reifegrad durch EDEN.


_____


## 7. Vorteile des Ansatzes

Der KSODI–EDEN-Light-Ansatz bietet eine Reihe praxisrelevanter Vorteile für Unternehmen jeder Größe – insbesondere in der frühen Phase der KI-Einführung und im Rahmen kontinuierlicher Prozessentwicklung.

---

### ✅ Technische Vorteile

- **Einfache Implementierung**  
  Kann direkt in bestehende Toolchains eingebunden werden:  
  z. B. via LangSmith, n8n, Copilot Studio, Google Vertex AI, IBM watsonx etc.

- **Datenschutzfreundlich**  
  Es werden keine Promptinhalte gespeichert.  
  Bewertet werden ausschließlich anonymisierte Scores – konform mit DSGVO und unternehmensinternen Richtlinien.

- **Geringe Einstiegshürde**  
  Der KSODI-Agent funktioniert als „Light-Version“ ohne API-Programmierung oder komplexe IT-Infrastruktur.

---

### 🚀 Strategische Vorteile

- **Skalierbar und modular**  
  Kann unternehmensweit ausgerollt oder abteilungsweise getestet werden.

- **Sichtbarer Kompetenzaufbau**  
  Promptverhalten wird messbar – individuell, teambasiert oder organisatorisch.

- **Governance-fähig**  
  Ideal für Auditierung, Trainingscontrolling, Qualitätsmessung und AI-Governance.

- **Förderung von Prompt-Kompetenzkultur**  
  Die strukturierte Auseinandersetzung mit Prompts erzeugt eine nachhaltige Lern- und Innovationskultur im Umgang mit KI.

---

### 🧠 Wissenschaftlicher Kontext

Im Sinne aktueller Forschung (Dherin et al., 2025) wird das Ziel verfolgt, die **interaktive Qualität des Prompts** zu verbessern, da diese das Modellverhalten **signifikant beeinflussen kann** – selbst ohne klassisches Training.  
→ Der Agent wirkt damit als **struktureller Resonanzverstärker** im menschlich-gestützten KI-Einsatz.

---

## 8. Perspektive: Ausbaustufen & Full-Variante

### 8.1 Erweiterung auf KSODI-Full (optional)

Der hier beschriebene KSODI-Light-Ansatz fokussiert auf Einfachheit und Schnelligkeit.  

Für Unternehmen mit **eigener LLM-Infrastruktur**, regulatorischen Auditpflichten oder erhöhtem Bedarf an Tiefenauswertung kann eine **KSODI-Full-Variante** bereitgestellt werden. Diese umfasst:

- feinere semantische Gewichtungen pro Dimension  
- Integration von Tonalität, Kontextsättigung, Referenzdichte  
- Audit-Exportfunktionen und ISO-kompatible Dokumentationsformate  
- Verknüpfung mit Rollenprofilen (z. B. Prompt-Owner, Reviewer, Entwickler:innen)

Hinweis: Die Full-Version ist nicht Teil dieses Whitepapers und wird **nur auf Anfrage lizenziert**.

---

### 8.2 Implementierung: Agentenstruktur & Betriebsoptionen

- **Promptbasierte Light-Version**:  
  Ein einfacher Initialprompt kann vom Nutzer eingefügt werden (Copy & Paste).  
  Das Bewertungssystem läuft im Hintergrund über das Modell selbst oder über ergänzende Agenten (z. B. Moderations-Agent).

- **Agent-in-Agent-Architektur** (empfohlen):  
  Der KSODI-Light-Agent kann durch ein LLM selbst betrieben werden (z. B. GPT-4o oder Mixtral), das sowohl den Prompt bewertet als auch Vorschläge generiert.

- **MoE-Ansatz (Mixture of Experts)**:  
  Bei Bedarf kann eine Phase/Forge-Struktur eingesetzt werden, z. B. über LangGraph (Light Agent = Phase, Audit Agent = Forge).

---

### 📌 Hinweis zur Trennung von Bewertung & Optimierung

Während klassische Tools wie Promptfoo, Langfuse oder Copilot-Dashboards primär **Antwortverhalten, Syntax oder Guardrails** evaluieren, fokussiert KSODI auf die **semantische Qualität des menschlichen Inputs** – also auf die **Frage, nicht die Antwort.**

→ Dadurch wird ein neuer Fokus auf **menschliche Prompt-Kompetenz als organisationaler Faktor** ermöglicht – ein Bereich, der in aktuellen KI-Governance-Strategien oft unterrepräsentiert ist.

---

## Fazit

Der **KSODI–EDEN-Light-Agent** verbindet messbare Promptqualität mit organisationaler Reifebewertung – datensparsam, modular, ethisch anschlussfähig und technisch sofort umsetzbar.  

**Promptkompetenz wird sichtbar. Entwicklung wird steuerbar. Vertrauen wird messbar.**

---

## Lizenz

Dieses Whitepaper steht unter der Creative Commons Lizenz  
**CC BY 4.0 – Anne Steinacker-Folkerts & Patrick Barthelmäs**  
→ Bei Nutzung ist die Nennung der Urheberin erforderlich.

**GitHub-Repo**:  
[github.com/Alkiri-dAraion/KSODI-Methode](https://github.com/Alkiri-dAraion/KSODI-Methode)

Für Rückfragen, Lizenzen der Full-Variante oder Trainingsmaterialien wenden Sie sich bitte direkt an das Projektteam.


_____




