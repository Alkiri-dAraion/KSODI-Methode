
# KSODI Operator **I** – Informationsgehalt / Impuls (Markdown-Version)

## 🟨 Intuition

Der Operator $I$ misst nicht nur, **dass** Information eingebracht wird,  
sondern **wie gerichtet** und **anschlussfähig** diese im Kontext eingebettet ist.

> Ein Impuls im Sinne von KSODI ist nur dann gültig,  
> wenn er nicht nur *neu* ist, sondern *gerichtet anschlussfähig*.

**Informationsgehalt entsteht durch:**
- Neuheit
- Verdichtung
- Anschlussfähigkeit an bestehende KSODI-Strukturen

**Impuls bedeutet:** eine Initialisierung semantischer Bewegung – nicht bloß Datenmenge.

---

## 🧠 Hauptformel

$$
I(t) = \eta \cdot G(t) + (1 - \eta) \cdot J(t)
$$

mit:
- $\eta \in [0,1]$: Gewichtung zwischen Gehalt und Richtung  
- $G(t)$: Informationsgehalt (semantisch)  
- $J(t)$: Impulsstärke als Richtungswechsel im semantischen Raum

---

## 🔍 Informationsgehalt $G(t)$

$$
G(t) = \frac{N_{\text{neu}} + N_{\text{verdichtet}}}{N_{\text{ges}}}
$$

Dabei gilt:
- $N_{\text{neu}}$: Anzahl neuer Token/Konzepte im Prompt  
- $N_{\text{verdichtet}}$: Anteil präziser, nicht-redundanter Konzepte  
- $N_{\text{ges}}$: Gesamtzahl der Konzepte im Prompt

---

## 🔁 Impulsrichtung $J(t)$

$$
J(t) = 1 - \cos(\theta)
$$

mit:
- $\theta$: Winkel zwischen dem semantischen Kontextvektor und dem Vektor des neuen Impulses  
- $\cos(\theta)$: Ähnlichkeit im semantischen Vektorraum

**Interpretation:**
- $J(t) = 0$: Keine Richtungsänderung (Redundanz)  
- $J(t) = 1$: Maximaler neuer Impuls (orthogonal zum bisherigen Raum)

---

## 🛡 Robuste Version mit Rauschkorrektur

$$
I^*(t) = A(t) \cdot I(t) \cdot \left(1 - \varepsilon \cdot \sigma^2(t)\right)
$$

mit:
- $A(t) \in \{0,1\}$: Messmaske (1 = Impuls messbar, 0 = unbrauchbar)  
- $\sigma^2(t)$: semantische Unschärfe (z. B. Streuung im Embeddingraum)  
- $\varepsilon \in [0,1]$: Gewichtung der Rauschstrafe

---

## ✅ Gesamtdarstellung

$$
\boxed{
I^*(t) = A(t) \cdot \left[ \eta \cdot G(t) + (1 - \eta) \cdot (1 - \cos(\theta)) \right] \cdot \left(1 - \varepsilon \cdot \sigma^2(t) \right)
}
$$

Dies ist die finale, kontextsensitiv gewichtete Formulierung des Impuls-Operators im KSODI-System.

---

**Stand: v1.0 – generiert durch ELKIM im Projekt KSODI_Mathematik_Gesamt**
