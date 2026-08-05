# 012 - Integración Cursor + OpenSpec

## Objetivo
Automatizar la generación de artifacts de OpenSpec utilizando Cursor.

## Workflow esperado de /opsx:propose

El comando está diseñado para ejecutar automáticamente:

1. openspec new change
2. openspec status
3. proposal.md
4. specs/<capability>/spec.md
5. design.md
6. tasks.md
7. validate
8. Quedar listo para /opsx:apply

## Comportamiento observado

Con la versión actual de Cursor:

Idea
↓
Review Plan
↓
Generación de To-dos
↓
(Espera ejecutar el workflow)

No se generaron automáticamente los artifacts.

## Modos observados

- Ask: conversación.
- Plan: genera un plan de trabajo.
- Build: debería ejecutar el plan (en esta prueba no produjo cambios).

## To-dos

Los To-dos mostrados por Cursor NO son los `tasks.md` de OpenSpec.

Representan el plan interno que Cursor pretende ejecutar.

## Conclusión

El prompt `/opsx:propose` indica que debe:

- crear el change,
- consultar el estado,
- generar todos los artifacts,
- validar el resultado.

En esta prueba sólo llegó hasta la etapa de planificación.

Queda pendiente determinar si la causa es:

- el modelo utilizado,
- permisos de ejecución (Tool Use),
- o un cambio en la integración de Cursor.

## Próximo paso

Investigar la configuración de Cursor (modelo y permisos) hasta lograr que `/opsx:propose` ejecute el workflow completo.