# Conceptos aprendidos del curso de Álvaro Moya

## Propósito

Este documento constituye la fuente de verdad del aprendizaje realizado durante el curso de Specification-Driven Development.

Resume exclusivamente las conclusiones consolidadas y acordadas, descartando hipótesis ya corregidas o superadas.

Todo análisis futuro deberá considerarlo como contexto previo antes de incorporar nuevos conceptos.



### Desarrollo Guiado por Especificaciones

Las decisiones de implementación no dependerán de criterios individuales de los desarrolladores.

Toda funcionalidad deberá implementarse a partir de especificaciones previamente definidas y validadas, garantizando un proceso de desarrollo sistemático, reproducible y verificable.


### Nuestra hipótesis de flujo de trabajo
#### Debemos corroborar a medida que avancemos en el curso

                 CONTRATO
                     │
                     │
                     ▼
         Feature (Backlog Refinado)
                     │
                     │
             (Contexto del proyecto)
                     │
      ┌──────────────┴──────────────┐
      │                             │
Modelo Conceptual            Arquitectura
      │                             │
      └──────────────┬──────────────┘
                     │
                     ▼
                OpenSpec
                     │
                     ▼
     User Story completamente especificada
     ├── Objetivo
     ├── Alcance
     ├── RF
     ├── RNF
     ├── Casos límite
     ├── Criterios de aceptación
     ├── Tests
     ├── Restricciones
     └── ...
                     │
                     ▼
                    IA
                     │
                     ▼
                  Código


Posiblemente:

Feature
      │
      ▼
US básica
      │
      ▼
OpenSpec
      │
      ▼
US completamente especificada


# AGENTS acaba de redefinirse

Ésta creo que es la conclusión más importante.
Hace unas horas discutíamos:
¿Qué debería contener AGENTS?
Ahora Álvaro prácticamente nos respondió.
AGENTS debería contener:
- Cómo trabajamos.
No:
Qué hace el sistema.
Eso pertenece a:
- Modelo Conceptual
- Arquitectura
- Backlog

Creo que acabamos de encontrar la frontera exacta entre AGENTS y el resto de la documentación.


# Mi conclusión más fuerte (GPT)

Creo que ya podemos definir, con bastante confianza, el rol de cada documento del proyecto:

Documento	Propósito
ModeloConceptual.md	Define qué es el sistema: conceptos del dominio, relaciones y lenguaje común.
Arquitectura.md	Define cómo está organizado el sistema: principios, decisiones de diseño y restricciones arquitectónicas.
Backlog.md	Define qué capacidades debe implementar el sistema: épicas, features y, más adelante, User Stories.
AGENTS.md	Define cómo se trabaja en el proyecto: metodología, convenciones, flujo de desarrollo, uso de herramientas y acuerdos del equipo.






# Apuntes SDD / OpenSpec

## Conclusiones obtenidas

### OpenSpec no es un generador de código

OpenSpec no implementa funcionalidades directamente.

Su responsabilidad consiste en transformar una necesidad funcional (Feature o User Story inicial) en una **especificación exhaustiva y verificable**, que posteriormente será utilizada por herramientas de generación de código (Cursor, Claude Code, Copilot, Gemini, etc.).

Su función pertenece al ámbito de la **Ingeniería de Requisitos**, no al de la implementación.

---

## Separación de responsabilidades

El proceso completo parece dividirse en dos grandes etapas:

```
Definir qué construir
        │
        ▼
      OpenSpec
        │
        ▼
Especificación completa
        │
        ▼
 Generador de código (IA)
        │
        ▼
     Implementación
```

Esto desacopla completamente la definición del producto de la tecnología utilizada para implementarlo.

---

## La especificación es la fuente de verdad

El código deja de ser la referencia principal del sistema.

La fuente de verdad pasa a ser la especificación generada por OpenSpec.

El código constituye únicamente una implementación de dicha especificación.

---

## La especificación permanece viva

A diferencia de una Historia de Usuario tradicional, una especificación no desaparece una vez implementada.

Luego de finalizar una funcionalidad, OpenSpec archiva la especificación para incorporarla al conocimiento permanente del producto.

Las nuevas funcionalidades se diseñan consultando primero todas las especificaciones existentes.

---

## Evolución incremental mediante "Delta"

Cuando una nueva funcionalidad modifica otra ya existente, OpenSpec no reemplaza la especificación anterior.

Genera una nueva especificación que representa únicamente la evolución (Delta) sobre la funcionalidad existente.

Esto permite mantener la trazabilidad histórica de la evolución del sistema.

---

## El contexto es el principal insumo de OpenSpec

La calidad de las especificaciones depende directamente de la calidad del contexto disponible.

Entre los elementos que conforman dicho contexto se encuentran:

- Modelo conceptual del dominio.
- Arquitectura del sistema.
- Backlog del producto.
- Modelo de datos.
- APIs disponibles.
- Convenciones de desarrollo.
- Flujo de trabajo del equipo.
- Estrategia de testing.
- Convenciones de documentación.
- Acuerdos metodológicos.

Cuanto más completo y consistente sea este contexto, mayor será la calidad de las especificaciones generadas.

---

## Rol de AGENTS.md

AGENTS no describe el dominio del problema.

Su responsabilidad consiste en documentar **cómo trabaja el equipo**.

Debe contener, entre otros aspectos:

- metodología de trabajo;
- convenciones de desarrollo;
- flujo de trabajo;
- estrategia de testing;
- criterios de documentación;
- estructura de commits;
- acuerdos del equipo;
- utilización de herramientas.

En cambio, la definición funcional del sistema pertenece a documentos como:

- ModeloConceptual.md
- Arquitectura.md
- Backlog.md

---

## Ciclo de vida propuesto del desarrollo

```
Modelo Conceptual
        │
        ▼
Arquitectura
        │
        ▼
Backlog
        │
        ▼
Feature seleccionada
        │
        ▼
OpenSpec
        │
        ▼
Especificación detallada
        │
        ▼
Implementación (IA)
        │
        ▼
Validación
        │
        ▼
Archivo permanente de la Especificación
```

Las especificaciones archivadas pasan a formar parte del conocimiento del producto y serán reutilizadas durante la generación de futuras funcionalidades.

---

## Hipótesis de trabajo (pendiente de confirmar)

Se plantea la siguiente hipótesis sobre el funcionamiento interno de OpenSpec:

```
Contrato + Feature
        │
        ▼
     OpenSpec
        │
        ▼
User Story completamente especificada
```

Dicha especificación incluiría:

- objetivos;
- requisitos funcionales;
- requisitos no funcionales;
- restricciones;
- criterios de aceptación;
- casos límite;
- estrategia de testing;
- validaciones;
- consideraciones de seguridad;
- rendimiento;
- trazabilidad.

Esta hipótesis deberá confirmarse durante el resto del curso.



# Precisiones de cómo funciona OpenSpec

## Lo que muestra la estructura

.openspec/

├── specs/
│     └── <domain>/
│            spec.md
│
├── changes/
│     └── <change-name>/
│            proposal.md
│            design.md
│            tasks.md
│            specs/
│                 └── <domain>/
│                        spec.md
│
└── config.yaml

### NO trabaja directamente sobre el Backlog
Feature (Backlog)
        │
        ▼
proposal.md

Es decir, el Backlog dispara un cambio, pero OpenSpec trabaja sobre el concepto de Change.


### Un Change produce varios artefactos
No genera solamente una Spec.
Genera al menos cuatro documentos:

#### proposal.md
¿Por qué existe el cambio?
¿Qué problema resuelve?

#### design.md
¿Cómo se implementará?
Decisiones de diseño.
Impacto.

#### tasks.md
Lista de tareas para implementar.

#### spec.md
La especificación funcional propiamente dicha.
Ésta termina siendo la fuente de verdad.


### La carpeta changes/
es temporal.
Representa trabajo en curso.
Cuando el cambio termina...
↓
OpenSpec mueve

spec.md
a
specs/

Eso significa que:

changes/
es el equivalente a una Pull Request.

Mientras que
specs/
es el producto terminado.


### La carpeta specs/
es exactamente la memoria permanente del producto.
Y confirma lo que intuíamos.
Cuando hacemos una nueva funcionalidad...

OpenSpec primero hace:
leer specs/

Nunca empieza desde cero.


### Concepto de Delta
Durante el cambio...

changes/
      specs/
             dominio/
                     spec.md

No contiene toda la funcionalidad.
Sólo contiene
qué cambia respecto a la Spec oficial.
Cuando termina...
fusiona.


### ya podemos mapear nuestro proyecto
Creo que sería algo así.

docs/
    ModeloConceptual.md
    Arquitectura.md
    Backlog.md

.openspec/
    config.yaml

specs/

Campañas/

Experimentos/

Configuraciones/

Infraestructura/

...

changes/

crear-campaña/
    proposal.md
    design.md
    tasks.md

specs/

Campañas/
    spec.md


### diferencia entre nuestros documentos y OpenSpec.

Nosotros tenemos:

Modelo Conceptual
↓
Arquitectura
↓
Backlog

OpenSpec agrega otra capa.

Modelo Conceptual
↓
Arquitectura
↓
Backlog
↓
OpenSpec
↓
Proposal
↓
Design
↓
Tasks
↓
Spec
↓
Código


## ¿Qué le vamos a pasar a OpenSpec?
Una Feature
+
Todo el contexto del proyecto.

Y ese contexto está compuesto por:

Modelo Conceptual
Arquitectura
Backlog
AGENTS
Specs existentes

OpenSpec toma eso y genera un Change completamente especificado.





# Empieza a verse claramente cuál es su ciclo de vida
# Apuntes SDD / OpenSpec

## Ciclo de desarrollo de OpenSpec

OpenSpec organiza el desarrollo de una funcionalidad mediante un flujo de trabajo completamente definido, donde la especificación constituye el elemento central del proceso.

El ciclo general es el siguiente:

```text
User Story
      │
      ▼
new / ff
      │
      ▼
Proposal Artifacts
      │
      ▼
apply
      │
      ├── Documentación
      ├── Tests
      ├── Código
      └── Actualización de la propuesta
      │
      ▼
verify
      │
      ▼
archive
      │
      ▼
Feature Ready
```

---

## 1. User Story

El proceso comienza con una necesidad funcional.

No necesariamente debe ser una User Story completamente detallada; puede ser una Feature del backlog o una descripción funcional inicial.

---

## 2. new

El comando **new** inicia un nuevo cambio (Change).
A partir de ese momento OpenSpec crea una carpeta dentro de:

```.openspec/changes/<nombre-del-cambio>/
```

## 3. Proposal Artifacts

OpenSpec genera automáticamente los artefactos necesarios para especificar completamente la funcionalidad.

Entre ellos:
- proposal.md
- design.md
- tasks.md
- spec.md

Cada documento posee una responsabilidad específica.

### proposal.md
Describe:
- qué problema se intenta resolver;
- cuál es el objetivo del cambio;
- alcance funcional.

### design.md
Describe:
- decisiones de diseño;
- impacto sobre el sistema;
- arquitectura involucrada;
- dependencias.

### tasks.md
Contiene el plan de implementación.

Se descompone en tareas pequeñas que OpenSpec irá completando automáticamente durante el desarrollo.

Cada tarea se marca como realizada a medida que se implementa.

### spec.md
Representa la especificación funcional.

Describe el comportamiento esperado del sistema y constituye la futura fuente de verdad del producto.


## 4. apply

Una vez aprobada la propuesta comienza la implementación.

OpenSpec desarrolla progresivamente:
- documentación;
- tests;
- código;
- actualización de la propuesta.

Durante este proceso mantiene actualizado automáticamente el archivo tasks.md.


## 5. verify

Al finalizar, OpenSpec realiza una verificación automática.

Evalúa principalmente:
- coherencia entre la solicitud inicial y la implementación;
- completitud de todas las tareas;
- cumplimiento de las convenciones definidas por el proyecto;
- consistencia técnica.

Como resultado obtiene una evaluación del cambio antes de incorporarlo definitivamente al producto.


## 6. archive

Si la verificación resulta satisfactoria, OpenSpec archiva la especificación.

La carpeta temporal del cambio deja de representar trabajo en curso.

La especificación pasa a formar parte del conocimiento permanente del sistema.


## 7. Feature Ready

La funcionalidad queda oficialmente incorporada al producto.

A partir de este momento OpenSpec la considera parte del sistema y la utilizará como contexto para generar futuras especificaciones.

Las próximas funcionalidades consultarán automáticamente esta especificación para:

- evitar duplicaciones;
- detectar modificaciones de comportamiento;
- generar deltas sobre funcionalidades existentes;
- mantener la coherencia global del producto.


# Conclusiones

OpenSpec no es un generador de código.

Es un sistema de gestión del conocimiento funcional del producto.

Su principal responsabilidad consiste en:

- transformar una necesidad funcional en una especificación completa;
- guiar la implementación;
- validar la coherencia del resultado;
- preservar el conocimiento generado para futuras evoluciones.

El código es únicamente una consecuencia de la especificación.

La especificación permanece como la verdadera fuente de verdad del sistema.

#### OpenSpec considera que implementar una funcionalidad implica mucho más que programar: incluye verificarla, documentarla y mantener sincronizada su especificación. Esta filosofía es una de las claves del enfoque Specification-Driven Development.


# 20260729 Análisis del nuevo material
## Concepto 1 — openspec init genera integración específica para cada agente
Qué explica Álvaro
Al ejecutar:

openspec init

OpenSpec pregunta con qué agentes de IA vas a trabajar (Cursor, Claude Code, etc.).
Luego genera automáticamente la estructura necesaria para cada uno.

## Concepto 2 — Los comandos (apply, explore, etc.) son Markdown (skills)

Este para mí es uno de los conceptos más importantes.

#### Los comandos no son código.

Son archivos Markdown.
Por ejemplo:
        opsx-apply.md
        opsx-explore.md
        opsx-propose.md
Es decir:
los comandos pueden personalizarse.

Qué significa realmente?
Esto cambia bastante la visión.

Nosotros pensábamos:

"/opsx:apply es un comando interno."

En realidad no. Es una skill !!!
Una especificación.

Eso significa que el flujo OpenSpec es configurable.


## Concepto 3 — Separar el contexto técnico del agente
Este me parece EL concepto importante del bloque.
Álvaro propone algo como:

ai-specs/

    agents/

    commands/

    standards/

    docs/

    prompts/

    ...

Todo independiente del agente.
Luego Cursor, Claude, Gemini...
simplemente apuntan allí.

### Comparación con nuestro laboratorio
Acá encontré una coincidencia enorme.
Nosotros ayer hicimos exactamente esto cuando decidimos mover todas las reglas permanentes a:
AGENTS.md
Sin saberlo, estábamos siguiendo la misma idea.
La diferencia es que Álvaro lo lleva un paso más allá.
No centraliza en un archivo.
Centraliza en toda una carpeta de conocimiento.


## Concepto 4 — Configuración mediante config.yaml
OpenSpec prácticamente no guarda contexto.
Lo referencia.
Ejemplo:

context:

   arquitectura.md

   backend-standards.md

   testing.md

   ...

No copia, Apunta!!!
Consecuencia:
        El contexto es modular.
Esto me gustó muchísimo.
Porque responde una pregunta que nos hacíamos ayer.

#### ¿Cómo reducir tokens?

Respuesta:
No metiendo todo en AGENTS.
Sino dividiendo el conocimiento.


## Concepto 5 — Dividir el conocimiento en archivos pequeños
Álvaro insiste mucho en esto.
No hacer:
        AGENTS.md
de 4000 líneas.

Sino:
        backend.md
        testing.md
        api.md
        arquitectura.md
        frontend.md
        DDD.md

Y que cada tarea cargue únicamente lo necesario.

Comparación con nuestro laboratorio:
Acá sí aparece una diferencia con lo que hicimos.
Nosotros venimos haciendo crecer mucho AGENTS.
Hoy todavía está perfecto.
Pero ya veo que, cuando el proyecto crezca, va a empezar a transformarse en un cuello de botella.

Mi conclusión
No cambiaría nada hoy.
Pero sí abriría un ítem de backlog.

## RESUMEN 20260729 Análisis del nuevo material
1- openspec init genera integración para distintos agentes.
2- Los comandos OpenSpec son skills escritas en Markdown.
3- El contexto técnico debe ser independiente del agente utilizado.
4- config.yaml referencia documentación; no la reemplaza.
5- El conocimiento debe organizarse de forma modular para minimizar el contexto consumido por la IA.


# NOTA IMPORTANTE: >
> **Decisión para el laboratorio**>
> Una vez finalizado el curso de Specification-Driven Development, se realizará una refactorización del contexto técnico del laboratorio.
>
> Dado que `AGENTS.md` ya supera las 1.500 líneas, se considera que ha alcanzado un tamaño que justifica su modularización.
>
> El objetivo será reorganizar el conocimiento en documentos especializados (arquitectura, estándares, convenciones, dominio, testing, etc.), siguiendo los principios presentados en el curso y manteniendo la compatibilidad con OpenSpec y los distintos agentes de IA.
> ËSTO OPTIMIZA AL AGENTE YA QUE LEERÁ SOLO LO NECESARIO Y NOS AHORRA MUCHOS TOKENS DE LECTURA INNECESARIA!!!
>
> Esta refactorización se realizará antes de continuar con nuevas implementaciones del laboratorio.


## Concepto 6 — AI Specs como conocimiento organizacional
Qué explicaLa carpeta AI Specs representa el conocimiento permanente del equipo:
        estándares de backend;
        estándares de testing;
        convenciones;
        arquitectura;
        buenas prácticas.
No contiene tareas concretas.
Contiene conocimiento reutilizable.

Comparación con nuestro laboratorio
Esto confirma la decisión que tomamos de separar:
        contexto permanente;
        tareas temporales.

La diferencia es que Álvaro propone que ese contexto esté modularizado desde el principio.


## Concepto 7 — OpenSpec debe adaptarse al proceso del equipo
Adaptá OpenSpec a tu proceso.
Ejemplos:
        crear automáticamente la branch;
        generar el commit;
        lanzar la PR;
        ejecutar CodeRabbit;
        ejecutar Cursor Review.
Todo eso es personalización.


##  Concepto 8 — Comenzar por el flujo mínimo
Álvaro insiste varias veces:
No intenten automatizar todo desde el primer día.
Primero:

Historia
↓
Artefactos
↓
Implementación
↓
Archive

Después...

recién ahí...
ir agregando automatizaciones.

Comparación con nuestro laboratorio

Acá me dio mucha tranquilidad.
Nosotros justamente estamos haciendo eso.

Tres Apply.

Nada más.

Sin:

Jira
PR
Playwright
MCP
CodeRabbit
CI/CD

Estamos exactamente en el camino que recomienda.


## Concepto 9 — OpenSpec permite automatizar todo el ciclo de desarrollo
Este es más una capacidad.
No una obligación.

Puede automatizar:

branch
commit
PR
pruebas
curl
Playwright
documentación
archive

Pero...
eso depende del proceso del equipo.

Para SmartParking
No haría absolutamente nada.
Es muchísimo más de lo que necesitamos.
Lo que NO agregaría
No agregaría cosas como:

CodeRabbit
Jira
Curl
Playwright
MCP
Postman

Porque son ejemplos.
No principios.

Y el objetivo de Conceptos_Curso_Alvaro.md es consolidar principios metodológicos, no inventariar herramientas.
Lo que sí empezaría a notar
Empieza a aparecer una filosofía muy clara del curso.

Specification-Driven Development (SDD) no propone un proceso rígido de desarrollo. Propone una metodología extensible que cada equipo debe adaptar a su propio flujo de trabajo, automatizando progresivamente aquellas actividades que aporten valor. OpenSpec es una herramienta que facilita la implementación de esa metodología mediante la gestión de especificaciones, artefactos y su integración con agentes de IA.


[SDD] La metodología debe adaptarse al proceso del equipo.
[OpenSpec] Los comandos son skills en Markdown y el contexto puede modularizarse mediante config.yaml.
[Álvaro] En su empresa, el flujo incluye creación automática de ramas, ejecución de pruebas, CodeRabbit, PR y revisiones automáticas.

***********

## 1. [SDD] La especificación es la fuente para construir y verificar
Este me parece el principio metodológico más importante del bloque.

Una especificación suficientemente precisa permite derivar automáticamente tanto la implementación como su verificación.


## 2. [OpenSpec] Los artefactos enriquecidos habilitan automatizaciones

OpenSpec (o mejor dicho, el flujo construido alrededor de OpenSpec) trabaja con artefactos mucho más ricos que una User Story tradicional.

Gracias a eso, la IA puede generar:

implementación;
pruebas;
documentación;
reportes.

No porque OpenSpec tenga un módulo mágico de testing, sino porque dispone de suficiente contexto.


## 3. [Álvaro] QA automatizado por IA
Acá ya estamos en la práctica de su empresa.
Ellos decidieron que el flujo incluya:

pruebas unitarias;
pruebas end-to-end;
llamadas a APIs;
screenshots;
reportes.

Eso no forma parte de SDD.
Tampoco de OpenSpec.
Es una decisión del equipo.

No la incorporaría como concepto general.


## 4. [SDD] La especificación también define el comportamiento esperado del testing
Normalmente pensamos:

        Especificación
           ↓
        Código


Álvaro propone:

        Especificación
           ↓
        Código

        Especificación
           ↓
        Testing

Es decir:
el testing nace de la especificación.
No del código.


## 5. [Álvaro] El objetivo no es reemplazar QA
Fijate que nunca dice:
"No hacen falta testers."

Dice algo mucho más interesante.
        La IA hace el trabajo repetitivo.
        El ingeniero analiza el reporte.

Eso cambia completamente el rol.

## 6. Conclusiones de este bloque

[SDD] La especificación es la fuente única de verdad

Una especificación suficientemente detallada constituye el contrato del sistema y puede utilizarse como fuente para derivar tanto la implementación como las actividades de verificación (pruebas, validaciones y documentación).

[SDD] El testing deriva de la especificación

Las pruebas no deberían diseñarse únicamente a partir del código implementado. La especificación debe definir explícitamente el comportamiento esperado, permitiendo generar y mantener automáticamente los casos de prueba a medida que la especificación evoluciona.

[OpenSpec] La riqueza de los artefactos habilita automatización

Cuanto más completos y precisos sean los artefactos generados durante el flujo SDD, mayor será la capacidad de los agentes de IA para automatizar la implementación, la verificación y la documentación, reduciendo el trabajo repetitivo del equipo.

#### Álvaro: no está enseñando a "programar con IA", sino a construir especificaciones de suficiente calidad para que la IA pueda ejecutar trabajo de ingeniería de forma confiable.

*******************

## El siguiente bloque es interesante porque ya no introduce demasiados conceptos nuevos de SDD. Más bien muestra el grado de automatización que Álvaro consiguió en su empresa.

## 1. El ciclo completo automatizado es una implementación, no SDD
Cuando Álvaro muestra:
        1- Definición técnica
        2-Tests unitarios
        3-Tests QA E2E
        4-Documentación
        5-Code Review
        6-Corrección automática
        7-Pull Request

Eso no es SDD.
Es el pipeline de ingeniería de su empresa, construido sobre SDD y OpenSpec.
GPT no lo incorporaría como un principio metodológico nuestro.

## 2. [SDD] La especificación acompaña todo el ciclo de desarrollo
Este sí me parece un concepto nuevo.
Hasta ahora pensábamos:

        Especificación
        ↓
        Implementación

Ahora Álvaro muestra algo más cercano a:

        Especificación
        ↓
        Implementación
        ↓
        Verificación
        ↓
        Corrección
        ↓
        Integración

La especificación deja de ser el punto de partida.
Pasa a acompañar todo el ciclo.
Eso sí merece incorporarse.

## 3. [Álvaro] La IA genera evidencia, no solo código
Esto me gustó mucho.
Fijate que permanentemente habla de:
        reportes;
        screenshots;
        code review;
        explicación del commit;
        documentación.
No dice:
        "La IA programó."
Dice:
        "La IA demuestra lo que hizo."

Eso es ingeniería. No programación.


## 4. [Álvaro] El ingeniero sigue tomando la decisión
Otro punto interesante.
En ningún momento plantea:
        IA
        ↓
        Producción
Siempre hay un paso donde el ingeniero:
        lee el reporte;
        revisa la code review;
        decide.
La IA automatiza el trabajo operativo.
No reemplaza el criterio técnico.

#### ¿Qué agregaría a Conceptos_Curso_Alvaro.md?
Solo dos conceptos.
[SDD] La especificación acompaña todo el ciclo de desarrollo

La especificación no constituye únicamente el punto de partida de la implementación. Debe mantenerse como referencia durante todo el ciclo de desarrollo, incluyendo la implementación, la verificación, la revisión y la integración de los cambios.

[SDD] La IA debe generar evidencia verificable

El objetivo de utilizar IA no es únicamente automatizar la generación de código, sino también producir evidencia del trabajo realizado (documentación, reportes, resultados de pruebas y revisiones) que permita al ingeniero validar el cumplimiento de la especificación antes de integrar los cambios.

Hay algo que me llamó la atención

Creo que recién ahora se entiende por qué Álvaro insiste tanto en que las especificaciones sean tan detalladas.

Al principio parecía exagerado.

Ahora se ve el objetivo.

Si la especificación es el contrato de ingeniería, entonces todos los artefactos posteriores pueden derivarse de ella:

        código;
        pruebas;
        documentación;
        revisión;
        evidencia.

No porque exista una herramienta especial, sino porque la especificación contiene toda la información necesaria para que distintos agentes ejecuten tareas distintas de manera consistente.

***********
# Reflexiones finales
## 1. [SDD] El valor del ingeniero se desplaza de programar a especificar y revisar
La programación deja de ser el centro de la actividad. El foco pasa a ser:

        comprender el problema;
        construir especificaciones de calidad;
        revisar críticamente el resultado.

## 2. [SDD] La IA automatiza la ejecución; el ingeniero orquesta el proceso
No dice que la IA reemplace al ingeniero.
Dice que el ingeniero cambia de rol.
Su responsabilidad pasa a ser:
        definir;
        supervisar;
        revisar;
        coordinar.
No ejecutar cada tarea manualmente.
Este también me parece un principio metodológico.

## 3. [Álvaro] Priorizar calidad antes que velocidad
Cuando dice:
"Cuando el coste de hacer buen código colapsa, centrémonos en la calidad antes que en la velocidad."
Eso es claramente una recomendación personal.
Pero me parece excelente.
Además...
coincide exactamente con una decisión que ya tomamos para SmartParking.
Desde el primer día dijimos:
Aprender SDD.
No:
Terminar SmartParking rápido.
Así que no cambia nada.
Pero confirma que vamos bien.

## Concepto 1
[SDD] El foco de la ingeniería se desplaza desde la implementación hacia la especificación y la revisión

A medida que la IA automatiza una parte creciente de la implementación, el principal aporte del ingeniero consiste en comprender el problema, construir especificaciones de alta calidad y revisar críticamente los resultados obtenidos.

## Concepto 2
[SDD] El ingeniero actúa como orquestador del proceso

El objetivo no es que la IA tome decisiones de ingeniería de forma autónoma, sino que automatice las tareas repetitivas mientras el ingeniero define el contexto, supervisa el proceso y valida que los resultados cumplan con la especificación.

## Concepto 3
[SDD] La calidad tiene prioridad sobre la velocidad

La automatización proporcionada por la IA debe aprovecharse inicialmente para incrementar la calidad del proceso de desarrollo (especificaciones, pruebas, documentación y revisiones). El aumento de velocidad será una consecuencia de esa mejora, no el objetivo principal.

Algo que me gustaría destacar

Hay una frase que dijo Álvaro que, para mí, resume mucho mejor el curso que muchas de las diapositivas:

#### "Esto no va de programar. Esto va de definir muy bien y revisar muy bien."

Creo que esa frase sintetiza la esencia de SDD mucho mejor que hablar de OpenSpec, Cursor o Claude.

## Una observación final

Después de analizar todo el material que compartiste, creo que podemos distinguir claramente tres niveles:

### 1. Metodología (SDD)
Define cómo pensar y organizar el trabajo:
        partir de especificaciones;
        enriquecerlas progresivamente;
        usar la especificación como contrato;
        derivar implementación y verificación;
        mantener al ingeniero como responsable del criterio técnico.

### 2. Herramienta (OpenSpec)
Proporciona el soporte para aplicar esa metodología:
        gestión de changes;
        artefactos;
        skills;
        contexto modular;
        integración con distintos agentes de IA.

### 3. Implementación del equipo de Álvaro
Es una personalización concreta de SDD y OpenSpec para su empresa:

Jira;
ramas automáticas;
TDD;
Playwright;
CodeRabbit;
PR automáticas;
reportes exhaustivos.

Creo que esa clasificación es uno de los aprendizajes más valiosos que obtuvimos al recorrer esta parte del curso. Nos permite separar qué pertenece a la metodología, qué depende de la herramienta y qué responde al contexto específico del equipo de Álvaro, evitando extrapolar prácticas particulares como si fueran reglas universales.