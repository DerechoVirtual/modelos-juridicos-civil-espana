---
name: contestacion-desahucio-fin-plazo-arrendamiento-uso-459
description: "Redacta el escrito «Contestación al desahucio por fin de plazo en arrendamiento de uso distinto de vivienda» (formulario 459 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación al desahucio por fin de plazo en arrendamiento de uso distinto de vivienda

> Formulario 0459 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº DE DOCUMENTO
- [ ] SEDE
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE (2 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don/Dª»; «…representación que ostento de la entidad»; «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 1566 y 1581 Código Civil
- arts. 438.8 y 438.10 LEC
- art. 1566 CC
- art. 1581 CC
- art. 394 de la LEC

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, MASC si es una demanda civil).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0459 · Contestación al desahucio por fin de plazo en arrendamiento de uso distinto de vivienda

- Año del modelo: 2017
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 9 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA, IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal número

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don/Dª [COMPLETAR], Procurador de los Tribunales, en la representación que ostento de la entidad [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en el juicio verbal de desahucio arriba expresado comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose dado traslado a esta parte de la demanda formulada por D en juicio verbal de desahucio por expiración del término convencional, siguiendo instrucciones de mi poderdante por medio del presente escrito y en nombre del mismo formulo en tiempo y forma CONTESTACIÓN A LA DEMANDA, oponiéndome a la misma en base a los siguientes

HECHOS

PRIMERO.- Se niegan todos los hechos expuestos en la demanda a excepción de los que se vean aceptados en la presente contestación.

En cuanto al hecho primero de la demanda, se acepta que se concertó contrato de arrendamiento para uso distinto al de vivienda por un periodo cinco años en fecha [FECHA] sobre el local de negocio sito en [LOCALIDAD], respecto de la cual viene abonándose una renta anual de [IMPORTE] euros, tal como consta en la cláusula segunda del contrato, pero se niega que haya expirado el término contractual al haberse producido la tácita reconducción.

Así, según se estipuló en la cláusula tercera, el arrendamiento de la vivienda se pactó por un periodo de cinco años por lo que finalizaba el día [FECHA] Al no haberse recibido comunicación alguna del arrendador pasados quince días el contrato se reconducido de modo tácito conforme a lo dispuesto en los arts. 1566 y 1581 Código Civil, por un año.

En efecto, el alquiler pactado fue anual, de modo que el contrato se recondujo por un año, no pudiendo pretenderse por la demandante la resolución del mismo al estar vigente hasta tanto no transcurra el término de la reconducción.

SEGUNDO.- Negamos asimismo los hechos expresados en el correlativo de la demanda.

Mi representado ha seguido en posesión del local con aquiescencia del arrendador, quien ha percibido las rentas sin hacer objeción alguna, tal como se acredita por los resguardos de transferencia bancaria que se acompañan como documentos número y en ningún momento ha comunicado su oposición al disfrute hasta el momento en que ha ejercitado de forma indebida la acción de desahucio en este proceso.

Por este motivo, la acción ejercitada contraviene los actos propios pues, como recuerda la STS, Sala 1ª, 7 diciembre 2010, rec. 258/2007, este principio tiene aplicación cuando, como en este caso, lo realizado se opone a los actos que previamente han creado una situación o relación de Derecho que no podía ser alterada unilateralmente por quien se hallaba obligado a respetarla. En este caso, el arrendador ha consentido el disfrute de la finca vencido el arrendamiento y no ha comunicado a mi representado su voluntad de dar por terminado el contrato, por lo que se produjo la tácita reconducción, todo lo cual nos lleva a solicitar la desestimación de la demanda al estar vigente el contrato de arrendamiento sobre el local.

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Se acepta la competencia y la tramitación de la causa por los tramites del juicio verbal, aceptando asimismo la cuantía de [IMPORTE] euros y asumiendo las alegaciones en este sentido vertidas en el escrito de demanda.

SEGUNDO.- Procedimiento.- Conforme con la tramitación por el cauce verbal en atención a objeto de este juicio. A los efectos de los arts. 438.8 y 438.10 LEC, esta parte interesa la celebración de vista [NOTA DE REVISIÓN: Tras la LO 1/2025 el art. 438.4 regula otra cosa (art. 250.1.7.º); la prueba se propone en 5 días (438.8) y el tribunal decide por auto si hay vista (438.10). Fuente: LEC art. 438.8-10 (redacc. LO 1/2025, BOE-A-2025-76).] para la práctica de las pruebas necesarias para el esclarecimiento de los hechos (o en su caso, no interesa la celebración de vista por entender que el conflicto es meramente jurídico, debiendo procederse a dictar sentencia sin más trámites, admitiendo como prueba los documentos presentados con esta contestación).

TERCERO.- Fondo de la reclamación.- Son de aplicación el art. 1566 CC dispone que "Si al terminar el contrato, permanece el arrendatario disfrutando quince días de la cosa arrendada con aquiescencia del arrendador, se entiende que hay tácita reconducción por el tiempo que establecen los artículos 1.577 y 1.581, a menos que haya precedido requerimiento", así como el art. 1581 CC dispone que "Si no se hubiese fijado plazo al arrendamiento, se entiende hecho por años cuando se ha fijado un alquiler anual, por meses cuando es mensual, por días cuando es diario".

CUARTO.- Costas.- Es de aplicación del art. 394 de la LEC, por lo que deberán imponerse a la parte actora al desestimarse íntegramente sus pretensiones

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y sus copias y lo admita a trámite a fin de que, tras los trámites legales incluida la celebración de vista que dejamos expresamente interesada, en su día dicte sentencia desestimando íntegramente la demanda con expresa imposición de costas a la parte actora.

 a [DÍA] de [MES] de [AÑO]

Firma Abogado y Procurador

========================================================================
