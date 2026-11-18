---
name: oposicion-ejecucion-titulo-no-judicial-947
description: "Redacta el escrito «Oposición a la ejecución de título no judicial» (formulario 947 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la ejecución de título no judicial

> Formulario 0947 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] NÚMERO (3 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…, PLAZA N.º»; «…roceda en derecho DIGO: Que con fecha de»; «…Silencia el ejecutante en su demanda que»; «… que consta la efectividad, con fecha de»; «…ineraria y como mínimo hasta la fecha de»; «…resente asunto concurre la circunstancia»; «…eridad y mala fe al instar una ejecución»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 557 de la LEC
- artículo 560 de la LEC

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

### Formulario 0947 · Oposición a la ejecución de título no judicial

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio ejecutivo n.º [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito con la escritura de poder que acompaño para acreditar mi representación, ante el Tribunal comparezco en los autos referenciados bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se ha notificado a mi representado el auto de fecha [FECHA] mediante el que se acuerda despachar contra mi mandante ejecución por el principal de [IMPORTE] euros más otros [IMPORTE] euros para intereses, gastos y costas, con simultáneo traslado de la demanda ejecutiva formulada por la representación procesal del actor D./Dña. [NOMBRE Y APELLIDOS] Dentro de plazo legal y al amparo de lo dispuesto en el art. 557 en relación con el art. 556 ambos de la LEC, formalizo mediante el presente escrito OPOSICIÓN A LA EJECUCIÓN despachada, basando mi oposición a la demanda ejecutiva deducida de contrario en los siguientes

HECHOS

Silencia el ejecutante en su demanda que [COMPLETAR] (rebatir el relato fáctico de la demanda ejecutiva, señalando los hechos que justifiquen la invocación de algunas de las causas de oposición detalladas en el inciso 1 del art. 557 de la LEC, y apoyar documentalmente el relato alternativo,

(Opciones):

1. Mi poderdante ha hecho efectiva la cantidad a cuyo pago le condenó la sentencia ejecutada, tal y como se desprende de la certificación bancaria de transferencia a la cuenta corriente del demandante —designada como domicilio de pagos— que acompaño reseñada como documento n.º [NÚMERO], en la que consta la efectividad, con fecha de [COMPLETAR], del ingreso bancario y la reseña de su aplicabilidad al pago de la suma objeto de condena en el presente procedimiento.

2. Las partes han alcanzado un acuerdo, documentado en escritura pública cuya primera copia acompaño reseñada como documento n.º [NÚMERO], mediante el que el actor se comprometía a mantener paralizada la ejecución en tanto el demandado obtenía la financiación precisa para hacer frente a la condena dineraria y como mínimo hasta la fecha de [COMPLETAR], con las demás condiciones que constan en el documento adjunto.

 (Rebatir o puntualizar los hechos aducidos en la demanda ejecutiva y aportar documentos que apoyen el relato fáctico alternativo).

A los hechos antecedentes resultan de aplicación, de manera correlativa a los invocados en la demanda ejecutiva, los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Conforme con el correlativo.

Legitimación

Conforme con el correlativo.

Requisitos procesales y trámite

• Se presenta este escrito de oposición a la ejecución dentro de los diez días siguientes a la notificación del auto por el que se acuerda el despacho de la ejecución (art. 557 en relación con art. 556.1 ambos de la LEC).

• Debe seguirse para sustanciar esta oposición el trámite previsto en los arts. 560 y ss. de la LEC.

• Art. 557.2: Si se formula la oposición prevista en el apartado anterior se suspenderá el curso de la ejecución.

Causas de oposición

El art. 557 de la LEC determina que puede oponerse a la ejecución despachada: 1. Pago, que pueda acreditarse documentalmente; 2. compensación de crédito líquido que se derive de documento ejecutivo; 3. pluspetición o exceso de computación a metálico de deudas en especie; 4. prescripción o caducidad; 5. Quita, espera o pacto o promesa de no pedir que conste documentalmente; 6. Transacción que conste en documento público; 7. que el título contenga cláusula abusiva.

En el presente asunto concurre la circunstancia [COMPLETAR] (desarrollar y acreditar encaje en uno de los supuestos legales anteriores).

Costas

Art. 561.2 de la LEC: Al rechazarse la ejecución, las costas deberán ser impuestas al ejecutante, que litiga con temeridad y mala fe al instar una ejecución [COMPLETAR] (para el cobro de una cantidad ya pagada; en contra de un convenio reflejado en documento público, …).

Por lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito con los documentos que acompaño, se sirva admitirlo, teniendo por formulada en tiempo y forma oposición a la ejecución despachada y por opuesta a esta parte a la demanda ejecutiva formulada por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS], ordenando lo necesario para el impulso del trámite procedimental pertinente con suspensión por el Letrado de la Administración de Justicia del curso de la ejecución, para en definitiva dictar auto mediante el que se estime la causa de oposición aducida y se declare no haber lugar a que prosiga la ejecución acordada (en su caso: y se alcen los embargos, trabas y medidas de garantía adoptados; o: se reintegre al ejecutado a la situación anterior al despacho de la ejecución) con expresa imposición de costas al ejecutante D./Dña. [NOMBRE Y APELLIDOS]

Por ser justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(en su caso)

OTROSÍ DIGO: Que según permite el artículo 560 de la LEC, esta parte interesa la celebración de vista por no poderse resolver la controversia meramente con los documentos aportados.

NUEVAMENTE SUPLICO: que se acuerde la celebración de vista que seguirá el cauce del juicio verbal por ser justicia que pido en mismo lugar y fecha.

========================================================================
