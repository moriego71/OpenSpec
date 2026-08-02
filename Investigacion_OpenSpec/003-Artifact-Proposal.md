# 003 - Artifact: Proposal
## Propósito
Primer artefacto del Change.
Describe el problema y el alcance funcional.

## Objetivo
Explicar **por qué** debe realizarse el cambio.

## Secciones
- Why
- What Changes
- Capabilities
- Impact

## No incluye
- Diseño
- Arquitectura
- Implementación

## Capabilities
- Define las capacidades nuevas o modificadas.
- Cada nueva Capability originará:
```text
openspec/specs/<capability>/spec.md
```

## Desbloquea
- Design
- Specs

## Observaciones
OpenSpec no genera el Proposal.
El agente de IA (o el ingeniero) escribe el contenido.
OpenSpec valida su existencia y lo utiliza como entrada para Design y Specs.
Las Capabilities definen qué especificaciones deberán crearse.