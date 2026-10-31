# Módulo S-BAL – P.R.Q. S.A.
### Trabajo Práctico Integrador · Organización Empresarial · UTN – TUP a Distancia

**Módulo Automatizado de Despacho, Balances de Masa y Gestión de Stock en Tanques (S-BAL)** para la planta petroquímica ficticia *Petróleo Refinado y Químicos S.A. (P.R.Q. S.A.)*.

📋 **Tablero de gestión ágil (GitHub Projects):** [S-BAL – Backlog TPI](https://github.com/users/GeronimoValeiras/projects/1/views/1)
📄 **Documento final consolidado:** [`docs/Trabajo_Práctico_Nº4_Valeiras_Geronimo_Ezequiel.pdf`](docs/Trabajo_Práctico_Nº4_Valeiras_Geronimo_Ezequiel.pdf)

---

## Descripción del sistema

En la planta, el stock de los tanques se mide de forma manual con cinta y el balance de masa se calcula a mano por turno. El resultado son errores de medición, demoras en la facturación y riesgo de vender producto que no está disponible.

El **Módulo S-BAL** integra la **telemetría de los tanques** (nivel y temperatura, mediante OPC UA y Modbus) para:

- calcular en tiempo real la **masa disponible** de cada tanque;
- **bloquear despachos** que superen el stock y evitar así las sobreventas;
- enviar a **Facturación** la masa neta de cada despacho, sin carga manual;
- generar un **requerimiento automático a Compras** cuando un tanque baja de su stock de seguridad.

**Metas del proyecto:** actualización en pantalla en menos de 2,5 s · hasta 350.000 registros diarios de telemetría · 0 % de sobreventas · implementación completa en 40 semanas, migrando tanque por tanque.

## Integrantes

| Rol | Nombre |
|---|---|
| Alumno | **Geronimo Ezequiel Valeiras** |
| Docente titular | Prof. Gabriela Martínez |
| Docente tutor | Pablo García |

## Contenido del TPI

| Entrega | Tema | Contenido principal |
|---|---|---|
| N.º 1 | La organización y su enfoque sistémico | Caso de estudio, modelo de sistema abierto (TGS), interdependencia de módulos |
| N.º 2 | Diagnóstico y planeación | Matriz FODA, objetivo SMART y metas, Diagrama de Gantt de 40 semanas |
| N.º 3 | Estructura formal y diseño de datos | Organigramas IRAM, diccionario de datos (5 entidades) |
| N.º 4 | Procesos, trabajo colaborativo y control | BPMN del despacho, Git y GitHub, backlog ágil, indicadores de control |

## Estructura del repositorio

```
├── README.md          
├── .gitignore
├── docs/
│   ├── TPI_Valeiras_Geronimo_Ezequiel.docx   ← documento editable
│   └── TPI_Valeiras_Geronimo_Ezequiel.pdf    ← documento final consolidado
└── diagramas/         ← BPMN y figuras del TPI
```

## Flujo de trabajo

- **`main`**: versión estable del documento.
- **Ramas por etapa**: `tpi-general` y `entrega-4`. Cada una se integra a `main` mediante un **Pull Request con revisión de pares**.
- **Commits** con el formato `tipo: descripción` (`docs`, `feat`, `fix`, `chore`), que referencian el issue correspondiente (`Refs #N` / `Closes #N`).
- Las **tareas e historias de usuario** se gestionan como issues vinculados al tablero, con los estados *Por Hacer → En Progreso → Listo*.

## Historias de usuario

| ID | Historia | Prioridad |
|---|---|---|
| HU-01 | Como **operador de Sala de Control**, quiero ver el stock real de cada tanque actualizado automáticamente desde la telemetría, para dejar de medir con cinta y calcular el balance de masa sin errores manuales. | Alta |
| HU-02 | Como **responsable de Despacho y Logística**, quiero que el sistema bloquee un despacho que supere el stock disponible, para evitar sobreventas. | Alta |
| HU-03 | Como **analista de Facturación**, quiero recibir automáticamente la masa neta de cada despacho finalizado, para emitir la factura y el remito sin cargar datos a mano. | Media |

---

## Declaración de Uso de IA

Durante el TPI utilicé asistentes de IA generativa: **Gemini** (Entregas 1 y 2, incluida la imagen del modelo de sistema abierto) y **Claude** (Entregas 3 y 4, y la consolidación final). Los usé como herramienta de apoyo, no como autores. El caso de estudio, los datos técnicos de la planta y las decisiones de diseño son míos, y revisé cada resultado antes de incorporarlo.

### Prompts principales y su justificación

| Prompt (resumido) | Para qué lo usé | Por qué así |
|---|---|---|
| *"Adaptá mi word a las condiciones de la Entrega 3 siguiendo las pautas de la plantilla, usa la Unidad 4 como fuente para aplicar una correcion de ser necesaria, emprolijá los diagramos hechos en word o generale una imagen"* | Estructurar la entrega y dibujar los organigramas con las normas IRAM. | Le di las pautas y mis entregas anteriores como contexto, para que no inventara una estructura distinta a la de la cátedra. |
| *"Creame imágenes de los diagramas que te dejo en word, son FODA y Gantt, implementalos en el tpi"* | Rehacer las partes observadas y pasar el FODA y el Gantt a figuras. | Pedí cambios puntuales sobre lo observado, no reescribir todo, para no perder lo que ya estaba aprobado. |
| *"Recordame paso a paso los comandos de Git y cómo usarlos. Creame un .txt o .md para tenerlo a mano"* | Aprender el flujo de trabajo del repositorio. | Necesitaba recordar cada paso en la termina para poder ejecutarlo y defenderlo. |
| *"Tomando en cuenta este boceto, cómo implementamos propiamente la consigna de bpmn? Dame una guía para dibujarlo en Bizagi."* | Definir el proceso de despacho y su lógica de excepciones. | Pedí una guía de Bizagi, nunca lo había usado. |
| *"Según las metas dadas en el TPI 2, y tomando en cuenta los indicadores dado en el .txt, crea la tabla requerida"* | Armar la tabla de indicadores (Consigna 4). | Partir de mis metas de la Entrega 2 garantiza la coherencia entre la planeación y el control. |
### Correcciones humanas sobre los resultados

- **El texto era "demasiado perfecto".** La primera versión de la Entrega 3 sonaba como un manual de IA, se dió muchas libertades en las correciones. Pedí reducir las correciones a solo cuestiones indispensables o de contexto, le brindé un .txt con algunas experiencias de planta para que considere agregarlas. Después corregí el exceso contrario: saqué expresiones coloquiales que no corresponden a un trabajo académico.
- **Validación técnica.** Verifiqué contra mi experiencia en planta los datos del dominio: corrección del volumen por temperatura, densidad de referencia, protocolos, rol de HSE como staff, restricciones de acceso a zonas clasificadas y operación en turnos.
- **Decisiones propias.** Agregar el puesto de *Redes y Telemetría (OT)*, ubicar HSE como staff y definir las metas (2,5 s, 350.000 registros diarios, 40 semanas) fueron decisiones mías, que la IA solo ayudó a redactar.
- **Coherencia entre entregas.** Detecté y corregí un error en la Entrega 1 (un nombre de empresa que no correspondía al caso) y revisé que las figuras, las tablas y las referencias cruzadas coincidieran en el documento consolidado.

Asumo la responsabilidad total sobre el contenido. Cualquier error del modelo que no haya detectado es un error mío.
