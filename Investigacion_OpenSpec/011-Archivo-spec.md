# 012 - Archivo spec.md

## Propósito
Define los requisitos funcionales de una Capability.

## Ubicación

```text
openspec/
└── changes/
    └── <change>/
        └── specs/
            └── <capability>/
                └── spec.md
```

## Estructura
```md

## ADDED Requirements

### Requirement: Registrar vehículo
El sistema SHALL permitir registrar un vehículo mediante su patente.

#### Scenario: Registro exitoso
- **WHEN** el usuario ingresa una patente válida.
- **THEN** el sistema registra el vehículo.
```

## Reglas descubiertas
- Los encabezados (`ADDED`, `Requirement`, `Scenario`) deben permanecer en inglés.
- Cada Requirement debe contener **SHALL** o **MUST**.
- Cada Requirement debe tener al menos un Scenario.
- Los nombres de Requirements y Scenarios pueden escribirse en español.
- El texto descriptivo puede escribirse en español.

## Observaciones
OpenSpec no solo verifica que exista el archivo; también parsea y valida su estructura.