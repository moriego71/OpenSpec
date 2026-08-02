## Context
Actualmente el sistema no posee una funcionalidad para registrar vehículos mediante su patente.

## Goals / Non-Goals
**Goals:**
- Incorporar la capacidad de registrar vehículos.
- Mantener una arquitectura simple.

**Non-Goals:**
- No implementar persistencia.
- No validar el formato de la patente.

## Decisions
- Se utilizará una entidad Vehicle.
- La patente será el identificador principal.
- La lógica de negocio permanecerá desacoplada de la infraestructura.

## Risks / Trade-offs
- **Risk:** La validación de la patente queda fuera del alcance.
  **Mitigation:** Se implementará en un cambio posterior.