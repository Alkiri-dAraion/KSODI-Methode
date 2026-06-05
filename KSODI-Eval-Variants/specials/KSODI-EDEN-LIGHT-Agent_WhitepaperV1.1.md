# KSODI & EDEN

**Ein Reifegradansatz zur Prompt-Optimierung in Unternehmen**

Status: Proof of Concept / Arbeitsfassung

## Geplantes Tool

**KSODI-Light Agent mit EDEN-Mapping**

## Zielsetzung

Dieses Whitepaper skizziert eine leichtgewichtige Agentenstruktur zur Beobachtung und Bewertung von KI-Prompting in Unternehmen. Die Grundlage bildet die Open-Source-Methode **KSODI** ([CC BY 4.0 Lizenz](https://creativecommons.org/licenses/by/4.0/)) zur Optimierung der Mensch-Maschine-Interaktion.

Erweitert wird diese Methodik durch das etablierte **EDEN-Reifegradmodell**, das eine anschlussfähige Systematik für Unternehmensentwicklung und Prozessreife liefert.

Ziel ist ein niedrigschwelliger Proof of Concept, der ohne aufwendige Infrastruktur realisiert werden kann und perspektivisch entlang der gesamten Wertschöpfungskette skalierbar ist, zum Beispiel in Schulung, Auditing, Governance und Automatisierung.

## 1. Was ist das Reifegradmodell EDEN?

Das **EDEN-Reifegradmodell** ist ein Framework zur strukturierten Bewertung von Prozessorientierung und Organisationskompetenz in Unternehmen.

Ursprünglich von **BPM&O** entwickelt, analysiert EDEN Prozesse, Strukturen und Fähigkeiten entlang definierter Entwicklungsstufen und ermöglicht gezielte Verbesserungen.

Ein zentrales Merkmal von EDEN ist die bildhafte Stufenlogik, die über fünf Metaphern die Reife von Bereichen oder Organisationen einordnet:

| EDEN-Stufe | Bedeutung |
| --- | --- |
| Sumpf | Impulsive, unstrukturierte Arbeitsweise |
| Wiese | Erste Strukturansätze |
| Hain | Zielorientierte, systematische Entwicklung |
| Garten | Reflektiertes, komplexes Zusammenspiel |
| Garten mit System | Kreative Integration in die tägliche Arbeit |

Typische Anwendungsfelder von EDEN sind:

- Prozessmanagement und Organisationsentwicklung
- Digitalisierung und Automatisierung
- Einführung neuer Technologien, z. B. KI, RPA oder ERP
- ISO-Zertifizierung und Auditierung
- Change Management und Kulturentwicklung
- Benchmarking und kontinuierliche Verbesserung

## 2. Das Beste aus zwei Welten

Durch die Kombination von **EDEN** und **KSODI** entsteht ein praxistauglicher Bewertungsansatz:

- **EDEN** liefert die Reifestufenstruktur für Organisationen.
- **KSODI** bringt eine KI-spezifische Bewertungsmethodik für Prompting und Mensch-KI-Interaktion ein.

Ein **KSODI-EDEN-Light-Agent** kann Unternehmen dabei unterstützen, KI-Readiness und Prompt-Kompetenz zu erfassen, zu vergleichen und gezielt weiterzuentwickeln: messbar, nachvollziehbar und anschlussfähig an bestehende Standards.

## 3. Was ist KSODI?

**KSODI-light** ist ein Open-Source-Modell zur Bewertung der Prompt-Qualität in der Mensch-KI-Interaktion.

Es basiert auf fünf Dimensionen:

1. **K - Kontextklarheit**
2. **S - Struktur**
3. **O - Objektivität**
4. **D - Deutlichkeit**
5. **I - Informationsgehalt**

Jede Dimension wird auf einer Skala von 0 (sehr gut) bis 5 (nicht verwertbar) bewertet. Die Methode erlaubt eine granulare Analyse von Prompts und deren Entwicklung über Zeit, ohne Modellanpassung und ohne Fine-Tuning.

Aktuelle Forschung legt nahe, dass strukturierte Prompts und Kontexte das Modellverhalten während der Inferenz beeinflussen können. Das stärkt die Relevanz klar formulierter, hochwertiger Prompts, wie sie durch KSODI bewertet und verbessert werden sollen.

Siehe: [Dherin et al., 2025 - *Learning without training*](https://arxiv.org/pdf/2507.16003)

## 4. Nutzen im Unternehmen

Der Einsatz von KSODI-light kann Unternehmen in mehreren Bereichen unterstützen:

- **Transparenz und Vergleichbarkeit:** Promptqualität wird messbar und über Zeit vergleichbar.
- **Gezielte Verbesserung:** Stärken und Schwächen im Prompting werden sichtbar; Schulung kann gezielter gesteuert werden.
- **Effizienzsteigerung:** Hochwertige Prompts können zu besseren Antworten führen und Tokenverbrauch senken.
- **Compliance und Governance:** Die Methode ist anschlussfähig an KI-Regularien, z. B. EU AI Act, ISO 42001 und interne Auditstrukturen.
- **Skalierbarkeit und Modularität:** KSODI-light kann in bestehende Toolchains eingebunden werden, z. B. LangSmith, n8n oder Copilot Studio.
- **Kultureller Hebel:** Strukturierte Reflexion fördert eine bewusstere KI-Nutzung und stärkt Lern- und Innovationskultur.

## 5. Bewertungsmodell nach KSODI

Im KSODI-Light-Modell bewertet die KI jede Nutzerfrage entlang der fünf KSODI-Dimensionen:

- **K - Kontextklarheit**
- **S - Struktur**
- **O - Objektivität**
- **D - Deutlichkeit**
- **I - Informationsgehalt**

Jede Dimension erhält einen Score von **0 (optimal)** bis **5 (nicht verwertbar)**. Der maximale KSODI-Score pro Prompt beträgt 25 Punkte.

Je nach Konfiguration kann für jede Dimension zusätzlich eine Einzelbewertung mit kurzer Begründung erfolgen. Prompts mit einer Bewertung **> 3 in einer beliebigen Dimension** können vom Agenten zurückgespielt werden, ohne direkt beantwortet zu werden. Stattdessen erhalten Nutzende strukturierte Hinweise zur Verbesserung, z. B.:

- Kontextnachforderung
- Strukturvorschläge
- Klarheits- oder Objektivitäts-Hinweise

Diese formative Rückmeldung ermöglicht ein unmittelbares Lernen durch Dialog. Das Modell lernt dadurch nicht selbst im klassischen Sinne; der Mensch verbessert jedoch seine Prompt-Kompetenz in Resonanz mit dem System.

## 6. Zeitbasierte Aggregation

Zur Beobachtung von Entwicklungen im Promptverhalten werden Bewertungen zeitlich aggregiert, z. B. über Wochen, Monate oder Projektphasen.

Dabei werden keine konkreten Promptinhalte und keine personenbezogenen Daten gespeichert. Die Bewertungsskalen je Dimension dienen als Grundlage für die Analyse.

Die zeitbasierte Aggregation erlaubt:

- Erkennung von Fortschritt oder Rückfall einzelner Teams
- Messung von Schulungseffekten
- Langzeitbeobachtung von Promptkompetenz
- EDEN-kompatibles Mapping auf Reifegrade

Beispielhafte Mittelwertberechnung:

```latex
K_1 = 1,\quad K_2 = 2,\quad K_3 = 2

\bar{K} = \frac{K_1 + K_2 + K_3}{3}
        = \frac{1 + 2 + 2}{3}
        = 1{,}67
```

Wird der Dimension Kontext in fünf Interaktionen folgender Durchschnittswert zugeordnet:

```text
4.1, 3.5, 2.2, 2.1, 1.6
```

dann ergibt sich über Zeit:

```latex
\bar{K}_T = \frac{4{,}1 + 3{,}5 + 2{,}2 + 2{,}1 + 1{,}6}{5}
          = 2{,}7
```

Dieser Wert kann genutzt werden, um Veränderungen in der Prompt-Qualität über Zeit zu messen, insbesondere im Vergleich vor und nach gezielten Schulungen oder KI-Einführungsmaßnahmen.

## 7. Evaluation-Loop

Um Lernfortschritte langfristig sichtbar zu machen, empfiehlt sich ein strukturierter Evaluationszyklus:

| Zeitpunkt | Funktion |
| --- | --- |
| T0 | Baseline-Messung vor Schulung |
| T1 | Erste Re-Evaluation, z. B. zwei Wochen nach Schulung |
| T2 | Follow-up nach sechs bis acht Wochen |
| T3+ | Wiederholung alle drei bis sechs Monate |

Diese Zeitpunkte können im KSODI-System konfiguriert oder extern getrackt werden, z. B. über Excel, Dashboard, LangSmith oder Power BI.

Die Kombination aus quantitativer Messung und qualitativer Reflexion erlaubt eine ganzheitliche Bewertung mit geringem Implementierungsaufwand.

## 8. KSODI-Mapping zu EDEN-Reifegraden

Die aggregierten KSODI-Mittelwerte ermöglichen eine Zuordnung zu Reifegraden im Sinne des EDEN-Modells.

Beispiel:

```latex
\bar{K} = 2{,}3,\quad
\bar{S} = 1{,}4,\quad
\bar{O} = 1{,}7,\quad
\bar{D} = 3{,}2,\quad
\bar{I} = 2{,}8

KSODI_\text{Ø}
= \frac{\bar{K} + \bar{S} + \bar{O} + \bar{D} + \bar{I}}{5}
= 2{,}28
```

| KSODI Ø-Wert | EDEN-Stufe | Bedeutung |
| --- | --- | --- |
| 3.0 - 5.0 | Sumpf | Impulsive, unstrukturierte Nutzung von Prompts |
| 2.5 - <3.0 | Wiese | Erste Strukturansätze im Prompting |
| 1.7 - <2.5 | Hain | Systematische Entwicklung, Zielorientierung |
| 0.8 - <1.7 | Garten | Reflektierte, strukturierte Nutzung für komplexe Aufgaben |
| 0.0 - <0.8 | Garten mit System | Kreative, professionelle Integration von KI durch konsistentes Prompting |

Beispielhafte Agentenmeldung:

> Abteilung A befindet sich derzeit auf EDEN-Stufe 3 (Hain). Stärken: Objektivität (Durchschnitt 1,8). Potenzial: Struktur (Durchschnitt 2,6). Empfehlung: Schulung zu Promptstruktur, Follow-up in sechs bis acht Wochen empfohlen.

Die Bewertung erfolgt automatisiert durch den KSODI-Light-Agenten und kann zusätzlich in Dashboards, Reports oder Copilot-Systeme eingebunden werden.

## 9. Vorteile des Ansatzes

Der KSODI-EDEN-Light-Ansatz bietet praxisrelevante Vorteile für Unternehmen jeder Größe, besonders in frühen Phasen der KI-Einführung und im Rahmen kontinuierlicher Prozessentwicklung.

### Technische Vorteile

- **Einfache Implementierung:** Einbindung in bestehende Toolchains, z. B. LangSmith, n8n, Copilot Studio, Google Vertex AI oder IBM watsonx.
- **Datenschutzfreundlichkeit:** Es werden keine Promptinhalte gespeichert; bewertet werden ausschließlich anonymisierte Scores.
- **Geringe Einstiegshürde:** Die Light-Version kann ohne komplexe IT-Infrastruktur pilotiert werden.

### Strategische Vorteile

- **Skalierbarkeit:** Der Ansatz kann unternehmensweit ausgerollt oder abteilungsweise getestet werden.
- **Sichtbarer Kompetenzaufbau:** Promptverhalten wird messbar, individuell, teambasiert oder organisatorisch.
- **Governance-Fähigkeit:** Der Ansatz eignet sich für Auditierung, Trainingscontrolling, Qualitätsmessung und AI-Governance.
- **Prompt-Kompetenzkultur:** Die strukturierte Auseinandersetzung mit Prompts erzeugt eine nachhaltige Lernkultur im Umgang mit KI.

## 10. Perspektive: Ausbaustufen und Full-Variante

Der hier beschriebene KSODI-Light-Ansatz fokussiert auf Einfachheit und schnelle Umsetzbarkeit.

Für Unternehmen mit eigener LLM-Infrastruktur, regulatorischen Auditpflichten oder erhöhtem Bedarf an Tiefenauswertung kann eine KSODI-Full-Variante bereitgestellt werden. Diese umfasst:

- feinere semantische Gewichtungen pro Dimension
- Integration von Tonalität, Kontextsättigung und Referenzdichte
- Audit-Exportfunktionen und ISO-kompatible Dokumentationsformate
- Verknüpfung mit Rollenprofilen, z. B. Prompt-Owner, Reviewer oder Entwickler:innen

Hinweis: Die Full-Variante ist nicht Teil dieses Whitepapers und wird nur auf Anfrage lizenziert.

## 11. Implementierung: Agentenstruktur und Betriebsoptionen

Mögliche Betriebsoptionen:

- **Promptbasierte Light-Version:** Ein Initialprompt kann durch Nutzende eingefügt werden. Das Bewertungssystem läuft im Hintergrund über das Modell selbst oder über ergänzende Agenten.
- **Agent-in-Agent-Architektur:** Der KSODI-Light-Agent kann durch ein LLM betrieben werden, das sowohl den Prompt bewertet als auch Verbesserungsvorschläge generiert.
- **Mixture-of-Experts-Ansatz:** Bei Bedarf kann eine modulare Agentenstruktur eingesetzt werden, z. B. über LangGraph.

## 12. Trennung von Bewertung und Optimierung

Klassische Tools wie Promptfoo, Langfuse oder Copilot-Dashboards evaluieren häufig Antwortverhalten, Syntax, Guardrails oder Systemmetriken. KSODI fokussiert dagegen auf die semantische Qualität des menschlichen Inputs: also auf die Frage, nicht nur auf die Antwort.

Dadurch wird menschliche Prompt-Kompetenz als organisationaler Faktor sichtbar. Dieser Bereich ist in vielen KI-Governance-Strategien noch unterrepräsentiert.

## Fazit

Der **KSODI-EDEN-Light-Agent** verbindet messbare Promptqualität mit organisationaler Reifebewertung: datensparsam, modular, ethisch anschlussfähig und technisch niedrigschwellig umsetzbar.

**Promptkompetenz wird sichtbar. Entwicklung wird steuerbar. Vertrauen wird messbar.**

## Lizenz

Dieses Whitepaper steht unter der Creative Commons Lizenz:

**CC BY 4.0 - Anne Steinacker-Folkerts & Patrick Barthelmäs**

Bei Nutzung ist die Nennung der Urheberin erforderlich.

GitHub-Repository:

[github.com/Alkiri-dAraion/KSODI-Public](https://github.com/Alkiri-dAraion/KSODI-Public)

Für Rückfragen, Lizenzen der Full-Variante oder Trainingsmaterialien wenden Sie sich bitte direkt an das Projektteam.
