# Apelación, casación y recursos civiles · España

> Plugin de Claude Code `modelos-recursos-civiles-espana` · **75 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para impugnar resoluciones civiles: recurso de reposición y de revisión, apelación y oposición a la apelación, casación y oposición a la casación, queja y nulidad de actuaciones.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 75 está al final):

- **Demandas, interposiciones y peticiones iniciales** (26). Por ejemplo: Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023); Interposición de casación por infracción procesal en la valoración de la prueba (reforma RDL 5/2023); Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023).
- **Recursos e impugnaciones** (30). Por ejemplo: Recurso de apelación contra la valoración de la prueba testifical; Recurso de apelación en la división de cosa común; Reposición contra la diligencia que señala vista telemática.
- **Contestaciones, oposiciones y alegaciones** (6). Por ejemplo: Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023); Oposición al recurso de apelación en jurisdicción voluntaria; Alegaciones en el incidente de nulidad de actuaciones.
- **Solicitudes y expedientes** (5). Por ejemplo: Nulidad de actuaciones en jurisdicción voluntaria; Certificación de la sentencia para recurrir en casación; Aclaraciones al perito en el juicio o vista.
- **Escritos de trámite** (4). Por ejemplo: Impugnación del recurso de revisión contra decreto en jurisdicción voluntaria; Subsanar la falta de tasa judicial en la apelación; Otrosí de proposición de prueba en apelación.
- **Otros** (4). Por ejemplo: Incidente excepcional de nulidad por defecto de emplazamiento telemático; Reposición oral contra resolución dictada en la comparecencia; Nulidad de actuaciones por vía de recurso.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Recurso de apelación contra una sentencia de desahucio»
   - «Escrito de oposición al recurso de casación»
   - «Recurso de reposición contra la inadmisión de una prueba»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-recursos-civiles-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-recursos-civiles-espana:recurso-apelacion-contra-valoracion-prueba-testifical-22`. Los nombres están en la lista de formularios de abajo.

## Qué hace Claude cuando usas un formulario

1. Comprueba que Jurisprudenciator está conectado. Si no lo está, se para y te dice cómo conectarlo: no redacta nada sin él.
   Todos los datos jurídicos del escrito (artículos vigentes, sentencias con su ECLI, convenios, datos registrales) salen de Jurisprudenciator; nunca de memoria.
2. Te pide en una sola tanda los datos del caso (partes, órgano, fechas, importes…). Lo que no sepas queda como hueco visible.
3. Resuelve contigo las opciones que el formulario deja abiertas y decide qué párrafos opcionales entran según los hechos.
4. Aplica las correcciones y avisos de la revisión del 17-11-2026 (reformas legales, órganos, plazos).
5. Comprueba en el BOE, con Jurisprudenciator, cada norma que cita el escrito; si alguna ha cambiado, usa la redacción vigente y te lo dice.
6. Te indica el plazo y ante quién se presenta, y te entrega el escrito en Word con un resumen de lo que queda pendiente.

El resultado es un borrador para que lo revise un profesional antes de presentarlo.

## Antes de empezar

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 6.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-recursos-civiles-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-recursos-civiles-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-recursos-civiles-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-recursos-civiles-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (26)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 50 | Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023) | 2023 | `interposicion-casacion-civil-interes-casacional-pais-50` |
| 51 | Interposición de casación por infracción procesal en la valoración de la prueba (reforma RDL 5/2023) | 2023 | `interposicion-casacion-infraccion-procesal-valoracion-51` |
| 55 | Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023) | 2023 | `interposicion-casacion-interes-casacional-infraccion-art-55` |
| 285 | Recurso extraordinario por infracción procesal del art. 469.1.3º LEC (anterior al RDL 5/2023) | 2020 | `recurso-extraordinario-infraccion-procesal-art-469-1-3o-285` |
| 286 | Recurso extraordinario por infracción procesal del art. 469.1.4º LEC (anterior al RDL 5/2023) | 2020 | `recurso-extraordinario-infraccion-procesal-art-469-1-4o-286` |
| 287 | Recurso extraordinario por infracción procesal del art. 469.1.1º LEC (anterior al RDL 5/2023) | 2020 | `recurso-extraordinario-infraccion-procesal-art-469-1-1o-287` |
| 367 | Recurso de apelación contra sentencia de desahucio | 2019 | `recurso-apelacion-contra-sentencia-desahucio-367` |
| 444 | Casación por infracción procesal y vulneración del art. 24 CE (tutela judicial efectiva) | 2018 | `casacion-infraccion-procesal-vulneracion-art-24-ce-444` |
| 445 | Casación por infracción de normas procesales que rigen los actos y garantías del proceso | 2018 | `casacion-infraccion-normas-procesales-rigen-actos-445` |
| 447 | Casación por oposición a la doctrina jurisprudencial del Tribunal Supremo | 2018 | `casacion-oposicion-doctrina-jurisprudencial-tribunal-447` |
| 448 | Casación por interés casacional: normas sin doctrina jurisprudencial del Tribunal Supremo | 2018 | `casacion-interes-casacional-normas-sin-doctrina-448` |
| 449 | Casación por jurisprudencia contradictoria de Audiencias Provinciales | 2018 | `casacion-jurisprudencia-contradictoria-audiencias-449` |
| 450 | Casación por infracción de normas de jurisdicción y competencia | 2018 | `casacion-infraccion-normas-jurisdiccion-competencia-450` |
| 451 | Casación por infracción de norma procesal y sustantiva | 2018 | `casacion-infraccion-norma-procesal-sustantiva-451` |
| 452 | Casación por infracción de las normas procesales reguladoras de la sentencia | 2018 | `casacion-infraccion-normas-procesales-reguladoras-452` |
| 507 | Incidente excepcional de nulidad de actuaciones: interposición | 2017 | `incidente-excepcional-nulidad-actuaciones-interposicion-507` |
| 640 | Apelación contra resolución definitiva en jurisdicción voluntaria | 2015 | `apelacion-contra-resolucion-definitiva-jurisdiccion-640` |
| 758 | Apelación en jurisdicción voluntaria: modelo genérico | 2015 | `apelacion-jurisdiccion-voluntaria-modelo-generico-758` |
| 759 | Reposición en jurisdicción voluntaria: modelo genérico | 2015 | `reposicion-jurisdiccion-voluntaria-modelo-generico-759` |
| 762 | Recurso de revisión en jurisdicción voluntaria (modelo genérico) | 2015 | `recurso-revision-jurisdiccion-voluntaria-modelo-generico-762` |
| 878 | Interponer el recurso de casación | 2013 | `interponer-recurso-casacion-878` |
| 1048 | Recurso de queja por inadmisión de la apelación | 2013 | `recurso-queja-inadmision-apelacion-1048` |
| 1063 | Recurso de queja por inadmisión de la casación | 2013 | `recurso-queja-inadmision-casacion-1063` |
| 1127 | Casación e infracción procesal conjuntas y simultáneas, previo al RDL 5/2023 (general) | 2013 | `casacion-e-infraccion-procesal-conjuntas-simultaneas-1127` |
| 1335 | Interposición de la apelación | 2013 | `interposicion-apelacion-1335` |
| 1463 | Apelación contra el auto que resuelve la oposición | 2014 | `apelacion-contra-auto-resuelve-oposicion-1463` |

### Recursos e impugnaciones (30)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 22 | Recurso de apelación contra la valoración de la prueba testifical | 2024 | `recurso-apelacion-contra-valoracion-prueba-testifical-22` |
| 135 | Recurso de apelación en la división de cosa común | 2022 | `recurso-apelacion-division-cosa-comun-135` |
| 142 | Reposición contra la diligencia que señala vista telemática | 2021 | `reposicion-contra-diligencia-senala-vista-telematica-142` |
| 155 | Oposición a la apelación sobre cláusula suelo | 2021 | `oposicion-apelacion-sobre-clausula-suelo-155` |
| 170 | Oposición a la apelación sobre gastos de constitución de hipoteca | 2021 | `oposicion-apelacion-sobre-gastos-constitucion-hipoteca-170` |
| 317 | Recurso de revisión contra decreto que resuelve la reposición | 2020 | `recurso-revision-contra-decreto-resuelve-reposicion-317` |
| 374 | Oposición a la acción de anulación del laudo arbitral | 2019 | `oposicion-accion-anulacion-laudo-arbitral-374` |
| 438 | Apelación contra el auto de inadmisión de demanda verbal | 2018 | `apelacion-contra-auto-inadmision-demanda-verbal-438` |
| 439 | Apelación contra el auto que tiene por desistido al actor | 2018 | `apelacion-contra-auto-tiene-desistido-actor-439` |
| 519 | Recurso de apelación sobre cláusula suelo | 2016 | `recurso-apelacion-sobre-clausula-suelo-519` |
| 666 | Revisión contra el decreto que inadmite un acto de conciliación | 2015 | `revision-contra-decreto-inadmite-acto-conciliacion-666` |
| 673 | Reposición contra resolución del LAJ en jurisdicción voluntaria | 2015 | `reposicion-contra-resolucion-laj-jurisdiccion-voluntaria-673` |
| 674 | Revisión contra decreto definitivo del LAJ en jurisdicción voluntaria | 2015 | `revision-contra-decreto-definitivo-laj-jurisdiccion-674` |
| 757 | Revisión contra el decreto que declara la caducidad | 2015 | `revision-contra-decreto-declara-caducidad-757` |
| 837 | Oposición a la infracción procesal extraordinaria: modelo general | 2013 | `oposicion-infraccion-procesal-extraordinaria-modelo-837` |
| 903 | Reposición contra el auto que rechaza la declinatoria | 2013 | `reposicion-contra-auto-rechaza-declinatoria-903` |
| 962 | Reposición por admisión o inadmisión de prueba | 2013 | `reposicion-admision-inadmision-prueba-962` |
| 965 | Reposición contra la inadmisión de prueba | 2013 | `reposicion-contra-inadmision-prueba-965` |
| 990 | Reposición contra la fijación de gastos de testigo | 2013 | `reposicion-contra-fijacion-gastos-testigo-990` |
| 1061 | Apelación contra la desestimación del recurso de revisión | 2013 | `apelacion-contra-desestimacion-recurso-revision-1061` |
| 1074 | Apelación contra el auto que suspende por prejudicialidad civil | 2013 | `apelacion-contra-auto-suspende-prejudicialidad-civil-1074` |
| 1075 | Reposición contra la denegación de suspensión por prejudicialidad civil | 2013 | `reposicion-contra-denegacion-suspension-prejudicialidad-1075` |
| 1076 | Impugnación de la reposición contra la denegación de suspensión por prejudicialidad civil | 2013 | `impugnacion-reposicion-contra-denegacion-suspension-1076` |
| 1079 | Impugnación de la reposición del demandado contra el auto que deniega suspender el procedimiento | 2013 | `impugnacion-reposicion-demandado-contra-auto-deniega-1079` |
| 1080 | Reposición contra la denegación de suspensión por prejudicialidad penal | 2013 | `reposicion-contra-denegacion-suspension-prejudicialidad-1080` |
| 1083 | Apelación contra el auto que suspende por prejudicialidad penal | 2013 | `apelacion-contra-auto-suspende-prejudicialidad-penal-1083` |
| 1088 | Apelación contra el auto que se abstiene por falta de competencia objetiva | 2013 | `apelacion-contra-auto-abstiene-falta-competencia-1088` |
| 1128 | Oponerse al recurso de casación | 2013 | `oponerse-recurso-casacion-1128` |
| 1352 | Apelación en propiedad horizontal (juicio ordinario o verbal) | 2013 | `apelacion-propiedad-horizontal-juicio-ordinario-verbal-1352` |
| 1354 | Reposición por no indicar si cabe enervación | 2013 | `reposicion-no-indicar-si-cabe-enervacion-1354` |

### Contestaciones, oposiciones y alegaciones (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 25 | Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023) | 2024 | `oposicion-recurso-casacion-modelo-general-rdl-5-2023-6-25` |
| 653 | Oposición al recurso de apelación en jurisdicción voluntaria | 2015 | `oposicion-recurso-apelacion-jurisdiccion-voluntaria-653` |
| 927 | Alegaciones en el incidente de nulidad de actuaciones | 2013 | `alegaciones-incidente-nulidad-actuaciones-927` |
| 1071 | Oposición al mantenimiento de medidas cautelares al recurrir la sentencia (general) | 2013 | `oposicion-mantenimiento-medidas-cautelares-recurrir-1071` |
| 1072 | Alegaciones de disconformidad con la causa de inadmisión del recurso | 2013 | `alegaciones-disconformidad-causa-inadmision-recurso-1072` |
| 1073 | Alegaciones de conformidad con la causa de inadmisión del recurso | 2013 | `alegaciones-conformidad-causa-inadmision-recurso-1073` |

### Solicitudes y expedientes (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 276 | Nulidad de actuaciones en jurisdicción voluntaria | 2020 | `nulidad-actuaciones-jurisdiccion-voluntaria-276` |
| 836 | Certificación de la sentencia para recurrir en casación | 2013 | `certificacion-sentencia-recurrir-casacion-836` |
| 999 | Aclaraciones al perito en el juicio o vista | 2013 | `aclaraciones-perito-juicio-vista-999` |
| 1062 | Mantenimiento de medidas cautelares al recurrir la sentencia | 2013 | `mantenimiento-medidas-cautelares-recurrir-sentencia-1062` |
| 1126 | Certificación de la sentencia para casación e infracción procesal conjuntas | 2013 | `certificacion-sentencia-casacion-e-infraccion-procesal-1126` |

### Escritos de trámite (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 677 | Impugnación del recurso de revisión contra decreto en jurisdicción voluntaria | 2015 | `impugnacion-recurso-revision-contra-decreto-jurisdiccion-677` |
| 838 | Subsanar la falta de tasa judicial en la apelación | 2013 | `subsanar-falta-tasa-judicial-apelacion-838` |
| 959 | Otrosí de proposición de prueba en apelación | 2013 | `otrosi-proposicion-prueba-apelacion-959` |
| 1097 | Otrosí: ofrecimiento de abono, consignación, depósito o aval para preparar recursos | 2013 | `otrosi-ofrecimiento-abono-consignacion-deposito-aval-1097` |

### Otros (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 350 | Incidente excepcional de nulidad por defecto de emplazamiento telemático | 2019 | `incidente-excepcional-nulidad-defecto-emplazamiento-350` |
| 678 | Reposición oral contra resolución dictada en la comparecencia | 2015 | `reposicion-oral-contra-resolucion-dictada-comparecencia-678` |
| 925 | Nulidad de actuaciones por vía de recurso | 2013 | `nulidad-actuaciones-via-recurso-925` |
| 1098 | Adhesión a la apelación | 2013 | `adhesion-apelacion-1098` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

