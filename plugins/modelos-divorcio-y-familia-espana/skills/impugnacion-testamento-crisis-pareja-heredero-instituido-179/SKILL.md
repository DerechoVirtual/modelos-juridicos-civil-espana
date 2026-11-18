---
name: impugnacion-testamento-crisis-pareja-heredero-instituido-179
description: "Redacta el escrito «Impugnación de testamento por crisis de pareja del heredero instituido (Cataluña)» (formulario 179 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de testamento por crisis de pareja del heredero instituido (Cataluña)

> Formulario 0179 del plugin **Familia** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] LOCALIDAD (5 veces)
- [ ] CALLE (4 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº DE DOCUMENTO (8 veces)
- [ ] COLEGIO
- [ ] Nº
- [ ] FECHA (6 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 27 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecina de»; «…E HEREDERO TESTAMENTARIO, del difunto D.»; «…, que habrá de ser citada en»; «…, calle [CALLE], nº [NÚMERO]; y D.»; «…e en los siguientes: HECHOS PRIMERO.- D.»; «… de vecindad civil catalana, falleció en»; «…dencia (acompaño como documentos números»; «…, ante el Notario de»; «…, ante el Notario de [COMPLETAR], D.»; «…(acompaño como documentos números»; «…numeración del juzgado de procedencia).]»; «…dante, formaban una unión de hecho desde»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 248 y 249.2 LEC
- art. 253.1 LEC
- art. 251 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 394.1 LEC
- Ley 10/2008

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

### Formulario 0179 · Impugnación de testamento por crisis de pareja del heredero instituido (Cataluña)

- Año del modelo: 2021
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 65 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 8 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de demanda de juicio ordinario instando la ineficacia sobrevenida de la institución de heredero por crisis matrimonial en Derecho civil especial de Cataluña.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecina de [COMPLETAR], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], en virtud de escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO]; bajo dirección del Letrado en ejercicio D./Dña. [NOMBRE Y APELLIDOS], del Iltre. Colegio de Abogados de [COLEGIO], y despacho abierto en [LOCALIDAD], calle [CALLE], nº [NÚMERO], comparezco y según sea procedente, DIGO:

Que por medio del presente escrito, vengo a ejercitar ACCIÓN DE NULIDAD DE INSTITUCIÓN DE HEREDERO TESTAMENTARIO, del difunto D. [COMPLETAR], debiendo ser tenida como parte demandada su ex-esposa Dña. [NOMBRE Y APELLIDOS], que habrá de ser citada en [COMPLETAR], calle [CALLE], nº [NÚMERO]; y D. [COMPLETAR], hermano de mi mandante.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Todo ello con base en los siguientes:

HECHOS

PRIMERO.- D. [COMPLETAR], de vecindad civil catalana, falleció en [COMPLETAR], el día [FECHA], como acredita la certificación de defunción expedida por el Registro Civil de [LOCALIDAD], que se acompaña como documento nº [Nº DE DOCUMENTO]

D. estuvo casado en únicas nupcias con la demandada, Dña. [NOMBRE Y APELLIDOS], con quien no tuvo descendencia (acompaño como documentos números [COMPLETAR] certificado de matrimonio y libro de familia).

SEGUNDO.- Constante el matrimonio con la demandada, D. otorgó testamento abierto, con fecha [FECHA], ante el Notario de [COMPLETAR], D. [COMPLETAR], en el cual, entre otras disposiciones, instituía como heredera a la demandada, Dña. [NOMBRE Y APELLIDOS] (acompaño como documentos números [COMPLETAR] certificado del registro de actos de últimas voluntades y copia simple del citado testamento).

TERCERO.- En fecha [FECHA], el causante D. [NOMBRE Y APELLIDOS] y la demandada Dña. pusieron fin a su convivencia matrimonial mediante divorcio instado de común acuerdo, dictándose sentencia de divorcio en fecha [FECHA] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], a cuya acreditación acompaño como documento nº [Nº DE DOCUMENTO] testimonio de la citada sentencia que consta inscrita en el certificado del Registro Civil aportado como documento nº [Nº DE DOCUMENTO]).

CUARTO.- El fallecido D. [NOMBRE Y APELLIDOS] y mi mandante, formaban una unión de hecho desde [COMPLETAR], fecha en que se inició su convivencia, si bien se inscribieron como pareja de hecho en el Registro de Uniones de Hecho de [COMPLETAR], en fecha [FECHA], con quien vino conviviendo hasta el momento de su fallecimiento, conforme se acredita con la aportación de certificados del Registro y de empadronamiento del causante y mis representada, como documentos números [COMPLETAR] y [COMPLETAR], respectivamente.

Pese a haber formalizado su situación como pareja de hecho y haber desaparecido totalmente los vínculos afectivos con su anterior pareja, lo cierto es que D. no modificó el testamento, sin duda por falta de previsión, al tratarse de una persona joven que falleció de forma súbita, pero que es indudable que su voluntad no podía ser en ningún caso la de mantener la institución de heredero cuando se había divorciado de la demandada y había roto cualquier vínculo afectivo con la misma, a la vez que había formado una nueva familia con mi representada.

Po todo ello, se interpone la presente demanda, para concretar la existencia de causa de revocación o ineficacia sobrevenida de la institución de heredero, conforme a lo preceptuado en el art. 422-13 CCC.

QUINTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A estos hechos le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1º LOPJ y 45 LEC.

Conforme a lo dispuesto en el art. 52.1.4º LEC es territorialmente competente el Tribunal de [LOCALIDAD] por ser el del lugar donde el finado D. [COMPLETAR], tuvo su último domicilio.

II.- CAPACIDAD Y LEGITIMACIÓN.

Tanto mi mandante D. [NOMBRE Y APELLIDOS],como los codemandados Dña. y D. [COMPLETAR], son personas físicas, mayores de edad, en pleno ejercicio de sus derechos civiles, por lo que tienen capacidad para ser parte y capacidad procesal ex arts. 6.1.1º y 7.1 LEC.

Está legitimada activamente mi mandante, en cuanto que pareja estable del causante, correspondiendo la legitimación pasiva a los herederos conforme al art. 422.13 CCC.

III.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, toda vez que el criterio de atribución preferente de la materia objeto del proceso resulta inaplicable, al carecer de especialidad típica la de éste, y cumplir entonces el criterio de cuantía, que rebasa con creces los quince mil euros.

IV.- CUANTÍA.

Cumpliendo lo prevenido en el art. 253.1 LEC, se hacemos constar que la cuantía de esta demanda es sólo relativamente determinable en [IMPORTE] euros, con arreglo a la regla 12ª, en relación con la regla 3ª.4º del art. 251 LEC, puesto se trata de pleito relativo a una herencia siendo que, en definitiva, se pretende por el derecho a adquirir ‘ope legis’ una cuota de una masa de bienes y derechos, de entre los que se identifica como prácticamente el que absorbe todo el valor de la herencia, la vivienda sita en [LOCALIDAD], calle [CALLE], nº [NÚMERO], que es finca [COMPLETAR], al folio [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR] de [COMPLETAR], inscrita en el Registro de la Propiedad de [COMPLETAR], y su valor catastral -utilizando el criterio subsidiario del art. 252.2ª LEC- asciende a [IMPORTE] euros.

Se aportan nota simple de la inscripción registral, en que aparece la titularidad, que es el documento nº [Nº DE DOCUMENTO] de la demanda.

V.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda por medio de Procurador/a de los Tribunales con poder para este pleito, que se conferirá ante el Letrado de la Administración de Justicia, y con dirección y firma de Letrado habilitado ante el Tribunal.

Asimismo se cumplen los requisitos formales del art. 399 LEC.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DE LA CUESTIÓN CONTROVERTIDA

Sobre la normativa aplicable

No hay discusión sobre la aplicación al caso de la Ley 10/2008, de 10 de julio, del Libro cuarto del Código Civil de Cataluña (CCC), relativo a las sucesiones, atendida la vecindad civil catalana por residencia del finado D. [NOMBRE Y APELLIDOS] (arts. 9.1 y 8; y 16.1.1.º CCiv) y la fecha de su fallecimiento (DT 1.ª Ley 10/2008); disponiendo el art. 422.13 CCC la ineficacia sobrevenida de la institución de heredero por crisis matrimonial o de convivencia.

Sobre la acción que se ejercita

Atendidos los hechos que han quedado expuestos y que esta parte acreditará cumplidamente en periodo probatorio, se insta la presente acción para que se declare ineficaz la institución de heredero a favor de la demandada Dña. [NOMBRE Y APELLIDOS], al amparo de lo dispuesto en el art. 422.13 CCC, precepto que establece que la institución de herederos que se haya ordenado a favor del cónyuge del causante deviene ineficaz si los cónyuges se separan de hecho o judicialmente o se divorcian, salvo si hubiera algún elemento que permita determinar que la voluntad del causante era mantenerla, sin que dicho elemento se desprenda en ningún momento del contexto del testamento acompañado como documento nº [Nº DE DOCUMENTO]

La previsión legal contenida en el art. 422.13 CCC parte de una presunción iuris tantum de la revocación de la institución de heredero por motivos sobrevenidos al acto de últimas voluntades, tales como la nulidad, la separación legal o el divorcio, que el legislador catalán introdujo por constatar, en la realidad social, la frecuencia de olvidos o descuidos, en caso de ruptura del matrimonio, de la modificación de los testamentos, lo cual se ha producido de forma evidente en este caso, lo que determina la ineficacia de la institución de heredero al no existir en el testamento ningún elemento que permita afirmar que el causante tuvo la voluntad de favorecer a su ex cónyuge.

Sobre la doctrina y la jurisprudencia aplicable

En interpretación de este precepto, citamos la STSJ Cataluña 1/2012 de 5 de enero de 2012, rec. 117/2011 y la SAP Barcelona 64/2019 de 30 de enero de 2019, rec. 403/2017, donde se recogen los requisitos para la estimación de la pretensión, que en este caso sin duda concurren.

Pues bien, en el presente caso concurren todos los requisitos, legal y jurisprudencialmente establecidos, para que concurra la causa de ineficacia de la disposición testamentaria del art. 422.13.1 CCC, toda vez que resulta indubitado el divorcio de la demandada con el finado D. [COMPLETAR], y se afirma la falta de voluntad de D. [COMPLETAR]. de mantener la institución de heredero cuando se divorció de la demandada.

En este sentido, el art. 422.13.1 CCC condiciona la ineficacia de la disposición testamentaria al mero hecho de la presentación de la demanda de separación, presumiéndose que, por la crisis matrimonial, la voluntad de los cónyuges manifestada en el testamento se transforma, y su intención, a partir de la crisis matrimonial o de convivencia, aún no habiendo revocación expresa, es que la disposición testamentaria quede sin efecto, no haciendo distinción la norma por razón del cónyuge que presente la demanda de separación, produciéndose la ineficacia por la mera presentación de la demanda por cualquiera de los cónyuges, no haciendo tampoco distinción la norma por razón de la situación económica en que pueda quedar el cónyuge superviviente, sea o no demandante, por la ineficacia de la disposición testamentaria, sin perjuicio de la prestación compensatoria del art. 233.14 CCC; de la prestación por alimentos del art. 237.2 CCC: o de los demás derechos que, en su caso, puedan asistir al cónyuge, contra sus hijos, o los herederos del premuerto (SAP Barcelona 598/2013 de 6 de noviembre de 2013, rec. 879/2012.

VIII.- COSTAS.

Se deben imponer a la parte demandada, por el criterio del vencimiento que establece para los declarativos en la instancia el art. 394.1 LEC.

Por lo expuesto,

AL TRIBUNAL SUPLICO

que, teniendo por presentado este escrito, se digne admitirlo, junto con sus documentos, y por comparecido a quien postula en la representación procesal que se le confiere haber por deducida, en calidad de parte actora, se entiendan conmigo todas las diligencias a partir de este momento, y tras la pertinente tramitación se dicte por ese Tribunal sentencia en la que se declare la ineficacia de la institución de heredero de Dña. [NOMBRE Y APELLIDOS] en el testamento otorgado por el causante D. [COMPLETAR], con todas las consecuencias legales inherentes a dicha declaración, todo ello con imposición de costas a la demandada si se opusiera a la demanda.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
