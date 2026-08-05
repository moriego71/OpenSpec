# 001 - Instalación e Inicialización

## Comandos
```bash
openspec --version
openspec init


## Resultado de init
Crea:
openspec/
Carpeta de integración con el agente (.cursor, .amazonq, etc.)


## Observaciones
OpenSpec es independiente del agente.
La integración con cada IA se instala por separado.
El proyecto queda preparado para trabajar mediante Changes.


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

# Validación

## proposal.md
- Debe existir.
- Es utilizado por `openspec show`.

## design.md
- Debe existir para desbloquear `tasks`.
- OpenSpec realiza una validación mínima de su estructura.

## spec.md
- Es el artefacto más estrictamente validado.
- Debe contener:
  - ADDED/MODIFIED/REMOVED/RENAMED
  - Requirement
  - SHALL o MUST
  - Scenario

## tasks.md
- Requiere previamente:
  - proposal
  - design
  - specs

  ---

# Los nombres de los artifacts son obligatorios

## Observación
OpenSpec reconoce los artifacts por su nombre exacto.

Ejemplos:
- proposal.md
- design.md
- tasks.md

Si el archivo existe pero tiene otro nombre (por ejemplo `task.md`), `validate` puede indicar que el cambio es válido, pero `status` no marcará el artifact como completado.

## Regla
Respetar exactamente el nombre y la ubicación indicados por `openspec instructions`.