# README ToolChain 

Ce répertoire regroupe les outils nécessaires à la compilation et à la génération de code de SolidDesigner, empaquetés directement dans le projet.
Objectif : éviter les dépendances à l’environnement de développement et garantir une build reproductible sur CI / nouvelles machines.

## Contenu
- `Python310/` : Python 3.10 (version embarquée) pour exécuter les scripts de génération
  - Exemple : `Python310/python.exe`

## Utilisation (CMake)
Dans CMake, privilégiez l’utilisation du Python embarqué.

Exemple :
- fixer `Python3_EXECUTABLE` sur `.../ToolChain/Python310/python.exe`
- le définir avant `find_package(Python3 REQUIRED COMPONENTS Interpreter)`

(Cela stabilise les étapes de génération comme `CommandsConfig.xml` → `SolidDesignerCommands.h`.)

## Remarques
- Il est recommandé de générer les fichiers dans le répertoire de build (ex. `generated/`) et de ne pas les versionner dans le dépôt.
- Si vous embarquez Python “embeddable” sous Windows, les scripts peuvent échouer selon la configuration de `python310._pth` et des chemins de la bibliothèque standard.
  Dans ce cas, vérifiez/ajustez la configuration Python côté ToolChain.
