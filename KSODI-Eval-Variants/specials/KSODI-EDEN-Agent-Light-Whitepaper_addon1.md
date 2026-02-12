# KSODI & EDEN  
**Ein Reifegradansatz zur Prompt-Optimierung in Unternehmen**  

## Geplantes Tool:  
**KSODI-Light Agent mit EDEN-Mapping (PoC)**

---

## Zielsetzung

Dieses Whitepaper skizziert eine minimalistische Agentenstruktur zur optimierten Beobachtung und Bewertung von KI-Prompting in Unternehmen, basierend auf der Open-Source-Methode **„KSODI“** ([CC BY 4.0 Lizenz](https://creativecommons.org/licenses/by/4.0/)) zur Optimierung der Mensch-Maschine-Interaktion – erweitert durch das Reifegradmodell **EDEN**.

Ziel ist ein Proof-of-Concept (PoC), der einfach implementierbar ist und später umfangreiche Erweiterungsmöglichkeiten für verschiedenste Bereiche einer Wertschöpfungskette liefern kann.

---

## 1. Was ist das „Reifegradmodell EDEN“ – und wo wird es eingesetzt?

Das **EDEN-Reifegradmodell** ist ein etabliertes Framework zur systematischen Bewertung und Entwicklung von Prozessorientierung und Organisationskompetenz in Unternehmen.  

Ursprünglich von **BPM&O** entwickelt, unterstützt EDEN Unternehmen dabei, ihre Prozesse, Strukturen und Fähigkeiten entlang klar definierter Entwicklungsstufen zu analysieren und gezielt zu verbessern.

EDEN arbeitet mit anschaulichen Metaphern wie:

- **Sumpf**
- **Wiese**
- **Hain**
- **Garten**
- **Garten mit System**

Jede Stufe steht für einen spezifischen Entwicklungszustand – von impulsiver, unstrukturierter Arbeitsweise bis hin zu kreativer und systematischer Prozess- und Technologieintegration.

**Typische Einsatzbereiche:**

- Prozessmanagement & Organisationsentwicklung  
- Digitalisierung und Automatisierung von Geschäftsprozessen  
- Einführung neuer Technologien (z. B. KI, RPA, ERP)  
- Auditierung & Zertifizierung (z. B. ISO-Normen)  
- Change Management & Kulturentwicklung  
- Benchmarking & kontinuierliche Verbesserung  

---

## 2. Was ist KSODI – und was bringt es mir als Unternehmen?

### 2.1 Was ist KSODI?

**KSODI-light** ist ein deutsches Open-Source-Bewertungsmodell, das die Qualität von KI-Prompts anhand folgender fünf Dimensionen bewertet:

1. **K** = Kontextklarheit  
2. **S** = Struktur  
3. **O** = Objektivität  
4. **D** = Deutlichkeit  
5. **I** = Informationsgehalt

Jede Dimension wird auf einer Skala von `0` (perfekt) bis `5` (nicht verwertbar) bewertet.

### 2.2 Unternehmensnutzen

- **Transparenz & Vergleichbarkeit:** Promptqualität wird objektiv messbar  
- **Gezielte Verbesserung:** Schwächen erkennbar → Schulung möglich  
- **Effizienz:** Weniger Token, bessere Ergebnisse  
- **Compliance:** Unterstützung bei AI-Act / ISO-Normen  
- **Skalierbarkeit:** Einfache Erweiterung auf Abteilungen & Tools  
- **Kulturentwicklung:** Förderung einer reflektierten, lernenden Organisation

---

## 3. Bewertungsmodell nach KSODI: die „KSODI-Skala“

- Bewertung jeder Prompt-Interaktion durch den KSODI-Light-Agenten  
- Jede Dimension von **0–5** bewertet  
- Prompts mit Score >3 werden nicht beantwortet, sondern mit Feedback versehen  
- Optional: Bewertung der **Antwort** nach AI-Act & ISO (Governance-Relevanz)

---

## 4. Zeitbasierte Aggregation

- Scores werden über Zeiträume gesammelt (z. B. Woche/Monat)  
- Ziel: **Prompt-Readyness** & **KI-Readyness** messen  
- Unterschied zu Purview / Promptfoo: Fokus liegt auf **User-Prompt**, nicht nur Systemantwort

---

## 5. Mathematische Herangehensweise (Light-Agent)

### 5.1 Mittelwert je Dimension

Für eine Dimension $K$ bei drei Prompts mit Scores $1$, $2$, $2$ gilt:

\[
\bar{K} = \frac{1 + 2 + 2}{3} = 1{,}67
\]

### 5.2 Durchschnitt über Zeit

Bei 5 Interaktionen mit Kontext-Bewertungen:  
$4{,}1 \,|\, 3{,}5 \,|\, 2{,}2 \,|\, 2{,}1 \,|\, 1{,}6$

\[
\Sigma \bar{K} = \frac{4{,}1 + 3{,}5 + 2{,}2 + 2{,}1 + 1{,}6}{5} = 2{,}7
\]

---

## 6. KSODI-Mapping zu EDEN-Reifegraden

| KSODI Ø-Wert | EDEN-Stufe           | Bedeutung                                                   |
|--------------|----------------------|--------------------------------------------------------------|
| 3–5          | Sumpf                | Impulsive, unstrukturierte Prompts                          |
| 2,5–3        | Wiese                | Erste Strukturansätze                                       |
| 1,7–2,5      | Hain                 | Systematische Zielorientierung                              |
| 0,8–1,6      | Garten               | Reflektierte, komplexe Prompts                              |
| 0–0,8        | Garten mit System    | Kreative KI-Integration in allen KSODI-Dimensionen          |

### 6.1 Beispielauswertung:

```text
Abteilung A befindet sich auf EDEN-Stufe 3 (Hain).  
Stärken: Objektivität (Ø 1,8)  
Potenzial: Struktur (Ø 2,6)  
Empfehlung: Schulungsmaßnahme & Re-Evaluation nach 8 Wochen  