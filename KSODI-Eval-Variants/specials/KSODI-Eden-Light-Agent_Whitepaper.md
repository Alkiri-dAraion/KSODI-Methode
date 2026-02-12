KSODI & EDEN
- ein Reifegradansatz zur Prompt-Optimierung in Unternehmen
 
 
Geplantes Tool:
KSODI-Light Agent mit EDEN-Mapping (PoC)
 
Zielsetzung
 
Dieses Whitepaper skizziert eine minimalistische Agentenstruktur zur optimierten Beobachtung und Bewertung von KI-Prompting in Unternehmen, basierend auf der Open-Source-Methode „KSODI“ (CC BY 4.0 Lizenz) zur Optimierung der Mensch-Maschine-Interaktion und mit einer neuartigen Erweiterung des EDEN-Reifegradmodells.
 
Ziel ist ein Proof-of-Concept (PoC), der einfach implementierbar ist und später umfangreiche Erweiterungsmöglichkeiten für verschiedenste Bereiche einer Wertschöpfungskette liefern kann.
 
 
1. Was ist das „Reifegradmodell EDEN – und wo wird es eingesetzt?
 
Das EDEN-Reifegradmodell ist ein etabliertes Framework zur systematischen Bewertung und Entwicklung von Prozessorientierung und Organisationskompetenz in Unternehmen.
Ursprünglich von BPM&O entwickelt, unterstützt EDEN Unternehmen dabei, ihre Prozesse, Strukturen und Fähigkeiten entlang klar definierter Entwicklungsstufen zu analysieren und gezielt zu verbessern.
 
EDEN arbeitet dabei mit anschaulichen Metaphern (z. B. Sumpf, Wiese, Hain, Garten, Garten mit System), die den jeweiligen Reifegrad einer Organisation oder eines Bereichs bildhaft und verständlich machen. Jede Stufe steht für einen spezifischen Entwicklungszustand – von impulsiver, unstrukturierter Arbeitsweise bis hin zu professioneller, kreativer und systematischer Integration von Prozessen und Technologien.

Typische Einsatzbereiche von EDEN:
 
• Prozessmanagement und Organisationsentwicklung
• Digitalisierung und Automatisierung von Geschäftsprozessen
• Einführung neuer Technologien (z. B. KI, RPA, ERP)
• Auditierung und Zertifizierung (z. B. ISO-Normen)
• Change Management und Kulturentwicklung
• Benchmarking und kontinuierliche Verbesserung
 
 
 
Das Beste aus zwei Welten:

Durch die Kombination von EDEN mit KSODI entsteht ein innovativer Ansatz, der die bewährte Reifegradlogik von EDEN mit der granularen, KI-spezifischen Bewertungsmethodik für Interaktionsqualität von KSODI verbindet.
Unternehmen, die EDEN bereits nutzen, können mit einem „KSODI-EDEN-Light-Agenten“ ihre KI- und Prompt-Kompetenz gezielt weiterentwickeln und die Transformation in Richtung „KI-readyness“ und „Prompt-readyness“ messbar und steuerbar gestalten.
 
 
2. Was ist KSODI – und was bringt es mir als Unternehmen?
 
2.1. Was ist KSODI?
 
KSODI-light ist ein Open-Source-Bewertungsmodell aus Deutschland, das die Qualität von KI-Prompts anhand fünf Dimensionen misst:
 
• Kontext
• Struktur
• Objektivität
• Deutlichkeit
• Informationsgehalt
 
KSODI-light ist Teil eines größeren Frameworks (KSODI und Framework) zur Optimierung der Mensch-KI-Interaktion anhand validierbarer und skalierbarer Metrik.
 
 
2.2. Was bringt ein Einsatz der „KSODI“-Metrik dem Unternehmen?
 
• Transparenz und Vergleichbarkeit:
o Die Qualität von Prompts wird messbar und über Zeit vergleichbar gemacht.
• Gezielte Verbesserung:
o Schwächen und Stärken im Prompting werden sichtbar, so dass gezielte Schulungsmaßnahmen und Prozessoptimierungen möglich sind.
• Effizienzsteigerung:
o Durch bessere Prompts werden KI-Interaktionen effizienter, der Tokenverbrauch sinkt und die Ergebnisqualität steigt.
• Governance und Compliance:
o Die Bewertung kann als Grundlage für Governance-Maßnahmen und zur Einhaltung von Standards (z. B. AI-Act, Datenschutz) genutzt werden.
• Skalierbarkeit:
o Das Modell „KSODI-light“ ist minimalistisch und kann einfach auf verschiedene Unternehmensbereiche und Prozesse ausgerollt werden.
• Kulturentwicklung:
o Die systematische Reflexion und Verbesserung des Promptings fördert eine lernende, innovationsfreundliche Unternehmenskultur.
 
 
3. Bewertungsmodell nach KSODI: die „KSODI-Skala“
 
Jede Nutzerfrage (Prompt) aller Mitarbeitenden wird (bei jeder Interaktion und über Zeit) von einem implementierten „KSODI-light-Agenten“ anhand der fünf KSODI-Dimensionen durch die KI bewertet:
 
• K – Kontextklarheit  
• S – Struktur  
• O – Objektivität  
• D – Deutlichkeit  
• I – Informationsgehalt  
 
Jede Dimension erhält einen Score von 0 bis 5, wobei 0 für perfekt steht und 5 für nicht verwertbar. Die maximale Punktzahl pro Prompt ist also: 5*5 = 25. Der Single-Score je Prompt wird (auf Wunsch) für jede der 5 Dimensionen vom Modell ausgegeben und begründet.
Fragen mit einer Bewertung >3 werden vom Modell nicht beantwortet, es wird die Dimension beschrieben, in der vertiefende Angaben benötigt werden und Hinweise zur Ergänzung gegeben.
 
Durch Nutzung von KSODI kann somit über Zeit das Prompt-Verhalten des Nutzenden nachhaltig verbessert werden, was insbesondere für wesentliche Rollen (z.B. Agent-Developer oder Prompt-Owner) in der Wertschöpfungskette mit Blick auf Automatisierungsprozesse breite Optimierungsmöglichkeiten bereitstellt.
 
Governance
Optional kann mit dieser Methodik neben den Prompt auch die Antwort der KI mit Blick auf den AI Act, die KI-VO und ISO – Standards bewertet werden und in Audits herangezogen werden (Governance-Relevanz).
Dieser Ansatz bietet die zusätzliche Möglichkeit, nachhaltig und schlüssig die Antworten einer KI unter Einbeziehung des bereitgestellten Prompt zu überprüfen und Halluzinationen von prompt-basierter semantischer Drift oder Kompromittierungs-Versuchen (Governance) zu unterscheiden.
Besonders durch letzteres kann die Sicherheit im Umgang mit eingesetzten Sprachmodellen deutlich erhöht werden.
 
 
4. Zeitbasierte Aggregation
 
Bei einer Evaluation nach KSODI - EDEN werden über einen definierten Zeitraum (z. B. Woche/Monat) die KSODI-Scores ohne Daten der Mitarbeitenden oder Zuordnung der Prompts erhoben.
 
Diese Evaluierung kann zusammen mit EDEN verwendet werden, um über diesen definierten Zeitraum hinweg mit einer überprüfbaren Metrik „KI-Readyness“ oder „Prompt-Readyness“ zu messen, also wie sich die Fähigkeit der Mitarbeitenden bei der Nutzung gezielter Prompt über Zeit verhält – und ob sich qualitative Veränderungen ergeben.
 
Herkömmliche Methoden über übliche Tools wie Purview bei MS Copilot 365, Langsmith, Promptfoo u.a. etc. vermessen die Anzahl der Prompts, loggen Interaktionen mit Blick auf die Arbeitsverteilung innerhalb von Agentensystemen und überprüfen Prompts, Kontext und beispielsweise sensibles Wording oder Semantik und Syntax unter festen Vorgaben (Guardrails und Constrains) – ohne den Nutzenden und dessen Promptverhalten in die Betrachtung einzubeziehen.
 
Typische Fehler wie unklare, ungerichtete Prompt, bleiben daher in klassischen Tools oft undetektiert und können somit auch nicht mit Optimierungsansätzen gezielt adressiert werden.
 
Neben schwachen, unbrauchbaren Antworten der KI hat diese Problemstellung häufig einen extrem hohen, kostenintensiven Token-Verbrauch für Unternehmen, gerade im Zug einer KI-Einführung, zur Folge – losgelöst vom Problem der steigenden Unzufriedenheit der User, die durch schwache und fehlerhafte KI-Antworten oder gar Halluzinationen oder semantische Drift teils nachhaltig abgeschreckt werden.
 
 
⇨ Hinweis:
Ein „guter Prompt“ zeichnet sich durch eine „zielgerichtete Aufgabenstellung“ mit Kontextbezug, sauberer Struktur, Objektivität und Klarheit aus und muss alle relevanten Informationen enthalten, die die KI zur Arbeitserledigung benötigt.
 

Mit Blick auf ein „Prompt-SOP“ (Standard Operating Procedure*) bedeutet das exemplarisch:
• Anweisungen zum gewünschten Prozessablauf müssen im Prompt enthalten sein,
• ebenso Zielsetzung,
• etwaige Zuständigkeiten Beteiligter,
• eine gewünschte Ablaufbeschreibung für die KI-Interaktion im Sinne von „Wir legen so los und wollen dort hin“ und auch
• ggf. relevante Sicherheitsvorschriften (Soft Constrains wie: „Du [Agent] weichst nicht auf folgende Themen aus: „Freitzeit etc….“).
 
Ergänzend kann ein Prompt Referenzen auf zugehörige Arbeitsanweisungen, Checklisten oder Formulare enthalten.
 
* Eine SOP im Zusammenhang mit KI beschreibt den idealen Ablauf für die KI-Interaktion und kann als Vorlage für strukturierte Prompts dienen.“
 
 
 
5. Einfache mathematische Herangehensweise im „Light-Agenten“
 
5.1. Durchschnittswerte der fünf KSODI-Dimensionen berechnen
 
Jede Nutzeranfrage (Prompt) wird entlang der fünf KSODI-Dimensionen bewertet: Kontextklarheit (), Struktur (), Objektivität (), Deutlichkeit (), Informationsgehalt ().
Die Bewertung erfolgt – wie zuvor beschrieben - auf einer Skala von 0 bis 5 je Dimension.

Für einen Zeitraum werden die Mittelwerte der Dimensionen berechnet:

 
⇨ Für jede Dimension wird über alle bewerteten Prompts hinweg der Durchschnitt berechnet.
 
o Beispiel: Wir betrachten eine Interaktion mit 3 Prompts und jeweiliger Kontext-Bewertung ( ) = 1, 2, 2, dann ist die Bewertung in der Dimension „Kontext“:
 
 
Die Werte 1, 2 und 2 wurden addiert und durch die Anzahl der Bewertungen (3) geteilt. Das Ergebnis = 1,67 ist der Mittelwert für diese Dimension.
 

5.2. Berechnung über Zeit
 
Berechnung des Durchschnitts aller Gesamtpunktzahlen in einer Dimension über mehrere Interaktionen hinweg (Beispiel: Kontext):
 
Ausgewertet wurden nach KSODI beispielhaft 30 Prompts in 5 Interaktionen mit Gesamtwerten in der Dimension „Kontext“ über einen bestimmten Zeitraum (z. B. 1 Tag).
 
Zuerst wird der Durchschnitt je Interaktion berechnet:
Die Bewertung für iwäre jeweils 4,1 | 3,5 | 2,2 | 2,1 | 1,6.
Dann berechnet sich die Summe des Durchschnitts von über Zeit ( ) wie folgt:
 
 
 
Die Werte von werden addiert und durch die Anzahl der Interaktionen geteilt.
 
⇨ Das Ergebnis ist der Mittelwert für die Dimension „Kontext“ für den gewählten Zeitraum – und fließt direkt in die EDEN-Bewertung ein.
 
 
 
6. KSODI-Mapping zu EDEN-Reifegraden
 
Die KSODI-Gesamtbewertung wird zur Überprüfung der Prompt-Qualität der Mitarbeitenden in allen Phasen der KI-Transformation im Anschluss maschinell durch den KSODI-Light-Agenten auf die EDEN-Stufen (nach BPM&O) gemappt, dabei werden zunächst alle 5 Dimensionen über Zeit zusammengezählt:
 
Beispiel:
= 2,3
= 1,4
= 1,7
= 3,2
= 2,8
 
KSODI-Wert Ø: 2,28
 
Anschließend erfolgt ein Mapping auf die EDEN-Stufen, etwa wie in folgender Tabelle angegeben:

KSODI Ø-Wert (0–5)
EDEN-Stufe*              
Bedeutung    
3 - 5
Sumpf
impulsive, unstrukturierte Nutzung von Prompts  
2,5 – 3
Wiese
erste Ansätze von Struktur beim Prompting                
1,7 – 2,5
Hain
beginnende Systematik mit Blick auf Zielerreichung, auch für erweiterte Aufgaben                  
0,8 – 1,6
Garten
bewusste Gestaltung, reflektierte Nutzung  von Prompting, auch für komplexere Aufgaben
0 – 0,8
Garten mit System
professionelle, kreative KI-Integration in die tägliche Arbeit durch gezielten Prompt-Einsatz in jeder KSODI - Dimension
 
*Stufenbezeichnungen adaptiert am Reifegradmodell EDEN
*anpassbar an individuelle Unternehmens-Metrik
 
 
 
6.1. Beispiel-Feedback des „KSODI-Light-Agenten“ bei einer EDEN-Prüfung der „KI-Readyness“
 
Setting und Messung:
Ein KSODI-Agent ist im Unternehmen seit einigen Monaten als „Light-Version“ im Einsatz.
Im Versuchszeitraum wurden in der Beispielfirma in der Abteilung A pro Tag etwa 300 Interaktionen mit KI durchgeführt (Auswertung durch KSODI-Agent-Light).
 
Dabei betrug die gemessene durchschnittliche Interaktionslänge im Beispiel 16 Iterationen und 35.900 Token. Über einen Zeitraum von 2 Wochen wurden in 02/2025 und 05/2025 vor und nach Schulungen zu Prompting durch den Agenten auch KSODI-Messungen durchgeführt.
 
 
1. Ergebnis, Auswertung und Empfehlung durch den Agenten:
 
⇨ „Abteilung A befinden sich derzeit auf EDEN-Stufe 3 (Hain).
o Die Stärken der Abteilung im Prompting liegen aktuell in Objektivität bei : Ø 1,8.
o Struktur (Ø 2.6) jedoch zeigt noch Potenzial zur Entwicklung.“
o Der Tokenverbrauch je Aufgabe kann durch Anhebung des KSODI-Score um 0,5 bei „Struktur“ deutlich reduziert werden.
 
2. Empfehlung durch den Agenten:
o Eine vertiefende Prompting-Schulungsmaßnahme wird empfohlen.
o Weitere Evaluierung sollte ca. 8 Wochen nach der erneuten Schulung erfolgen.
 
 
 
7. Vorteile des Ansatzes
 
- Einfache Implementierung
(z. B. mit LangSmith, Copilot Studio, Agent Builder, n8n, Google Vertex AI, IBM watsonx etc.)  
- Datenschutzfreundlich
(keine Speicherung von Prompt-Texten über das gesetzlich geforderte Niveau zwecks Auditierung notwendig)  
- Leicht kommunizierbar im Unternehmensumfeld  
- Skalierbar und erweiterbar
 
⇨ Promptverhalten wird nachhaltig und langfristig optimiert durch den möglichen Einsatz zielgerichteter Team-Schulungen mit Blick auf Automatisierungspotentiale, Optimierung von Tokenmengen, Aufgabenstellung und Ergebnisqualität.
⇨ Parallele Auditierung der Prompt durch einfache Audit-Tools für Prompts wie Promptfoo oder komplexere Varianten wie Langsmith, etc. ist möglich und empfehlenswert
 
 
 
8. Perspektive: Ausbaustufen und ggf Erweiterung auf KSODI-Full für tiefe Auditierung
 
8.1. Möglichkeiten zur Optimierung der KI-Nutzung und Förderung optionaler Automatisierungsansätze  im Unternehmen, mit KSODI-EDEN-Light möglich:
 
• Gezielte Schulungen für Prompt-Verbesserung mit Blick auf SOP
• Gezielte, vertiefende Schulungen für Prompt-Owner
• Überprüfung bestehender SOP auf KI-Readyness
• Auswertung von Schulungsfeedback & Einsatz von Coaching-Modulen
• Dashboard-Integration

8.2. Implementierung in einer Agentenstuktur
 
Die einfache KSODI-Nutzung kann ohne EDEN-Metrik auf einfache Weise mit reinen Soft-Prompt auf User-Seite gestartet werden. Dazu wird ein spezifischer KSODI-Prompt, der für das jeweilige Unternehmen geringfügig angepasst wird, mit Copy&Paste im User-Account hinterlegt und unterliegt damit den Guardrails und Constrains des jeweiligen KI-Systems des Unternehmens selbst. Bewertungen erhält in diesem Fall allein der User, was diese Art der Implementierung mit Blick auf eine Einbindung in das Reifegradmodell EDEN und eine dadurch bedingte Optimierung der KI-Nutzung im Unternehmen ausschließt.
 
Es empfiehlt sich zunächst eine einfache Implementierung wie oben beschrieben mit Standard-Tools. Eine 1-Modell-Architektur eignet sich ebenso wie ein MoE (Mixture of Experts). Der Prompt zum KSODI-EDEN-Agenten wird direkt im System-Prompt des ersten LLM hinterlegt, das der User adressiert.
Die Ergebnisse der Bewertung werden durch das LLM für jeden Prompt im Hintergrund durchgeführt, aus den Antworten extrahiert – und wie die Antworten (gemäß den gesetzlichen Vorgaben) für eine anschließende Auswertung gespeichert.
 
Eine Meta-Metrik, etwa in Form eines Moderations-Agenten für den KSODI-EDEN-User-Agenten, kann separat aufgebaut werden. Dieser kann bei Bedarf/ vorhandenen Rechten automatisierte Anpassungen im User-Agenten zur Optimierung der Interaktion vornehmen.
 
 
8.3. Erweiterung auf KSODI-Full für tiefe Auditierung
 
Hinweis:
Auf die „KSODI-Full-Version“ wird aufgrund der Komplexität der sehr präzisen Metrik und der aufwändigeren Implementierung nicht eingegangen, da sie derzeit über den üblichen Bedarf von Unternehmen ohne eigenen LLM-Betrieb hinausgeht.
 
 
 
Fazit
 
Der EDEN–KSODI-Light Agent bietet eine erste, robuste und einfache sowie skalierbare Methode zur Bewertung der KI-Kompetenz im Unternehmen – mit minimalem Implementierungsaufwand und klarer Erweiterungsperspektive.
 
 
 
⇨ Ein KSODI-Light-Agent mit den Schwerpunkt „Tonalität“ kann hier (KSODI-Light-Agent-Langsmith_Tonalität) angesehen werden.
2


## Lizenz
Dieses Whitepaper ist unter der Creative Commons Lizenz CC BY 4.0 veröffentlicht.  
Sie dürfen es teilen und anpassen, solange Sie den Urheber (Anne Steinacker-Folkerts) nennen.

📩 Für die kommerzielle Nutzung, tiefere Auditierung oder Trainingsmaterialien der KSODI-Full-Version kontaktieren Sie uns bitte direkt.