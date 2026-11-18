---
name: conciliacion-previa-reclamar-danos-accidente-circulacion-333
description: "Redacta el escrito «Conciliación previa para reclamar daños de un accidente de circulación» (formulario 333 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conciliación previa para reclamar daños de un accidente de circulación

> Formulario 0333 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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

- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA
- [ ] MARCA/MODELO (4 veces)
- [ ] MATRÍCULA (2 veces)
- [ ] CALLE (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DE Don»; «…nales, en nombre y representación de Don»; «…o, asistido del Letrado en ejercicio Don»; «…itud de acto de conciliación contra:Doña»; «…y contra la entidad aseguradora»; «… por la calle [CALLE] de la localidad de»; «…, conducido por su propietaria Doña»; «…, y asegurado por»; «…da SOLICITUD DE CONCILIACIÓN contra Doña»; «…y la Entidad Aseguradora»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 36 LEC
- arts. 2 y 140 LJV
- art. 10 LEC
- art. 7.1 LEC
- art. 141 LJV
- art. 140.1 LJV

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

### Formulario 0333 · Conciliación previa para reclamar daños de un accidente de circulación

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); 27 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud de conciliación sobre reclamación de indemnización derivada de hecho de la circulación, frente a conductor del vehículo y aseguradora, con representación y defensa técnica.

Formulario adaptado a la reforma procesal de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE Don [COMPLETAR], Procurador de los Tribunales, en nombre y representación de Don [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, asistido del Letrado en ejercicio Don [COMPLETAR], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:Que conforme con lo que disponen los arts. 140 y ss. LJV formulo solicitud de acto de conciliación contra:Doña [COMPLETAR], con domicilio en [LOCALIDAD] y contra la entidad aseguradora [COMPLETAR], con domicilio en [LOCALIDAD], a fin de que se avengan a reconocer los siguientes,

HECHOS

Primero.- El día [FECHA] mi representado conducía el vehículo de su propiedad marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], por la calle [CALLE] de la localidad de [COMPLETAR] cuando al llegar a la intersección con la calle [CALLE] el vehículo marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], conducido por su propietaria Doña [COMPLETAR], y asegurado por [COMPLETAR] irrumpió en el cruce sin respetar el ceda el paso que le obligaba y colisionó contra el vehículo conducido por mi representado.

Segundo.- A consecuencia de la colisión se produjeron daños en el vehículo de mi representado por importe de [IMPORTE] euros que fueron pagados en su totalidad por éste.

Tercero.- Que a consecuencia del accidente anteriormente relatado los requeridos de conciliación adeudan a mi representado el importe de los daños producidos al vehículo que ascienden a [IMPORTE] euros, más los intereses legales.A estos hechos, le son de aplicación los siguientesFUNDAMENTOS DE DERECHOI.- Jurisdicción y competencia.

Corresponde al orden jurisdiccional civil conocer del asunto en base a los arts. 36 LEC; 9 y 21.1 LOPJ.Corresponde la competencia al Tribunal al que nos dirigimos conforme a lo dispuesto en los arts. 2 y 140 LJV, debiendo conocer del acto de conciliación el Letrado de la Administración de Justicia.II.- Capacidad y legitimación.

La legitimación activa corresponde al solicitante en su calidad de titular de la relación jurídica u objeto litigioso conforme al art. 10 LEC, como acreedor.

La legitimación pasiva corresponde a los requeridos de conciliación en su calidad de titulares de la relación jurídica u objeto litigioso conforme al art. 10 LEC, como deudores.

Ambas partes tienen capacidad para ser parte conforme dispone el art. 6.1.1º LEC, respecto a la actora, y 6.1.1º ó 6.1.3º LEC respecto a la demandada.

Igualmente tiene la actora capacidad procesal según lo dispuesto en el art. 7.1 LEC.III.- Representación y defensa.

Comparece la actora representada por Procurador y asistida de Letrado, a pesar de no ser preceptiva su intervención, según el art. 141 LJV.IV.- Cuantía.

La cuantía de la presente solicitud de conciliación se fija en [IMPORTE] euros a los efectos de la competencia para conocer la misma según lo dispuesto en el art. 140.1 LJV.V.- Procedimiento.

Conforme a lo dispuesto en los arts. 139 y ss. LJV, se trata de un acto de jurisdicción voluntaria debiendo seguirse por estos trámites conforme sus normas específicas de tramitación.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL:Que teniendo por presentado este escrito con los documentos y copias que se acompañan, y a mí por comparecido y parte en la representación que ostento, se sirva admitirlo, tenga por formulada SOLICITUD DE CONCILIACIÓN contra Doña [COMPLETAR] y la Entidad Aseguradora [COMPLETAR]; y previos los trámites legales, se cite a los interesados señalando día y hora para acto de conciliación ante el Letrado de Administración de Justicia y, tras la celebración de dicho acto, dicte decreto haciendo constar la avenencia o, en su caso, que se intentó sin efecto o que se celebró sin avenencia, acordándose el archivo definitivo de las actuaciones y la expedición del testimonio del acta que ponga fin a la conciliación.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO]. Firma de Abogado/a

Firma de Procurador/a
