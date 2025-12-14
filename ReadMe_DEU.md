- # ToolChain README
  
  Dieses Verzeichnis bündelt die für den Build und die Code-Generierung von SolidDesigner benötigten Tools direkt im Projekt.
  Ziel: keine Abhängigkeiten von der Entwicklerumgebung und reproduzierbare Builds auf CI / neuen Rechnern.
  
  ## Inhalt
  - `Python310/` : Mitgeliefertes Python 3.10 zum Ausführen der Generierungsskripte
    - Beispiel: `Python310/python.exe`
  
  ## Verwendung (CMake)
  In CMake sollte das mitgelieferte Python bevorzugt verwendet werden.
  
  Beispiel:
  - `Python3_EXECUTABLE` auf `.../ToolChain/Python310/python.exe` festlegen
  - vor `find_package(Python3 REQUIRED COMPONENTS Interpreter)` setzen
  
  (Dadurch werden Generierungsschritte wie `CommandsConfig.xml` → `SolidDesignerCommands.h` stabil.)
  
  ## Hinweise
  - Generierte Dateien sollten im Build-Verzeichnis (z. B. `generated/`) abgelegt und nicht ins Repository eingecheckt werden.
  - Wenn unter Windows ein „embeddable“ Python gebündelt wird, können Skripte je nach `python310._pth` und Standardbibliothekspfaden fehlschlagen.
    In diesem Fall die Python-Konfiguration im ToolChain prüfen/anpassen.
