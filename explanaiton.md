## 1. Das Problem: Der „Würfel“ vs. die „Liste“

Stell dir vor, was aus dem **ResNet50 (ohne Top)** herauskommt.  
Es ist kein einzelnes Ergebnis, sondern ein dreidimensionaler Datenblock (ein Tensor).

### Der Output: Ein Block der Größe **7×7×2048**

- **7×7**: Das ist die räumliche Größe (Höhe und Breite).  
  Das Bild wurde von **224×224** auf **7×7** „zusammengestaucht“.

- **2048**: Das ist die Tiefe (Kanäle / Feature Maps).  
  Jede dieser 2048 Schichten sucht nach einem bestimmten Merkmal  
  (z.B. „flauschige Textur“, „rundes Ding“, „roter Fleck“).

### Das Problem

Deine finale Entscheidungsschicht (**Dense**) ist wie eine Excel-Tabelle.  
Sie erwartet eine flache Liste von Zahlen (einen **1D-Vektor**).

Sie kann mit einem **7×7 Gitter** nichts anfangen.  
Sie weiß nicht, wie sie einen 3D-Würfel verarbeiten soll.

---

## 2. Die Lösung: GlobalAveragePooling2D

Diese Schicht ist wie eine Presse.  
Sie nimmt diesen 3D-Block und presst ihn zu einer flachen Liste zusammen,  
indem sie den Durchschnitt berechnet.

### So funktioniert es im Detail:

- Wir haben **2048 verschiedene Karten** (Feature Maps) der Größe **7×7**.

- GlobalAveragePooling nimmt die erste Karte (Karte Nr. 1)  
  und berechnet den Durchschnittswert aller **49 Pixel** (7×7).

➡️ Ergebnis: Eine einzelne Zahl, die sagt:  
„Wie sehr ist Merkmal 1 im Durchschnitt in diesem Bild vorhanden?“

- Das macht sie für Karte Nr. 2, Nr. 3 ... bis Karte Nr. 2048.

### Das Ergebnis

Aus dem **7×7×2048 Block** wird ein Vektor mit **2048 Zahlen**.

Die räumliche Information (7×7) wird weggeworfen,  
aber die Information „Was ist im Bild?“ bleibt erhalten.

---

## 3. Warum es den Fehler löst

Der Fehler **Incompatible Shapes** kam, weil die Dense-Schicht sagte:

> „Ich brauche eine flache Liste von Inputs.  
> Du gibst mir aber 49 Pixel pro Merkmal (7×7).  
> Ich weiß nicht, welches Pixel ich nehmen soll!“

Durch **GlobalAveragePooling2D** entfernst du die Dimensionen Höhe und Breite.

### Shapes vorher vs. nachher

- Vorher:  
  **(Batch, 7, 7, 2048)** → 3 Dimensionen + Batch

- Nachher:  
  **(Batch, 2048)** → 1 Dimension + Batch

Jetzt passen die Formen perfekt:

Die Dense-Schicht bekommt 2048 Werte und kann daraus lernen,  
dass z.B. hohe Werte bei Merkmal 50 und Merkmal 100 „Tasse“ bedeuten.

---

## 4. Warum „Average Pooling“ und nicht „Flatten“?

Man könnte den 7×7×2048 Block auch einfach plattwalzen (**Flatten**).

Dann hätte man:

\[
7×7×2048 = 100.352
\]

Werte.

### Warum ist GlobalAveragePooling besser für ResNet?

#### Weniger Parameter

Bei Flatten müsste deine Dense-Schicht:

\[
100.352 × \text{Anzahl Klassen}
\]

Verbindungen lernen.

Das sind riesige Datenmengen und führt schnell zu **Overfitting**  
(Auswendiglernen).

Bei Pooling sind es nur:

\[
2048 × \text{Anzahl Klassen}
\]

---

#### Positions-Unabhängigkeit

Wenn die Tasse oben links im Bild ist,  
sind andere Pixel im 7×7 Gitter aktiv als wenn sie unten rechts ist.

Flatten würde das verwirren.

GlobalAveragePooling ist das egal:

Der Durchschnittswert von „Tassen-Merkmalen“ bleibt hoch,  
egal ob die Tasse links oder rechts steht.

➡️ Das macht das Modell robuster.

---
