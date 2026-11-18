# Herencias: testamentos, partición y legítimas · España

> Plugin de Claude Code `modelos-herencias-espana` · **87 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para herencias: testamentos, declaración de herederos, aceptación y repudiación, partición y cuaderno particional, legítimas, desheredación y las acciones judiciales sobre la herencia.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 87 está al final):

- **Demandas, interposiciones y peticiones iniciales** (30). Por ejemplo: Demanda declarativa de prescripción de los derechos legitimarios; Demanda contra el cuaderno particional del contador-partidor dativo de notaría; Nulidad de la partición hereditaria: demanda.
- **Contestaciones, oposiciones y alegaciones** (7). Por ejemplo: Contestación a la demanda de nulidad de testamento (juicio ordinario); Contestación a la demanda de adición a la partición hereditaria; Oposición a la división judicial de la herencia e intervención del caudal.
- **Solicitudes y expedientes** (19). Por ejemplo: Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación; Requerimiento para aceptar o repudiar la herencia (Aragón); Cese de la intervención judicial de la herencia.
- **Escritos de trámite** (3). Por ejemplo: Sucesión del fiador en la posición procesal del ejecutante; Autorización al acreedor para aceptar la herencia; Jura de cuentas del procurador contra la herencia yacente.
- **Actos y resoluciones de la Administración o del órgano judicial** (2). Por ejemplo: Acta de sorteo del contador-partidor por acuerdo mayoritario (Galicia); Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia).
- **Contratos, escrituras y documentos** (18). Por ejemplo: Designación del delegado de protección de datos en el sector público; Designación del delegado de protección de datos en el sector privado; Testamento en caso de epidemia.
- **Comunicaciones, requerimientos y reclamaciones** (2). Por ejemplo: Honorarios de abogado contra herencia yacente: reclamación; Requerir al contador-partidor.
- **Otros** (6). Por ejemplo: Ineficacia sobrevenida del testamento por premoriencia de los herederos; Revocar conjuntamente el testamento mancomunado correspectivo (Galicia); Revocar unilateralmente el testamento mancomunado correspectivo (Galicia).

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de nulidad de la partición hereditaria»
   - «Demanda contra el cuaderno particional del contador-partidor dativo»
   - «Oposición a la división judicial de la herencia»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-herencias-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-herencias-espana:contestacion-demanda-nulidad-testamento-juicio-ordinario-17`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 7.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-herencias-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-herencias-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-herencias-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-herencias-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (30)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 31 | Demanda declarativa de prescripción de los derechos legitimarios | 2024 | `demanda-declarativa-prescripcion-derechos-legitimarios-31` |
| 41 | Demanda contra el cuaderno particional del contador-partidor dativo de notaría | 2024 | `demanda-contra-cuaderno-particional-contador-partidor-41` |
| 42 | Nulidad de la partición hereditaria: demanda | 2024 | `nulidad-particion-hereditaria-demanda-42` |
| 75 | Demanda de rendición de cuentas contra un coheredero | 2023 | `demanda-rendicion-cuentas-contra-coheredero-75` |
| 108 | Casación del art. 477.2 LEC por derechos fundamentales: intromisión en el honor | 2022 | `casacion-art-477-2-lec-derechos-fundamentales-108` |
| 129 | Demanda por intromisión en la intimidad personal y familiar (art. 18.1 CE) | 2022 | `demanda-intromision-intimidad-personal-familiar-art-18-1-129` |
| 181 | Impugnación de testamento por desheredación (Cataluña) | 2021 | `impugnacion-testamento-desheredacion-cataluna-181` |
| 186 | Demanda de ejecución de sentencia contra herencia yacente | 2021 | `demanda-ejecucion-sentencia-contra-herencia-yacente-186` |
| 205 | Acción rescisoria de herencia por lesión de más de una cuarta parte | 2020 | `accion-rescisoria-herencia-lesion-mas-cuarta-parte-205` |
| 212 | Impugnación de testamento por preterición | 2020 | `impugnacion-testamento-pretericion-212` |
| 213 | Impugnación de testamento por desheredación (acción general) | 2020 | `impugnacion-testamento-desheredacion-accion-general-213` |
| 325 | Demanda ordinaria de reducción de legado | 2020 | `demanda-ordinaria-reduccion-legado-325` |
| 330 | Demanda de declaración de indignidad del heredero | 2020 | `demanda-declaracion-indignidad-heredero-330` |
| 343 | Demanda de petición de herencia | 2019 | `demanda-peticion-herencia-343` |
| 345 | Demanda de reclamación de legítima (Galicia) | 2019 | `demanda-reclamacion-legitima-galicia-345` |
| 352 | Demanda verbal de complemento de legítima | 2019 | `demanda-verbal-complemento-legitima-352` |
| 356 | Demanda de un coheredero en beneficio de la comunidad hereditaria | 2019 | `demanda-coheredero-beneficio-comunidad-hereditaria-356` |
| 376 | Demanda ordinaria de complemento de legítima | 2019 | `demanda-ordinaria-complemento-legitima-376` |
| 416 | Demanda de cantidad por venta de acciones sin el consentimiento de todos los coherederos | 2018 | `demanda-cantidad-venta-acciones-sin-consentimiento-todos-416` |
| 431 | Demanda ordinaria de reducción de legado por inoficioso | 2018 | `demanda-ordinaria-reduccion-legado-inoficioso-431` |
| 446 | Casación del art. 477.2 LEC por derechos fundamentales: intromisión en la intimidad | 2018 | `casacion-art-477-2-lec-derechos-fundamentales-446` |
| 454 | Demanda verbal de cantidad contra herencia yacente | 2018 | `demanda-verbal-cantidad-contra-herencia-yacente-454` |
| 464 | Demanda por intromisión en el honor por injurias leves | 2017 | `demanda-intromision-honor-injurias-leves-464` |
| 504 | Demanda por inclusión indebida en registro de morosos (honor) | 2017 | `demanda-inclusion-indebida-registro-morosos-honor-504` |
| 508 | Desahucio por precario entre coherederos: demanda | 2017 | `desahucio-precario-entre-coherederos-demanda-508` |
| 572 | Demanda de ejecución hipotecaria contra herencia yacente | 2016 | `demanda-ejecucion-hipotecaria-contra-herencia-yacente-572` |
| 1183 | Demanda de reclamación de legítima (Derecho civil de Cataluña) | 2014 | `demanda-reclamacion-legitima-derecho-civil-cataluna-1183` |
| 1466 | Ejecución de tasación de costas contra la herencia yacente | 2014 | `ejecucion-tasacion-costas-contra-herencia-yacente-1466` |
| 1468 | Demanda de cantidad contra herencia yacente | 2014 | `demanda-cantidad-contra-herencia-yacente-1468` |
| 1498 | Demanda de remoción del albacea testamentario | 2014 | `demanda-remocion-albacea-testamentario-1498` |

### Contestaciones, oposiciones y alegaciones (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 17 | Contestación a la demanda de nulidad de testamento (juicio ordinario) | 2024 | `contestacion-demanda-nulidad-testamento-juicio-ordinario-17` |
| 18 | Contestación a la demanda de adición a la partición hereditaria | 2024 | `contestacion-demanda-adicion-particion-hereditaria-18` |
| 263 | Oposición a la división judicial de la herencia e intervención del caudal | 2020 | `oposicion-division-judicial-herencia-e-intervencion-263` |
| 328 | Contestación a la demanda de indignidad del heredero | 2020 | `contestacion-demanda-indignidad-heredero-328` |
| 329 | Contestación a la demanda de indignidad con rehabilitación tácita o expresa del causante | 2020 | `contestacion-demanda-indignidad-rehabilitacion-tacita-329` |
| 351 | Contestación a demanda de complemento de legítima con reconvención de nulidad de la partición | 2019 | `contestacion-demanda-complemento-legitima-reconvencion-351` |
| 428 | Contestación oponiendo falta de legitimación pasiva | 2018 | `contestacion-oponiendo-falta-legitimacion-pasiva-428` |

### Solicitudes y expedientes (19)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 46 | Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación | 2023 | `pedir-contador-partidor-nuevo-cuaderno-particional-46` |
| 111 | Requerimiento para aceptar o repudiar la herencia (Aragón) | 2022 | `requerimiento-aceptar-repudiar-herencia-aragon-111` |
| 262 | Cese de la intervención judicial de la herencia | 2020 | `cese-intervencion-judicial-herencia-262` |
| 264 | Intervención judicial de la herencia | 2020 | `intervencion-judicial-herencia-264` |
| 316 | Administrador judicial de herencia abintestato sin declaración de herederos | 2020 | `administrador-judicial-herencia-abintestato-sin-316` |
| 631 | Renuncia de un albacea ante notario | 2015 | `renuncia-albacea-ante-notario-631` |
| 662 | Requerimiento notarial para presentar un testamento cerrado | 2015 | `requerimiento-notarial-presentar-testamento-cerrado-662` |
| 671 | Adveración, apertura y protocolización de testamento oral | 2015 | `adveracion-apertura-protocolizacion-testamento-oral-671` |
| 723 | Renuncia del contador-partidor o prórroga de su plazo | 2015 | `renuncia-contador-partidor-prorroga-plazo-723` |
| 724 | Renuncia del albacea o prórroga del albaceazgo | 2015 | `renuncia-albacea-prorroga-albaceazgo-724` |
| 726 | Remoción del albacea | 2015 | `remocion-albacea-726` |
| 727 | Autorización al albacea para disponer de bienes de la herencia | 2015 | `autorizacion-albacea-disponer-bienes-herencia-727` |
| 728 | Rendición de cuentas del albacea | 2015 | `rendicion-cuentas-albacea-728` |
| 730 | Aprobación de la partición del contador-partidor no confirmada por todos los herederos y legatarios | 2015 | `aprobacion-particion-contador-partidor-no-confirmada-730` |
| 732 | Designación de contador-partidor dativo (art. 1057 CC) | 2015 | `designacion-contador-partidor-dativo-art-1057-cc-732` |
| 736 | Aprobación judicial de la repudiación de herencia por asociaciones, corporaciones y fundaciones | 2015 | `aprobacion-judicial-repudiacion-herencia-asociaciones-736` |
| 860 | Intervención judicial de la herencia tras la declaración de herederos | 2013 | `intervencion-judicial-herencia-tras-declaracion-860` |
| 1041 | Exhibición de acto de última voluntad: petición | 2013 | `exhibicion-acto-ultima-voluntad-peticion-1041` |
| 1145 | Sobreseimiento por acuerdo de los herederos | 2013 | `sobreseimiento-acuerdo-herederos-1145` |

### Escritos de trámite (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 278 | Sucesión del fiador en la posición procesal del ejecutante | 2020 | `sucesion-fiador-posicion-procesal-ejecutante-278` |
| 735 | Autorización al acreedor para aceptar la herencia | 2015 | `autorizacion-acreedor-aceptar-herencia-735` |
| 1467 | Jura de cuentas del procurador contra la herencia yacente | 2014 | `jura-cuentas-procurador-contra-herencia-yacente-1467` |

### Actos y resoluciones de la Administración o del órgano judicial (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 540 | Acta de sorteo del contador-partidor por acuerdo mayoritario (Galicia) | 2016 | `acta-sorteo-contador-partidor-acuerdo-mayoritario-540` |
| 541 | Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia) | 2016 | `acta-requerimiento-designar-contador-partidor-acuerdo-541` |

### Contratos, escrituras y documentos (18)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 214 | Designación del delegado de protección de datos en el sector público | 2020 | `designacion-delegado-proteccion-datos-sector-publico-214` |
| 215 | Designación del delegado de protección de datos en el sector privado | 2020 | `designacion-delegado-proteccion-datos-sector-privado-215` |
| 303 | Testamento en caso de epidemia | 2020 | `testamento-caso-epidemia-303` |
| 539 | Partija de los coherederos en documento privado (Galicia) | 2016 | `partija-coherederos-documento-privado-galicia-539` |
| 542 | Partija por acuerdo mayoritario protocolizada en escritura (Galicia) | 2016 | `partija-acuerdo-mayoritario-protocolizada-escritura-542` |
| 545 | Otorgamiento de testamento mancomunado correspectivo (Galicia) | 2016 | `otorgamiento-testamento-mancomunado-correspectivo-545` |
| 549 | Partija conjunta extratestamentaria en documento privado | 2016 | `partija-conjunta-extratestamentaria-documento-privado-549` |
| 565 | Partija conjunta extratestamentaria para protocolizar (Galicia) | 2016 | `partija-conjunta-extratestamentaria-protocolizar-galicia-565` |
| 567 | Partija del contador-partidor en documento privado (Galicia) | 2016 | `partija-contador-partidor-documento-privado-galicia-567` |
| 568 | Partija del testador en documento privado extratestamentario (Galicia) | 2016 | `partija-testador-documento-privado-extratestamentario-568` |
| 569 | Escritura de pacto de mejora sin entrega de presente (Galicia) | 2016 | `escritura-pacto-mejora-sin-entrega-presente-galicia-569` |
| 570 | Escritura de pacto de mejora con entrega de presente (Galicia) | 2016 | `escritura-pacto-mejora-entrega-presente-galicia-570` |
| 571 | Escritura de pacto de apartación (Galicia) | 2016 | `escritura-pacto-apartacion-galicia-571` |
| 579 | Otorgamiento de testamento mancomunado cerrado (Aragón) | 2016 | `otorgamiento-testamento-mancomunado-cerrado-aragon-579` |
| 586 | Otorgamiento de testamento ológrafo mancomunado (Aragón) | 2016 | `otorgamiento-testamento-olografo-mancomunado-aragon-586` |
| 1185 | Testamento con desheredación | 2014 | `testamento-desheredacion-1185` |
| 1445 | Testamento con cláusula de cautela socini | 2014 | `testamento-clausula-cautela-socini-1445` |
| 1450 | Contrato de servicios entre sociedad y consejero delegado | 2014 | `contrato-servicios-entre-sociedad-consejero-delegado-1450` |

### Comunicaciones, requerimientos y reclamaciones (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 462 | Honorarios de abogado contra herencia yacente: reclamación | 2017 | `honorarios-abogado-contra-herencia-yacente-reclamacion-462` |
| 1147 | Requerir al contador-partidor | 2013 | `requerir-contador-partidor-1147` |

### Otros (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 210 | Ineficacia sobrevenida del testamento por premoriencia de los herederos | 2020 | `ineficacia-sobrevenida-testamento-premoriencia-herederos-210` |
| 543 | Revocar conjuntamente el testamento mancomunado correspectivo (Galicia) | 2016 | `revocar-conjuntamente-testamento-mancomunado-543` |
| 544 | Revocar unilateralmente el testamento mancomunado correspectivo (Galicia) | 2016 | `revocar-unilateralmente-testamento-mancomunado-544` |
| 566 | Protocolización de partija conjunta y testamento paralelo (Galicia) | 2016 | `protocolizacion-partija-conjunta-testamento-paralelo-566` |
| 580 | Revocar unilateralmente testamento mancomunado (País Vasco) | 2016 | `revocar-unilateralmente-testamento-mancomunado-pais-580` |
| 581 | Revocar conjuntamente testamento mancomunado (País Vasco) | 2016 | `revocar-conjuntamente-testamento-mancomunado-pais-vasco-581` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

