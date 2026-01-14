# 🏀 Three-Point Inflation in the NBA  
## Where is the limit?

## 1. Projektbeschreibung
In den letzten Jahrzehnten hat sich der Spielstil in der NBA stark verändert.  
Besonders der Drei-Punkte-Wurf hat seit Mitte der 2010er-Jahre massiv an Bedeutung gewonnen.  
Während Teams immer mehr Dreier nehmen, stellt sich die Frage, ob dieses steigende Wurfvolumen langfristig effizient bleibt oder ob ein Sättigungspunkt erreicht wird.

Dieses Projekt untersucht die Entwicklung des Drei-Punkte-Wurfs **historisch**, **statistisch** und **mithilfe von Machine Learning**.

---

## 2. Ziel & Forschungsfrage
**Zentrale Frage:**  
> Wo liegt das Limit der Drei-Punkte-Inflation in der NBA?

Unterfragen:
- Wie hat sich das Drei-Punkte-Volumen seit 1996 entwickelt?
- Gibt es einen Effizienzverlust bei steigendem Wurfvolumen?
- Lässt sich ein struktureller Wendepunkt um 2014/15–2015/16 erkennen?
- Ist der Drei-Punkte-Wurf im Jahr 2026 noch der wichtigste Erfolgsfaktor für Teams?

---

## 3. Datengrundlage
- **Analyseebene:** Team × Saison  
- **Zeitraum:** 1996–2026  
- **Quelle:** Offizielle NBA-Team-Saisonstatistiken  
- **Kennzahlen:**
  - Drei-Punkte-Würfe: 3PA, 3PM, 3P%
  - Weitere Effizienzmaße: FG%, FT%
  - Team-Erfolg: Wins / Winning Percentage

Alle Kennzahlen werden **pro Spiel** berechnet, um die Vergleichbarkeit zwischen Saisons sicherzustellen.

---

## 4. Datenaufbereitung
Die Daten wurden bereinigt und vereinheitlicht:
- Standardisierung der Saisonformate (z. B. 2015/16)
- Vereinheitlichung von Teamnamen (Franchise-Wechsel)
- Berücksichtigung verkürzter Saisons (Lockout, COVID)
- Umgang mit fehlenden Werten in aktuellen Saisons
- Umrechnung aller Kennzahlen auf **Per-Game-Basis**

Das Ergebnis ist eine **bereinigte Master-Tabelle**, die für statistische Analysen und Machine Learning geeignet ist.

---

## 5. Feature Engineering: True 3PT%
Neben der klassischen Drei-Punkte-Quote (3P%) wird eine bereinigte Effizienzkennzahl verwendet:

**True 3PT% (Bayes-adjustiert)**  
- reduziert Verzerrungen durch kleine Stichproben  
- zieht extreme Quoten in Richtung Ligadurchschnitt  
- erlaubt fairere Vergleiche zwischen Teams  

Diese Kennzahl stellt einen zentralen methodischen Mehrwert des Projekts dar.

---

## 6. Methodik

### 6.1 Deskriptive Analyse
- Zeitreihenanalyse von 1996 bis 2026
- Untersuchung der Entwicklung von:
  - 3PA pro Spiel
  - 3P%
  - True 3PT%
- Markierung eines strukturellen Wendepunkts um 2015/16

### 6.2 Statistische Hypothesentests
Vergleich der Saisons:
- **2015/16** (Beginn der modernen Drei-Punkte-Ära)
- **2025/26** (aktuelle NBA)

Tests:
- t-Test auf klassische 3P%
- t-Test auf True 3PT%

Ziel ist die Unterscheidung zwischen einem reinen Volumen-Effekt und einer realen Effizienzveränderung.

### 6.3 Machine Learning
- **Zielvariable:** Wins oder Winning Percentage  
- **Features:**
  - 3PA pro Spiel
  - 3P%
  - True 3PT%
  - FG%
  - FT%
- **Modelle:**
  - Lineare Regression (Baseline)
  - Nichtlineares Modell (z. B. Random Forest)
- Analyse der Modellgüte und Feature Importance

---

## 7. Projektstruktur
Die Projektstruktur beschreibt den Aufbau des GitHub-Repositories und legt fest, wo Daten, Code und Ergebnisse abgelegt werden.  
Sie sorgt für Übersichtlichkeit, Nachvollziehbarkeit und Reproduzierbarkeit der Analyse.

nba-3pt-inflation-limit/
│
├── data/
│ ├── raw/ # Rohdaten (unverändert, Originalquelle)
│ └── processed/ # Bereinigte und vereinheitlichte Master-Tabelle
│
├── notebooks/
│ ├── 01_data_audit.ipynb # Datenüberblick, fehlende Werte, Plausibilitätschecks
│ ├── 02_trend_analysis.ipynb # Deskriptive Analyse und Zeitreihen
│ ├── 03_true_3pt.ipynb # Feature Engineering (True 3PT%)
│ ├── 04_hypothesis_tests.ipynb # Statistische Hypothesentests
│ └── 05_modeling.ipynb # Regressions- und ML-Modelle
│
├── reports/
│ └── figures/ # Exportierte Grafiken für Präsentation und Bericht
│
├── slides/ # Finale Präsentation (PDF / PPTX)
│
├── requirements.txt # Benötigte Python-Bibliotheken
├── .gitignore # Dateien, die nicht versioniert werden
└── README.md # Projektbeschreibung und Anleitung

**Erläuterung:**  
- Rohdaten und bereinigte Daten sind klar getrennt.  
- Die Analyse erfolgt schrittweise in nummerierten Notebooks.  
- Ergebnisse und Präsentation sind vom Code getrennt.  
- Dadurch ist das Projekt übersichtlich und reproduzierbar.



