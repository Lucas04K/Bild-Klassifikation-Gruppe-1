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
