# 009 - Arquitectura Conceptual

## Flujo

```text
Idea
   │
   ▼
Proposal
   │
   ├──────────────┐
   ▼              ▼
Design         Specs
   └──────┬───────┘
          ▼
        Tasks
          ▼
     Implementación
```

## Responsabilidades

### OpenSpec
- Gestiona Changes.
- Gestiona el flujo.
- Controla dependencias.
- Genera instrucciones para la IA.

### IA
- Redacta los artefactos.
- Implementa el código.
- Ejecuta las tareas.

### Ingeniero
- Define el problema.
- Revisa los artefactos.
- Aprueba la implementación.