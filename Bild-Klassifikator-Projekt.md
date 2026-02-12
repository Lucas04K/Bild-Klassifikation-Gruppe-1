# Projekt: Bild-Klassifikator für eigene Objekte

## Überblick

In diesem Projekt baust du einen funktionierenden Bild-Klassifikator, der Objekte aus deiner Umgebung erkennen kann. Du wirst den gesamten Machine Learning Workflow durchlaufen: von der Datensammlung über das Training bis zur Evaluation.

**Zeitaufwand:** 1 Tag  
**Schwierigkeitsgrad:** Mittel  
**Ziel:** Ein trainiertes Modell, das 3-5 selbstgewählte Objektkategorien mit >70% Genauigkeit klassifiziert

## Lernziele

- Verstehen des kompletten ML-Workflows von Daten bis Modell
- Praktische Erfahrung mit Datensammlung und -qualität
- Anwendung von Transfer Learning
- Evaluation und Fehleranalyse von Klassifikationsmodellen
- Umgang mit kleinen Datasets durch Data Augmentation

## Aufgabenstellung

### Phase 1: Datensammlung

**Aufgabe:**
1. Wähle 3-5 Objektkategorien aus deiner Umgebung (z.B. Kaffeetasse, Buch, Pflanze, Brille, Smartphone)
   - Die Objekte sollten visuell unterscheidbar sein
   - Wähle Objekte, die du mehrfach fotografieren kannst

2. Erstelle pro Kategorie 50-100 Fotos mit unterschiedlichen:
   - Winkeln (von oben, von der Seite, schräg)
   - Beleuchtungen (Tageslicht, Kunstlicht, Schatten)
   - Hintergründen (Schreibtisch, Boden, vor der Wand)
   - Abständen (nah, mittel, weiter weg)

3. Organisiere die Bilder in folgender Ordnerstruktur:
   ```
   data/
   ├── train/
   │   ├── klasse1/
   │   ├── klasse2/
   │   └── klasse3/
   ├── validation/
   │   ├── klasse1/
   │   ├── klasse2/
   │   └── klasse3/
   └── test/
       ├── klasse1/
       ├── klasse2/
       └── klasse3/
   ```

**Hinweise:**
- Nutze dein Smartphone oder die Laptop-Webcam
- Achte auf Varianz in den Trainingsdaten
- Split: ca. 70% Training, 15% Validation, 15% Test

### Phase 2: Datenverarbeitung & Exploration 

**Aufgabe:**
1. Lade die Bilder und verschaffe dir einen Überblick:
   - Wie viele Bilder pro Klasse?
   - Zeige Beispielbilder aus jeder Kategorie
   - Prüfe Bildgrößen und -formate

2. Implementiere Preprocessing:
   - Skaliere alle Bilder auf einheitliche Größe (z.B. 224x224)
   - Normalisiere Pixelwerte (z.B. auf Bereich [0,1])

3. Richte Data Augmentation ein:
   - Rotation (±15-20°)
   - Horizontales Flipping
   - Zoom (±10-20%)
   - Helligkeitsanpassungen

**Technische Hinweise:**
- Nutze `ImageDataGenerator` (Keras)
- Augmentation nur auf Trainingsdaten anwenden!

### Phase 3: Modelltraining mit Transfer Learning

**Aufgabe:**
1. Wähle ein vortrainiertes Modell als Basis:
   - ResNet50
   - MobileNetV2
   - EfficientNetB0

2. Implementiere Feature Extraction:
   - Lade vortrainiertes Modell (ImageNet weights)
   - Friere die unteren Layer ein
   - Füge eigene Classification Layer hinzu

3. Trainiere das Modell:
   - Starte mit wenigen Epochen (5-10)
   - Beobachte Training/Validation Loss
   - Nutze eventuell Early Stopping

4. Optional: Fine-Tuning
   - Taue obere Layer des Base-Models auf
   - Trainiere mit niedriger Learning Rate weiter

**Hinweise:**
- Dokumentiere deine Hyperparameter (Learning Rate, Batch Size, Epochs)
- Plotte Training History (Loss & Accuracy)
- Achte auf Overfitting (Train vs. Validation Performance)

### Phase 4: Evaluation

**Aufgabe:**
1. Evaluiere das Modell auf dem Test-Set:
   - Berechne Accuracy
   - Erstelle eine Confusion Matrix
   - Berechne Precision, Recall, F1-Score pro Klasse

2. Fehleranalyse:
   - Welche Bilder werden falsch klassifiziert?
   - Zeige die "schwierigsten" Beispiele
   - Gibt es Muster in den Fehlern?

3. Interpretiere die Ergebnisse:
   - Wo ist das Modell stark/schwach?
   - Was könnte man verbessern?
   - Wie würde mehr Daten helfen?

### Phase 5: Testing mit neuen Bildern 

**Aufgabe:**
1. Nimm 5-10 komplett neue Fotos von deinen Objekten auf
   - Andere Beleuchtung als beim Training
   - Andere Hintergründe
   - Andere Winkel

2. Teste das Modell auf diesen Bildern:
   - Lade die Bilder
   - Führe Predictions durch
   - Zeige Predictions mit Confidence Scores

3. Reflektiere:
   - Wie gut generalisiert das Modell?
   - Wo sind die Grenzen?

## Tipps für den Erfolg

### Datensammlung
- Qualität > Quantität: Lieber weniger, aber vielfältigere Bilder
- Vermeide zu ähnliche Bilder (nicht 100x dasselbe Objekt aus leicht anderem Winkel)
- Denke an "Edge Cases": Was könnte das Modell verwechseln?

### Debugging
- Wenn Accuracy sehr niedrig: Prüfe Datenverarbeitung und Labels
- Wenn starkes Overfitting: Mehr Augmentation, weniger trainierbare Parameter
- Wenn keine Verbesserung: Learning Rate anpassen

## Zusätzliche Herausforderungen (Optional)

Wenn du schneller fertig bist oder tiefer einsteigen möchtest:

1. **Multi-Objekt-Szenen**: Teste das Modell mit Bildern, die mehrere Objekte gleichzeitig zeigen
2. **Model Comparison**: Vergleiche verschiedene Base-Models (ResNet vs. MobileNet vs. EfficientNet)
4. **Schwierige Negative Examples**: Füge eine "Hintergrund"-Klasse mit beliebigen Objekten hinzu
5. **Deployment**: Speichere das Modell und lade es in einer separaten Anwendung

## Ressourcen

- Keras Transfer Learning Guide: https://keras.io/guides/transfer_learning/
- ImageDataGenerator Dokumentation: https://keras.io/api/preprocessing/image/
- Scikit-learn Metrics: https://scikit-learn.org/stable/modules/model_evaluation.html

---

**Viel Erfolg beim Projekt!**
