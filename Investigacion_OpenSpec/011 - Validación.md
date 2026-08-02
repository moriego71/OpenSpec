# 011 - Validación

## Comando
```bash
openspec validate <change>


## Qué valida
    Existencia de specs/
    Uso de deltas (ADDED, MODIFIED, REMOVED, RENAMED)
    Que cada Requirement tenga al menos un Scenario
    Estructura del Change

## Observaciones
OpenSpec no genera las specs.
Solo valida que existan y cumplan el esquema esperado.

-----

Creo que ya empezamos a ver con bastante claridad la filosofía de OpenSpec: **es un validador y orquestador del proceso, no un generador de contenido**. Esa es una distinción importante para entender el alcance real de la herramienta.

-----