## Recorrido Completo de un Proyecto

Idea de investigación
        ↓
Visión de la plataforma
        ↓
Modelo conceptual
        ↓
Arquitectura
        ↓
AGENTS (reglas permanentes)
        ↓
Backlog
        ↓
OpenSpec
    ├── Specification
    ├── Design
    ├── Tasks
    └── Apply
        ↓
Código

OpenSpec resuelve muy bien el "cómo desarrollar cada incremento", mientras que todo el trabajo anterior (visión, arquitectura, AGENTS y modelo conceptual) resuelve el "qué plataforma estamos construyendo y bajo qué principios". Lejos de competir, ambas partes se complementan y hacen que cada iteración tenga un contexto mucho más sólido.

---

# Guia de Trabajo para aprender OpenSpec

## Paso 1 — Comprender OpenSpec

Objetivo:
Entender exactamente qué artefactos produce.

No escribir nada todavía.

## Paso 2 — Diseñar nuestra metodología
Responder preguntas como:

¿Qué contexto recibe?
¿Qué archivos necesita?
¿Qué nivel de detalle esperamos?
¿Cómo organizaremos las especificaciones?
¿Qué formato tendrán las User Stories?


## Paso 3 — Diseñar el Prompt Maestro

Éste me parece el punto más importante.

En lugar de improvisar un prompt cada vez, construiremos el prompt oficial del proyecto.

Algo como:
Contexto:
- AGENTS.md
- ModeloConceptual.md

Entrada:
- Una Feature del Backlog

Salida esperada:
- User Stories
- Separación Backend/Frontend cuando corresponda
- Acceptance Criteria
- Domain Rules
- OpenSpec
- Dependencias
- Supuestos

## Paso 4 — Ejecutar un experimento piloto

Con:

FE01.01 Crear Campaña Experimental

Sólo esa.

Nada más.

## Paso 5 — Auditar el resultado

Y acá está la parte más importante.
No aceptaremos lo que produzca OpenSpec automáticamente.
Lo vamos a revisar preguntándonos:

¿Las US están bien separadas?
¿Hay redundancias?
¿Inventó cosas?
¿Respeta el modelo conceptual?
¿Respeta AGENTS?
¿Falta alguna US?
¿Hay demasiadas?
¿Se entiende?

## Paso 6 — Congelar la metodología

Cuando estemos conformes, diremos:
Ésta es la metodología oficial del proyecto para generar User Stories mediante OpenSpec.

Y desde ese momento, todo el backlog se procesará exactamente igual.
---

