# Zeitliche Entwicklung der KSODI-Methode

English version: [KSODI Development Timeline](./KSODI_Timeline_since_2024-11.md)

## Öffentliche Einordnung

Diese Timeline dokumentiert die methodische Entwicklung von DOSI zu KSODI
sowie wichtige Beiträge, Reflexionsphasen und Implementierungsschritte.

Sie unterscheidet bewusst zwischen:

- methodischer Urheberschaft und konzeptioneller Entwicklung
- fachlicher Reflexion und interdisziplinärer Schärfung
- technischer Implementierung und Infrastrukturarbeit
- frühem Testing, Feedback und Anwendungserprobung

Technische Implementierung, Testing oder Infrastrukturbeiträge bedeuten nicht
automatisch methodische Urheberschaft. Wo eine Rolle nicht als Urheberschaft,
sondern als Reflexion, Umsetzung oder Testing zu verstehen ist, wird sie als
solche benannt.

Mathematische Detailformulierungen, Implementierungsdetails und laufende
Paper-Inhalte können in privaten Repositories, internen Arbeitsständen oder
späteren Veröffentlichungen getrennt geführt werden.

Personen werden in dieser öffentlichen Timeline überwiegend mit Vornamen
genannt. Firmen-, Arbeitgeber- und Plattformbezüge werden nur dort benannt, wo
sie für das Verständnis des öffentlichen Repositories notwendig sind.

## Meilensteine

| Datum | Teil der Methodik | Beteiligte | Was geschah | Rolle / Beitrag |
| --- | --- | --- | --- | --- |
| 11/2024 - 02/2025 | Vertiefte Nutzung von Chatbots, Beobachtung von Menschen, DOSI | Anne | Entdecken von Kommunikationsachsen; Formulierung von DOSI als Methode mit Scoring des User-Prompts durch KI. | Methodische Ursprungsidee und Entwicklung: Anne |
| 03.03.2025 | Formulierung KSODI und Weitergabe technischer Beobachtungen | Anne, Silke | Anne entdeckt das fehlende K, Navigation und Symbolik. Anne reflektiert mit Silke erste Ansätze zu R vor dem Hintergrund klassischer Kommunikationstheorie. Erste Weitergabe von Beobachtungen zu Voice-Konsistenzproblemen als Produktfeedback und technischer Kontext. | Methodische Entwicklung: Anne. Fachliche Reflexion: Silke, insbesondere zu Kommunikation und Resonanzfragen. |
| 06.03.2025 | Erstellung des öffentlichen Repositories mit KSODI-Light, CC BY 4.0 | Anne, Heiko | Heiko erstellt technisch das öffentliche Repository und die Lizenzstruktur. | Methodische Urheberschaft: Anne. Technische Repository- und Lizenzunterstützung: Heiko. |
| 14.03.2025 | Erweiterung des öffentlichen Repositories mit KSODI-Light | Anne, Heiko | Anne formuliert KSODI-Light mit Operatoren v1. Heiko erstellt Repository-Strukturen und reflektiert mit Anne beim Testen mit Anwendungsfällen. Anne und Heiko entwickeln erste Gedanken zu Feldern. | Methodische Entwicklung: Anne. Konzeptionelle Reflexion und technische Strukturunterstützung: Heiko. |
| 19.03.2025 | Weitergabe methodischer und technischer Beobachtungen | Anne | Weitere Weitergabe von Beobachtungen zu Voice-/Web-Konsistenzfehlern und zur KSODI-Methodik als Produktfeedback und technischer Kontext. | Anne |
| 25.03.2025 | KSODI in einem kontrollierten RAG-Test | Anne, Benjamin | Test mit derselben Architektur, demselben Embeddingmodell, derselben Datenbank und Prompt-Erweiterung mit KSODI. Bei gleichen Dokumenten entstehen mit KSODI-Light-Prompt präzisere, weitergehende und sauber eingerahmte Modellantworten. | Methodische Anwendung und Beobachtung: Anne. Frühes Testing und RAG-Feedback: Benjamin. Kein fortlaufender Implementierungs- oder Urheberstatus daraus abgeleitet. |
| 14.04.2025 | Dokumentation, Feedback-Kontext, Anpassung des öffentlichen Repositories, KSODI v1.0 | Anne, Silke, Heiko | Zusammenstellung der bis dahin erstellten Informationen zu KSODI, erste mathematische Formulierung, Hinweise zu möglicher Resilienzsteigerung und erste Ideen zu R. Teile wurden als Produktfeedback und technischer Kontext weitergegeben. Aus einem Rechtschreibfehler in der Interaktion mit ELKIM entsteht der Hangargedanke. | Methodische Entwicklung: Anne. Reflexion und Schärfung: Silke und Heiko. |
| 15.04.2025 | R-Definitionen, mathematisches Interaktionsmodell, KSODI v2.0 | Anne | Anne formuliert das erste mathematische Interaktionsmodell. Rückmeldungen auf zuvor geteiltes Produktfeedback und technischen Kontext wirkten ermutigend, stellen aber keine offizielle Validierung oder Übernahme durch einen externen Anbieter dar. | Methodische und mathematische Entwicklung: Anne. Rückbindung einzelner Grundlagenideen mit Heiko. |
| 20.04.2025 | Weitergabe sicherheitsbezogener Beobachtungen | Anne | Idee zur Kombination mit Security-Scanner-Methodik; Weitergabe von Beobachtungen zu eventuell möglichem Fingerprinting als technischer Kontext. | Anne |
| 22.04.2025 | Repository-Erweiterung um R, RSigma und RSigma(Hangar), KSODI v2.5 | Anne, Heiko, Silke | Anne erkennt R als Phasen-Modell von Mensch-KI-Interaktion. Erste mathematische Formulierung mit einem KI-Modell. Erste Ideen zu Takt und Zeit. | Methodische Entwicklung: Anne. Fachliche Impulse: Heiko zu Signalperspektive, Silke zu Resonanz. |
| 03.05.2025 | Weitere Formalisierung der Operatoren, K, 2-Phasen-Version, KSODI v2.6 - 2.8 | Anne, Patrick | K-Mathematik nach Erkennen der möglichen Architektur-Agnostik. Reflexion über die Form von R. | Methodische Entwicklung: Anne. Frühe technische und konzeptionelle Reflexion mit Patrick. |
| 18.05.2025 | KSODI-Prompt für Patrick, Chatbot-Implementierung | Anne, Patrick | Arbeitsthese: R könnte als Vektor oder komplexere Form dargestellt werden. Frage: Ist es nur Resonanz? | Prompting und methodische Hypothesen: Anne. Implementierungsbezogene Reflexion: Patrick. |
| 16.06.2025 | Entdeckung von IDAS und SIRA als notwendiger Rahmen | Anne | Erkenntnis: Methode ohne Rahmen und Protokoll ist nicht ausreichend legitimierbar. Leitfragen: In welchem Kontext beobachten wir? Mit welchem Ziel? Erste Trennung von Observability und Alignment. | Anne |
| 17.08.2025 | Framework-Formalisierung, Repository-Update, mathematisches Interaktionsmodell v2.9 | Anne, Heiko | Festlegung des Rahmens und Anpassung des Protokolls. Signaltheorie für Beobachtung, Takt und Zeit werden relevant. | Methodische Entwicklung: Anne. Konzeptionelle Schärfung von Methode, Framework und Protokoll mit Heiko. |
| 19.08.2025 | Erweiterte Ideen mit Patrick | Anne, Patrick, Heiko | Überprüfung von R und Möglichkeit der Implementierung nach paralleler methodenstrenger Nutzung von KSODI in mehreren KI-Accounts. | Methodische Reflexion: Anne. Implementierungsbezogene Reflexion: Patrick. Zusätzliche Rückbindung: Heiko. |
| 08/2025 - 11/2025 | Erstellung eines KSODI-Light-Agent-Prototyps | Patrick, Anne | Patrick implementiert Infrastruktur. Anne liefert Prompting und methodische Vorgaben. | Substantielle technische Implementierung und Infrastruktur: Patrick. Methodische Vorgaben und Prompting: Anne. |
| 02.11.2025 | R als Resonanzkörper | Anne, Patrick, Heiko, Silke | Überlegungen zur Form der Interaktion, Feld/Raum. Silke formuliert: Resonanz ist kein Add-on, sondern Fundament. | Methodische Entwicklung: Anne. Formen aus Implementierungs- und Mathematikperspektive sowie erste Infrastruktur: Patrick. Physikalische Formperspektive: Heiko. Resonanz- und Interaktionsreflexion: Silke. |
| 06.11.2025 | R ist nicht Interaktionskohärenz | Silke, Anne, Patrick | Kohärenz und Resonanz werden getrennt. Interaktion wird als flüchtig beobachtet. Reflexion über Verortung einer Entität gegenüber einer anderen in der Interaktion. | Methodische Trennung: Anne. Theoretische Schärfung: Silke. Vorangegangene Reflexion zu IK/R: Patrick. |
| 18.11.2025 | Erste Definition von IK getrennt von R, KSODI v2.93 | Anne, Heiko | IK als Interaktionskohärenz; R als Resonanz; Messverfahren; Operator-Anpassungen. | Methodische Definition: Anne. Mathematisch-technische Plausibilisierung über Ableitungen: Heiko. |
| 03.01.2026 | IK als streng getrennte logische Interaktionskohärenz, KSODI v2.94 | Anne, Patrick, Heiko | Didaktischer Prompt mit Reflexionsphase und Output-Phase. Präzisierung von IK. | Methodische Präzisierung: Anne. Reflexion mit Patrick und Heiko. |
| 28.01.2026 | Erweiterte Definition von IK v3.0 bis v3.41 | Anne, Patrick, Silke, Heiko | IK als Trennung von R; Messverfahren; Operator-Anpassungen; erste Implementierungsarchitektur mit containerisierten Services je Operator und ersten Visualisierungen. | Methodische Erweiterung: Anne. Reflexion und Schärfung mit Patrick, Silke und Heiko. |
| 03.02.2026 | Definition und Trennung von Z-Vec und R0, Übergang zu v3.42 ff. | Anne, Patrick, Heiko, Silke | Messung ohne Zustand ist nicht möglich. Verbindungsmodell Mensch-Maschine: KSODI > IDOSK > C > IDOSK > KSODI > C usw. | Methodische Entwicklung von Signalfluss, Zuständen und States: Anne. Reflexion mit Patrick, Heiko und Silke. |
| 04.02.2026 | Observability ist nicht Alignment und nicht Zielerreichung | Anne | Trennung von Observability und Alignment in KSODI v3.0 bis v3.66. | Anne |
| 25.02.2026 | Trennung von R_struc und R_phase, R-Full v3.41e | Anne, Heiko, Patrick | Takt und Pacing in der Interaktion; saubere Trennung; Anpassung der Implementierung. | Methodische Trennung: Anne. Erneute Präzisierung von Operatoren, Zuständen, Projektion und Vektoren mit Heiko. Implementierungsanpassung: Patrick. |
| 14.03.2026 | 3-Hangar-Theorie und Operatorenumkehr beim Senden vs. Empfangen | Anne | Jeder Agent bzw. jede Entität denkt und verarbeitet getrennt. Im flüchtigen Raum der Begegnung finden Beteiligte zusammen: H_H, H_M und H_geteilt. Bezug zu Autopoiesis und Dialogtheorie. Gedankliche Trennung von KSODI-Light-(Multi-)Agenten und KSODI-Standard-Eval/-Full-Observer-Modellen; erste Ideen zu Self-Alignment. | Methodische Strukturierung von Z, IK und R mit Sigma und Sigma(Hangar) für das erste Paper: Anne. |
| 23.04.2026 | Modelle von innen beobachten lassen vs. Modelle in der Interaktion beobachten | Anne, Heiko | Saubere Trennung von KSODI und anderen Methodiken. Paper-Bezug: interne Modellbildung und Beobachtung von Interaktion. | Methodische Reflexion: Anne. Rückbindung mit Heiko. |
| bis 10.05.2026 | Beginn Paper | Anne | Fertig bis 10.05.2026: Abstract, Contributions, Einleitung, Herkunft, KSODI-Operatoren, Z-Vektor, IK, R0 und weitere Grundteile. | Paper-Ausarbeitung und methodische Verdichtung: Anne. |
| ab 10.05.2026 | Weiterarbeit Paper | Anne | IK_rel, R-Full mit R_struc und R_pace, Implikationen, Limitationen, Conclusion, Annex B. | Notwendigkeit und Schärfung von IK_rel für dyadische IK im geteilten flüchtigen Hangar: Anne. |
| anstehend | Prüfung der Rollen und Beiträge | Anne | Prüfung und Nachschärfung der Attributionen. | Anne |
| anstehend | Übergabe überarbeiteter Operatoren V3.5 als Referenzversion | Anne, Patrick | Überarbeitung der Operatoren mit Z, IK, IK_rel und aktuellem Stand zu R; Überarbeitung der Zustands- und Resonanzlogik in der Implementierung. | Methodische Spezifikation: Anne. Umsetzungsvorbereitung: Patrick. |
| anstehend | Implementierung | Patrick | Implementierung der methodischen Strukturen in der Infrastruktur. | Technische Implementierung und Infrastruktur: Patrick. |
| anstehend | Testen | Anne, Patrick | Gemeinsames Testen der Implementierung und Beobachtungsstrecke. | Methodisches Testing: Anne. Technisches Testing und Implementierungsrückkopplung: Patrick. |

## Öffentliche Abgrenzung

Diese Timeline ist als Entwicklungs- und Beitragsübersicht gedacht. Sie ersetzt
keine vollständige mathematische Spezifikation und keine Paper-Fassung. Für das
öffentliche Repository ist sie geeignet, um transparent zu zeigen, dass KSODI,
IDAS und SIRA empirisch, iterativ und interdisziplinär entstanden sind, während
tiefergehende Formulierungen noch in Arbeit sind oder getrennt geführt werden.
