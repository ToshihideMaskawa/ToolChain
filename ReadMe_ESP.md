# README de ToolChain 

Este directorio empaqueta las herramientas necesarias para compilar SolidDesigner y ejecutar la generación de código como parte del proyecto.
Objetivo: evitar dependencias del equipo del desarrollador y garantizar builds reproducibles en CI / máquinas nuevas.

## Contenido
- `Python310/` : Python 3.10 incluido para ejecutar scripts de generación
  - Ejemplo: `Python310/python.exe`

## Uso (CMake)
En CMake, priorice el Python incluido.

Ejemplo:
- fijar `Python3_EXECUTABLE` a `.../ToolChain/Python310/python.exe`
- configurarlo antes de `find_package(Python3 REQUIRED COMPONENTS Interpreter)`

(Esto estabiliza pasos de generación como `CommandsConfig.xml` → `SolidDesignerCommands.h`.)

## Notas
- Se recomienda emitir los archivos generados en el directorio de build (p. ej., `generated/`) y no versionarlos en el repositorio.
- Si incluye Python “embeddable” en Windows, los scripts pueden fallar según la configuración de `python310._pth` y las rutas de la librería estándar.
  En ese caso, revise y ajuste la configuración de Python en ToolChain.
