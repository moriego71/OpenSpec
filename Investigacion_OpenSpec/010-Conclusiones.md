# 010 - Conclusiones

## Confirmado

- OpenSpec organiza el trabajo mediante Changes.
- Cada artefacto tiene una responsabilidad específica.
- OpenSpec no escribe Proposal, Design, Specs ni Tasks.
- OpenSpec genera instrucciones enriquecidas para la IA.
- Proposal define las Capabilities.
- Cada Capability genera una Spec.
- Design describe el "cómo".
- Specs describen el "qué".
- Tasks describen el trabajo de implementación.
- Tasks depende de Design y Specs.
- OpenSpec controla las dependencias entre artefactos.

## Pendiente

- Validación (`validate`).
- Archivado (`archive`).
- Sincronización de Specs.
- Flujo completo con un agente (Cursor, Claude, etc.).



Una observación importante

Con los cuatro artefactos vistos, hay una conclusión que no esperaba y me parece una de las más valiosas de la investigación:

OpenSpec no parece ser un generador de especificaciones, sino un orquestador del proceso de especificación.

El CLI no "piensa" ni redacta. Su responsabilidad es:

definir el flujo,
imponer dependencias,
indicar entradas y salidas,
proporcionar instrucciones estructuradas al agente de IA.

La inteligencia para redactar los documentos sigue estando en el agente (Cursor, Claude, GPT, Gemini, etc.), mientras que OpenSpec actúa como el marco que asegura que todos sigan el mismo proceso. Esa distinción conceptual explica muy bien la separación de responsabilidades que veníamos buscando.

-----

- `show` requiere que existan los artefactos del Change (al menos `proposal.md`).
- Crear un Change (`new change`) sólo crea el contenedor, no los documentos.

-----

