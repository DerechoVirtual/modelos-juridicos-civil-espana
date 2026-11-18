# Cobrar deudas: monitorio y cambiario · España

> Plugin de Claude Code `modelos-monitorio-espana` · **37 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para el proceso monitorio y el juicio cambiario: petición inicial, oposición del deudor (prescripción, pluspetición, cláusulas abusivas…), impugnación de la oposición y paso al declarativo, y oposición en el juicio cambiario.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 37 está al final):

- **Demandas, interposiciones y peticiones iniciales** (12). Por ejemplo: Petición inicial de monitorio contra la comunidad por honorarios del administrador; Demanda ordinaria contra el propietario tras oposición al monitorio; Oposición por abusividad al juicio cambiario: demanda.
- **Recursos e impugnaciones** (3). Por ejemplo: Impugnación de la oposición al monitorio; Apelación contra el auto que rechaza cláusulas abusivas en el monitorio; Impugnación de la oposición al monitorio por el trámite del verbal.
- **Contestaciones, oposiciones y alegaciones** (10). Por ejemplo: Oposición al monitorio por prescripción de la deuda; Oposición al monitorio por cláusula rebus sic stantibus; Oposición al monitorio por cláusulas abusivas.
- **Solicitudes y expedientes** (4). Por ejemplo: Inicio de expediente de título de crédito: cheque; Monitorio por deuda de alquiler impagado; Monitorio: petición.
- **Escritos de trámite** (5). Por ejemplo: Impugnación de la oposición al monitorio (financiación de vehículo); Petición inicial de monitorio por contrato de financiación de vehículos; Petición inicial de monitorio por contrato de renting.
- **Contratos, escrituras y documentos** (3). Por ejemplo: Modelo normalizado de reclamación monitoria; Modelo normalizado de reclamación monitoria de gastos comunes de comunidad; Monitorio simplificado con documentación mercantil habitual.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Oposición a un monitorio por prescripción de la deuda»
   - «Impugnación de la oposición al monitorio»
   - «Oposición a un juicio cambiario»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-monitorio-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-monitorio-espana:peticion-inicial-monitorio-contra-comunidad-honorarios-49`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 3.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-monitorio-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-monitorio-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-monitorio-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-monitorio-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (12)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 49 | Petición inicial de monitorio contra la comunidad por honorarios del administrador | 2023 | `peticion-inicial-monitorio-contra-comunidad-honorarios-49` |
| 555 | Demanda ordinaria contra el propietario tras oposición al monitorio | 2016 | `demanda-ordinaria-contra-propietario-tras-oposicion-555` |
| 637 | Oposición por abusividad al juicio cambiario: demanda | 2015 | `oposicion-abusividad-juicio-cambiario-demanda-637` |
| 876 | Monitorio con procurador y abogado | 2013 | `monitorio-procurador-abogado-876` |
| 880 | Monitorio con intereses moratorios ya liquidados | 2013 | `monitorio-intereses-moratorios-ya-liquidados-880` |
| 890 | Monitorio encabezado por el acreedor | 2013 | `monitorio-encabezado-acreedor-890` |
| 1035 | Oposición al juicio cambiario: demanda | 2013 | `oposicion-juicio-cambiario-demanda-1035` |
| 1240 | Monitorio tipo por rentas atrasadas | 2013 | `monitorio-tipo-rentas-atrasadas-1240` |
| 1332 | Monitorio de la comunidad por certificado de impago de gastos, presentado por el presidente | 2013 | `monitorio-comunidad-certificado-impago-gastos-presentado-1332` |
| 1370 | Monitorio por cuotas pendientes y gastos de requerimiento | 2013 | `monitorio-cuotas-pendientes-gastos-requerimiento-1370` |
| 1404 | Monitorio por derramas extraordinarias | 2013 | `monitorio-derramas-extraordinarias-1404` |
| 1405 | Monitorio de propiedad horizontal con procurador y abogado | 2013 | `monitorio-propiedad-horizontal-procurador-abogado-1405` |

### Recursos e impugnaciones (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 623 | Impugnación de la oposición al monitorio | 2016 | `impugnacion-oposicion-monitorio-623` |
| 635 | Apelación contra el auto que rechaza cláusulas abusivas en el monitorio | 2015 | `apelacion-contra-auto-rechaza-clausulas-abusivas-635` |
| 716 | Impugnación de la oposición al monitorio por el trámite del verbal | 2015 | `impugnacion-oposicion-monitorio-tramite-verbal-716` |

### Contestaciones, oposiciones y alegaciones (10)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 103 | Oposición al monitorio por prescripción de la deuda | 2022 | `oposicion-monitorio-prescripcion-deuda-103` |
| 180 | Oposición al monitorio por cláusula rebus sic stantibus | 2021 | `oposicion-monitorio-clausula-rebus-sic-stantibus-180` |
| 238 | Oposición al monitorio por cláusulas abusivas | 2020 | `oposicion-monitorio-clausulas-abusivas-238` |
| 636 | Alegaciones del deudor en el incidente de abusividad de oficio en el monitorio | 2015 | `alegaciones-deudor-incidente-abusividad-oficio-monitorio-636` |
| 719 | Alegaciones del demandado sobre cláusulas abusivas en el monitorio | 2015 | `alegaciones-demandado-sobre-clausulas-abusivas-monitorio-719` |
| 1025 | Oposición al monitorio con paso al juicio ordinario | 2013 | `oposicion-monitorio-paso-juicio-ordinario-1025` |
| 1326 | Oposición al monitorio por pluspetición | 2013 | `oposicion-monitorio-pluspeticion-1326` |
| 1327 | Oposición al monitorio | 2013 | `oposicion-monitorio-1327` |
| 1342 | Oposición al monitorio en propiedad horizontal | 2013 | `oposicion-monitorio-propiedad-horizontal-1342` |
| 1369 | Oposición al monitorio por pluspetitio | 2013 | `oposicion-monitorio-pluspetitio-1369` |

### Solicitudes y expedientes (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 275 | Inicio de expediente de título de crédito: cheque | 2020 | `inicio-expediente-titulo-credito-cheque-275` |
| 492 | Monitorio por deuda de alquiler impagado | 2017 | `monitorio-deuda-alquiler-impagado-492` |
| 711 | Inicio de expediente de título de crédito: letra de cambio | 2015 | `inicio-expediente-titulo-credito-letra-cambio-711` |
| 1254 | Monitorio: petición | 2013 | `monitorio-peticion-1254` |

### Escritos de trámite (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 76 | Impugnación de la oposición al monitorio (financiación de vehículo) | 2023 | `impugnacion-oposicion-monitorio-financiacion-vehiculo-76` |
| 77 | Petición inicial de monitorio por contrato de financiación de vehículos | 2023 | `peticion-inicial-monitorio-contrato-financiacion-77` |
| 78 | Petición inicial de monitorio por contrato de renting | 2023 | `peticion-inicial-monitorio-contrato-renting-78` |
| 511 | Impugnación de la oposición cambiaria | 2017 | `impugnacion-oposicion-cambiaria-511` |
| 1448 | Apelación contra el auto de inadmisión del monitorio | 2014 | `apelacion-contra-auto-inadmision-monitorio-1448` |

### Contratos, escrituras y documentos (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 610 | Modelo normalizado de reclamación monitoria | 2016 | `modelo-normalizado-reclamacion-monitoria-610` |
| 612 | Modelo normalizado de reclamación monitoria de gastos comunes de comunidad | 2016 | `modelo-normalizado-reclamacion-monitoria-gastos-comunes-612` |
| 852 | Monitorio simplificado con documentación mercantil habitual | 2013 | `monitorio-simplificado-documentacion-mercantil-habitual-852` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

