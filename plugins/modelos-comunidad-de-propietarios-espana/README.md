# Comunidades de propietarios: juntas, acuerdos y morosos · España

> Plugin de Claude Code `modelos-comunidad-de-propietarios-espana` · **78 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para comunidades de propietarios: convocatorias, actas y certificados de la junta, impugnación de acuerdos, acción de cesación de actividades molestas o prohibidas, obras y accesibilidad, cuotas y relaciones con el administrador.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 78 está al final):

- **Demandas, interposiciones y peticiones iniciales** (15). Por ejemplo: Demanda contra la comunidad para obras de accesibilidad: instalación de ascensor; Demanda por obras no autorizadas en la comunidad de propietarios; Demanda verbal contra la comunidad por indemnización al cesar al administrador.
- **Recursos e impugnaciones** (2). Por ejemplo: Impugnación de acuerdo de junta lesivo o perjudicial; Impugnación de acuerdo de junta contrario a la ley o a los estatutos.
- **Contestaciones, oposiciones y alegaciones** (6). Por ejemplo: Contestación a la demanda por alteración de elementos comunes en propiedad horizontal; Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas; Contestación a reclamación de cuotas impagadas por el anterior propietario.
- **Solicitudes y expedientes** (7). Por ejemplo: Prueba pericial anticipada en propiedad horizontal antes del proceso; Permiso para instalaciones provisionales en elementos comunes por obra privativa; Convocatoria de junta solicitada por comuneros al presidente.
- **Escritos de trámite** (5). Por ejemplo: Propietario pide al presidente que requiera a otro el cese de actividades prohibidas; Otrosí: acreditación de pago de cantidades debidas por un comunero; Declinatoria por mediación pactada entre comuneros y comunidad.
- **Actos y resoluciones de la Administración o del órgano judicial** (22). Por ejemplo: Certificado de estar al corriente de pago en la comunidad de propietarios; Certificado del acuerdo de la junta de ejercitar la acción de cesación; Acta que acuerda desafectar elementos comunes para venderlos.
- **Contratos, escrituras y documentos** (6). Por ejemplo: Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención; Cláusula informativa de videovigilancia en comunidades de propietarios; Respuesta de la comunidad al derecho de acceso sobre su videovigilancia.
- **Comunicaciones, requerimientos y reclamaciones** (11). Por ejemplo: Convocatoria de la junta general ordinaria de propietarios (Cataluña); Aviso a la comunidad de obra en vivienda o local; Convocatoria de junta extraordinaria para instalar ascensor.
- **Otros** (4). Por ejemplo: Constitución en comunidad de propietarios de un complejo inmobiliario privado; Comunidad agrupada: estatutos; Constitución en agrupación de comunidades de propietarios.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de impugnación de un acuerdo de la junta contrario a la ley o a los estatutos»
   - «Demanda de cesación de una actividad molesta contra un propietario»
   - «Convocatoria de junta extraordinaria para reclamar cuotas atrasadas»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-comunidad-de-propietarios-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-comunidad-de-propietarios-espana:contestacion-demanda-alteracion-elementos-comunes-5`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 7.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-comunidad-de-propietarios-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-comunidad-de-propietarios-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-comunidad-de-propietarios-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-comunidad-de-propietarios-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (15)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 7 | Demanda contra la comunidad para obras de accesibilidad: instalación de ascensor | 2025 | `demanda-contra-comunidad-obras-accesibilidad-instalacion-7` |
| 71 | Demanda por obras no autorizadas en la comunidad de propietarios | 2023 | `demanda-obras-no-autorizadas-comunidad-propietarios-71` |
| 306 | Demanda verbal contra la comunidad por indemnización al cesar al administrador | 2020 | `demanda-verbal-contra-comunidad-indemnizacion-cesar-306` |
| 315 | Demanda ordinaria de constitución de edificio en propiedad horizontal | 2020 | `demanda-ordinaria-constitucion-edificio-propiedad-315` |
| 359 | Demanda contra el promotor por impugnación del título constitutivo de propiedad horizontal | 2019 | `demanda-contra-promotor-impugnacion-titulo-constitutivo-359` |
| 365 | Demanda verbal de división de cosa común y constitución en propiedad horizontal | 2019 | `demanda-verbal-division-cosa-comun-constitucion-365` |
| 395 | Demanda de la comunidad contra un propietario para acceder a su vivienda o local | 2019 | `demanda-comunidad-contra-propietario-acceder-vivienda-395` |
| 420 | Demanda de daños entre comunidades de propietarios en elementos comunes | 2018 | `demanda-danos-entre-comunidades-propietarios-elementos-420` |
| 503 | Demanda contra propietario por aire acondicionado no consentido en patio interior | 2017 | `demanda-contra-propietario-aire-acondicionado-no-503` |
| 609 | Demanda de impugnación de acuerdos de la junta lesivos para la comunidad | 2016 | `demanda-impugnacion-acuerdos-junta-lesivos-comunidad-609` |
| 842 | Demanda de la comunidad contra un comunero por alterar elementos comunes | 2015 | `demanda-comunidad-contra-comunero-alterar-elementos-842` |
| 1245 | Demanda de repetición del antiguo propietario | 2013 | `demanda-repeticion-antiguo-propietario-1245` |
| 1329 | Cesación de actividad e indemnización por perjuicios contra propietario | 2013 | `cesacion-actividad-e-indemnizacion-perjuicios-contra-1329` |
| 1339 | Cesación de actividad contra propietario (general) | 2013 | `cesacion-actividad-contra-propietario-general-1339` |
| 1440 | Demanda de cesación de actividades prohibidas con indemnización de daños | 2013 | `demanda-cesacion-actividades-prohibidas-indemnizacion-1440` |

### Recursos e impugnaciones (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1289 | Impugnación de acuerdo de junta lesivo o perjudicial | 2013 | `impugnacion-acuerdo-junta-lesivo-perjudicial-1289` |
| 1334 | Impugnación de acuerdo de junta contrario a la ley o a los estatutos | 2013 | `impugnacion-acuerdo-junta-contrario-ley-estatutos-1334` |

### Contestaciones, oposiciones y alegaciones (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 5 | Contestación a la demanda por alteración de elementos comunes en propiedad horizontal | 2025 | `contestacion-demanda-alteracion-elementos-comunes-5` |
| 603 | Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas | 2016 | `oposicion-solicitud-cesacion-actividades-prohibidas-603` |
| 1221 | Contestación a reclamación de cuotas impagadas por el anterior propietario | 2013 | `contestacion-reclamacion-cuotas-impagadas-anterior-1221` |
| 1371 | Contestación del propietario no usuario a demanda de cesación de actividades prohibidas | 2013 | `contestacion-propietario-no-usuario-demanda-cesacion-1371` |
| 1403 | Contestación del usuario a demanda de cesación de actividades prohibidas | 2013 | `contestacion-usuario-demanda-cesacion-actividades-1403` |
| 1416 | Contestación al requerimiento de cesar actividades molestas | 2013 | `contestacion-requerimiento-cesar-actividades-molestas-1416` |

### Solicitudes y expedientes (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 104 | Prueba pericial anticipada en propiedad horizontal antes del proceso | 2022 | `prueba-pericial-anticipada-propiedad-horizontal-antes-104` |
| 1365 | Permiso para instalaciones provisionales en elementos comunes por obra privativa | 2013 | `permiso-instalaciones-provisionales-elementos-comunes-1365` |
| 1388 | Convocatoria de junta solicitada por comuneros al presidente | 2013 | `convocatoria-junta-solicitada-comuneros-presidente-1388` |
| 1406 | Solicitud de obras privadas en elementos comunes | 2013 | `solicitud-obras-privadas-elementos-comunes-1406` |
| 1412 | Solicitud de instalación individual de telecomunicaciones | 2013 | `solicitud-instalacion-individual-telecomunicaciones-1412` |
| 1413 | Solicitud de acceso a servicios comunes de telecomunicaciones | 2013 | `solicitud-acceso-servicios-comunes-telecomunicaciones-1413` |
| 1437 | Autorización de entrada en elemento privativo: solicitud | 2013 | `autorizacion-entrada-elemento-privativo-solicitud-1437` |

### Escritos de trámite (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 604 | Propietario pide al presidente que requiera a otro el cese de actividades prohibidas | 2016 | `propietario-pide-presidente-requiera-otro-cese-604` |
| 1104 | Otrosí: acreditación de pago de cantidades debidas por un comunero | 2013 | `otrosi-acreditacion-pago-cantidades-debidas-comunero-1104` |
| 1345 | Otrosí: cesación inmediata de la actividad | 2013 | `otrosi-cesacion-inmediata-actividad-1345` |
| 1347 | Declinatoria por mediación pactada entre comuneros y comunidad | 2013 | `declinatoria-mediacion-pactada-entre-comuneros-comunidad-1347` |
| 1394 | Comunero pide requerir a otro que derribe lo construido en elementos comunes | 2013 | `comunero-pide-requerir-otro-derribe-lo-construido-1394` |

### Actos y resoluciones de la Administración o del órgano judicial (22)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 101 | Certificado de estar al corriente de pago en la comunidad de propietarios | 2022 | `certificado-estar-corriente-pago-comunidad-propietarios-101` |
| 307 | Certificado del acuerdo de la junta de ejercitar la acción de cesación | 2020 | `certificado-acuerdo-junta-ejercitar-accion-cesacion-307` |
| 557 | Acta que acuerda desafectar elementos comunes para venderlos | 2016 | `acta-acuerda-desafectar-elementos-comunes-venderlos-557` |
| 605 | Requerimiento al presidente para convocar junta extraordinaria y acordar acciones judiciales | 2016 | `requerimiento-presidente-convocar-junta-extraordinaria-605` |
| 606 | Acta de la junta que aprueba la acción de cesación por actividades prohibidas | 2016 | `acta-junta-aprueba-accion-cesacion-actividades-606` |
| 823 | Permiso para entrar en un elemento privativo | 2015 | `permiso-entrar-elemento-privativo-823` |
| 1173 | Acta de constitución de comunidad de propietarios con subcomunidades | 2015 | `acta-constitucion-comunidad-propietarios-subcomunidades-1173` |
| 1174 | Citación de los comuneros a la reunión de la comunidad | 2015 | `citacion-comuneros-reunion-comunidad-1174` |
| 1175 | Acta de junta ordinaria o extraordinaria de propietarios | 2015 | `acta-junta-ordinaria-extraordinaria-propietarios-1175` |
| 1206 | Acta de junta constituida sin convocatoria previa | 2013 | `acta-junta-constituida-sin-convocatoria-previa-1206` |
| 1214 | Acta de aprobación de ascensor | 2013 | `acta-aprobacion-ascensor-1214` |
| 1219 | Acuerdo de junta autorizando al presidente a integrarse en un complejo inmobiliario privado | 2013 | `acuerdo-junta-autorizando-presidente-integrarse-complejo-1219` |
| 1223 | Acta de junta de comunidad agrupada con acuerdos de mayoría cualificada | 2013 | `acta-junta-comunidad-agrupada-acuerdos-mayoria-1223` |
| 1234 | Certificar el acta de la junta de propietarios | 2013 | `certificar-acta-junta-propietarios-1234` |
| 1379 | Notificación del acta a los propietarios presentes | 2013 | `notificacion-acta-propietarios-presentes-1379` |
| 1380 | Notificación de convocatoria de junta a un comunero | 2013 | `notificacion-convocatoria-junta-comunero-1380` |
| 1382 | Notificación del acta a los propietarios ausentes | 2013 | `notificacion-acta-propietarios-ausentes-1382` |
| 1387 | Acta de la junta constituyente | 2013 | `acta-junta-constituyente-1387` |
| 1408 | Autorización de acceso a servicios comunes de telecomunicaciones | 2013 | `autorizacion-acceso-servicios-comunes-telecomunicaciones-1408` |
| 1410 | Autorización de instalación individual de telecomunicaciones | 2013 | `autorizacion-instalacion-individual-telecomunicaciones-1410` |
| 1436 | Junta de comunidad agrupada: acta | 2013 | `junta-comunidad-agrupada-acta-1436` |
| 1441 | Acta de aprobación de obras y derrama extraordinaria | 2013 | `acta-aprobacion-obras-derrama-extraordinaria-1441` |

### Contratos, escrituras y documentos (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 56 | Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención | 2023 | `contrato-comunidad-instaladora-paneles-solares-gestion-56` |
| 69 | Cláusula informativa de videovigilancia en comunidades de propietarios | 2023 | `clausula-informativa-videovigilancia-comunidades-69` |
| 70 | Respuesta de la comunidad al derecho de acceso sobre su videovigilancia | 2023 | `respuesta-comunidad-derecho-acceso-sobre-videovigilancia-70` |
| 137 | Contrato de acceso a datos entre la comunidad y el administrador de fincas | 2021 | `contrato-acceso-datos-entre-comunidad-administrador-137` |
| 558 | Estatutos de la comunidad de monte vecinal en mano común | 2016 | `estatutos-comunidad-monte-vecinal-mano-comun-558` |
| 1376 | Estatutos de la comunidad (documento) | 2013 | `estatutos-comunidad-documento-1376` |

### Comunicaciones, requerimientos y reclamaciones (11)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 89 | Convocatoria de la junta general ordinaria de propietarios (Cataluña) | 2023 | `convocatoria-junta-general-ordinaria-propietarios-89` |
| 1176 | Aviso a la comunidad de obra en vivienda o local | 2015 | `aviso-comunidad-obra-vivienda-local-1176` |
| 1211 | Convocatoria de junta extraordinaria para instalar ascensor | 2013 | `convocatoria-junta-extraordinaria-instalar-ascensor-1211` |
| 1212 | Convocatoria de junta extraordinaria para reclamar cuotas atrasadas | 2013 | `convocatoria-junta-extraordinaria-reclamar-cuotas-1212` |
| 1215 | Convocatoria de junta extraordinaria sobre telecomunicaciones | 2013 | `convocatoria-junta-extraordinaria-sobre-1215` |
| 1229 | Convocatoria de junta extraordinaria para ejercitar la acción de cesación | 2013 | `convocatoria-junta-extraordinaria-ejercitar-accion-1229` |
| 1232 | Convocatoria de nueva junta por falta de quórum | 2013 | `convocatoria-nueva-junta-falta-quorum-1232` |
| 1375 | Convocar la junta constituyente por los propietarios | 2013 | `convocar-junta-constituyente-propietarios-1375` |
| 1377 | Convocatoria de la junta constituyente por el promotor | 2013 | `convocatoria-junta-constituyente-promotor-1377` |
| 1402 | Aviso de obras privadas en elementos comunes | 2013 | `aviso-obras-privadas-elementos-comunes-1402` |
| 1409 | Denegación de instalación individual de telecomunicaciones | 2013 | `denegacion-instalacion-individual-telecomunicaciones-1409` |

### Otros (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 825 | Constitución en comunidad de propietarios de un complejo inmobiliario privado | 2015 | `constitucion-comunidad-propietarios-complejo-825` |
| 1235 | Comunidad agrupada: estatutos | 2013 | `comunidad-agrupada-estatutos-1235` |
| 1433 | Constitución en agrupación de comunidades de propietarios | 2013 | `constitucion-agrupacion-comunidades-propietarios-1433` |
| 1434 | Constituirse en comunidad de propietarios | 2013 | `constituirse-comunidad-propietarios-1434` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

