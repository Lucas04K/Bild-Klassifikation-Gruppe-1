[![Shipping files](https://github.com/neuefische/ds-artificial-neural-networks/actions/workflows/workflow-04.yml/badge.svg?branch=main&event=workflow_dispatch)](https://github.com/neuefische/ds-artificial-neural-networks/actions/workflows/workflow-04.yml)

# Künstliche Neuronale Netze

In diesem Repository werden wir uns mit künstlichen neuronalen Netzen beschäftigen.

## Aufgabe

Bitte arbeitet paarweise alle Notebooks in dieser Reihenfolge durch:

### Tag 1 – Dense Neural Networks (DNN)

Typische Bibliotheken sind PyTorch, TensorFlow & Keras. Wir werden in diesem Kurs TensorFlow & Keras verwenden. Die folgenden Notebooks zeigen euch, wie man DNNs für Regressions- und Klassifikationsprobleme implementiert. Zusätzlich findet ihr Notebooks zum Umgang mit Over- und Underfitting. Und ihr findet ein Notebook darüber, wie man Modelle speichert und lädt.

1. [Regression mit TensorFlow & Keras](day_1/01_Regression_TensorFlow_Keras.ipynb)
2. [Klassifikation mit TensorFlow & Keras](day_1/02_Classification_TensorFlow_Keras.ipynb)

### Tag 2 – Regularisierung & Modell-Persistenz

3. [Over- und Underfitting](day_2/03_Overfit_Underfit.ipynb)
4. [Modelle speichern & laden](day_2/04_Load_saved_Models.ipynb) (optional)

### Tag 3 – Convolutions & Transfer Learning

5. [CNN mit Keras](day_3/cnn/cnn_keras.ipynb)
6. [Vortrainierte Netze & Transfer Learning](day_3/pretrained_transfer_learning/Pretrained_networks+transfer_learning.ipynb)

### Bonus

Normalerweise erstellt niemand sein eigenes DNN von Grund auf in Python. Aber es könnte für manche eine nützliche Übung sein. In dieser Übung werdet ihr mit etwas Unterstützung euer eigenes tiefes neuronales Netz bauen. Dies sollte euch helfen, ein besseres Verständnis dafür zu bekommen, was beim "Trainieren" eines NN vor sich geht.
Daher werdet ihr sogar euren eigenen Backpropagation-Algorithmus berechnen. Beginnt hiermit, wenn ihr an einem der anderen Tage früh fertig seid, ansonsten hebt es euch für später auf, falls ihr interessiert seid.

7. [DNN von Grund auf](bonus/00_DNN_from_scratch.ipynb)


## Einrichtung eurer Umgebung

Bitte stellt sicher, dass ihr das Repo geforkt und eine neue virtuelle Umgebung eingerichtet habt.

Die hinzugefügte **requirements-Datei** enthält alle Bibliotheken und Abhängigkeiten, die wir zur Ausführung dieser Notebooks zu neuronalen Netzen benötigen.

**`Hinweis:`**

- Falls es Fehler bei der Einrichtung der Umgebung gibt, versucht die Versionen der fehlschlagenden Pakete aus der requirements-Datei zu entfernen.
- In manchen Fällen ist es notwendig, den **graphviz**-Compiler für die Transformers-Bibliothek zu installieren.
- Stellt sicher, dass ihr **hdf5** installiert, falls ihr das noch nicht getan habt.

 - Überprüft die **graphviz-Version**, indem ihr folgenden Befehl ausführt:
    ```sh
    dot -V
    ```
    Falls ihr es noch nicht installiert habt, beginnt bei `Schritt_1`. Ansonsten fahrt mit `Schritt_2` fort.


### **`macOS` oder `Linux`** gebt folgende Befehle ein: 

- `Schritt_1:` Aktualisiert Homebrew und installiert **hdf5** und **graphviz** mit folgenden Befehlen:

    ```BASH
     brew update
     brew install graphviz
    ```
    Drückt dann ```Y``` für die Standardinstallation.
    
    Dann können wir mit der Installation von hdf5 fortfahren:
    
    ```BASH
     brew install hdf5
    ```

  Startet euer Terminal neu und überprüft dann die **graphviz-Version**, indem ihr folgenden Befehl ausführt:
     ```sh
    dot -V
    ```
 
- `Schritt_2:` Installiert die virtuelle Umgebung und die benötigten Pakete mit folgenden Befehlen:

  > HINWEIS: für macOS mit **Silicon**-Chips (nicht Intel)
    ```BASH
    pyenv local 3.11.3
    python -m venv .venv
    source .venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements_silicon.txt
    ```
  > HINWEIS: für macOS mit **Intel**-Chips
  ```BASH
    pyenv local 3.11.3
    python -m venv .venv
    source .venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

    
### **`WindowsOS`** gebt folgende Befehle ein:

- `Schritt_1:` Aktualisiert Chocolatey und installiert **hdf5** und **graphviz** mit folgenden Befehlen:

    ```BASH
     choco upgrade chocolatey
     choco install graphviz
    ```
    Drückt dann ```Y``` für die Standardinstallation.
    
    Dann können wir mit der Installation von hdf5 fortfahren:
    
  Besucht diese Website [hdf5 installieren](https://www.hdfgroup.org/download-hdf5/)

  Startet euer Terminal neu und überprüft dann die **graphviz-Version**, indem ihr folgenden Befehl ausführt:
     ```sh
    dot -V
    ```
     

- `Schritt_2:` Installiert die virtuelle Umgebung und die benötigten Pakete mit folgenden Befehlen.

   Für `PowerShell` CLI:

    ```PowerShell
    pyenv local 3.11.3
    python -m venv .venv
    .venv\Scripts\Activate.ps1
    python -m pip install --upgrade pip
    pip install -r requirements.txt
    ```

    Für `Git-bash` CLI:
  
    ```BASH
    pyenv local 3.11.3
    python -m venv .venv
    source .venv/Scripts/activate
    python -m pip install --upgrade pip
    pip install -r requirements.txt
    ```

## Daten

Der Datensatz für das Notebook ist im Ordner `data.zip` gespeichert. Um den Datenordner direkt im Terminal zu entpacken, führt aus:
- Tabellarische Datensätze, die in den Dense-Network-Notebooks verwendet werden, befinden sich in `data/` und umfassen:
  - `boston.csv`
  - `titanic.csv`
  - `vehicle_emissions.csv`

  ```sh
  unzip data.zip
  ```
- Das Transfer-Learning-Notebook hat sein eigenes Archiv unter `day_3/pretrained_transfer_learning/data.zip`; entpackt es in diesem Ordner, bevor ihr das Notebook ausführt.
