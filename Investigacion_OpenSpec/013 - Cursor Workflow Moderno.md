# 014 - Cursor Workflow Moderno

## Descubrimiento

En la versión actual de Cursor, /opsx:propose no ejecuta inmediatamente.

Genera primero un Review Plan.

Luego muestra:

- Plan
- To-dos
- Botón Build

La ejecución real comienza recién al presionar Build.

## Flujo

/opsx:propose
        ↓
Review Plan
        ↓
Build
        ↓
Ejecución de herramientas
        ↓
Creación de artifacts OpenSpec

## Conclusión

El comportamiento observado no corresponde a una falla de OpenSpec sino al nuevo flujo de ejecución de Cursor.