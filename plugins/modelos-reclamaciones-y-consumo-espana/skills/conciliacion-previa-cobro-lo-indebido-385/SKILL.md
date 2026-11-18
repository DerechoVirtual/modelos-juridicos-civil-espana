---
name: conciliacion-previa-cobro-lo-indebido-385
description: "Redacta el escrito «Conciliación previa por cobro de lo indebido» (formulario 385 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conciliación previa por cobro de lo indebido

> Formulario 0385 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (5 veces)
- [ ] COLEGIO (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE DOCUMENTO
- [ ] ACTO O RESOLUCIÓN (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] NÚMERO
- [ ] PLAZO
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Al Juez/a de Paz de»; «…D./Doña»; «…, y bajo la dirección letrada de D/Doña»; «…mo mejor proceda en Derecho DICE D./Doña»; «…los siguientes, HECHOS PRIMERO.- D./Doña»; «…e venta de productos de segunda mano con»; «… concertando la adquisición del producto»; «…ante las conversaciones mantenidas entre»; «…y»; «…pacta un precio de compra que asciende a»; «…eembolso realizado como documentos nums.»; «…o se corresponde al producto adquirido a»; …

## Elecciones que hay que hacer

- NIF / CIF
- Letrado de la Administración de Justicia / Juez/a de Paz
- Juez/a de Paz / Letrado de la Administración de Justicia del Tribunal de Instancia

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosa…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 2 y 140 de la Ley 15/2015
- artículo 10 LEC
- artículo 7.1 LEC
- artículo 141 Ley 15/2015
- artículo 140 Ley 15/2015
- art. 231 de la LEC

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

### Formulario 0385 · Conciliación previa por cobro de lo indebido

- Año del modelo: 2019
- Revisión 17-11-2026: 5 desplegables convertidos en elección en blanco; 3 bloques de alternativas señalados; 1 párrafos opcionales señalados; 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

A la Sección Civil del Tribunal de Instancia que por turno de reparto corresponda de [LOCALIDAD]

Al Juez/a de Paz de [COMPLETAR]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D./Doña [COMPLETAR], Procurador/a de los Tribunales, Coleg. del Ilustre Colegio de Procuradores de [COLEGIO], actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección letrada de D/Doña [COMPLETAR], Letrado/a del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparece y como mejor proceda en Derecho DICE

D./Doña [COMPLETAR], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF], ante el Tribunal comparece y como mejor proceda en Derecho DICE

Que por medio del presente escrito vengo a formular Seleccione una u otra opción en nombre de mi mandante/en mi propio nombre SOLICITUD DE CONCILIACIÓN frente a [ACTO O RESOLUCIÓN], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF], al amparo de lo dispuesto en los artículos 140 y ss de la L 15/2015, de 2 de julio, de Jurisdicción Voluntaria, a fin de que se reconozcan los siguientes,

HECHOS

PRIMERO.- D./Doña [COMPLETAR] contactó a través de una página web de venta de productos de segunda mano con [COMPLETAR], concertando la adquisición del producto [COMPLETAR] por importe [IMPORTE]. Se acredita tal extremo mediante las conversaciones mantenidas entre [COMPLETAR] y [COMPLETAR] que se acompañan como documento núm. [NÚMERO].

SEGUNDO.- Tras diversas conversaciones, se pacta un precio de compra que asciende a [COMPLETAR] y que ha de ser hecho efectivo por mi mandante en el plazo de [PLAZO] a fin de formalizar la reserva del producto. Dicho producto se enviará con los gastos pagados al domicilio de mi mandante en el plazo de días una vez recibida en la cuenta indicada el abono realizado por mi mandante.

TERCERO.- Con fecha [FECHA] se realiza la transferencia indicada por importe de [IMPORTE] y en el plazo de [Nº] días, se remite a su domicilio el producto adquirido. Sin embargo, para poder recoger el producto, ha de hacerse el pago contrareembolso, motivo por el cual, en creencia errónea de mi mandante de otro producto adquirido a proveedor distinto, realiza el pago contrareembolso. Se acredita tal extremo mediante la orden de transferencia efectuada y el justificante del pago contrareembolso realizado como documentos nums. [COMPLETAR].

CUARTO.- Al comprobar el producto, mi mandante se da cuenta que el mismo se corresponde al producto adquirido a [COMPLETAR], por el cual ya se realizó el pago mediante transferencia bancaria.

QUINTO.- En consecuencia, se avenga a restituir al solicitante la cantidad de [IMPORTE] en concepto de COBRO INDEBIDO.

A estos hechos, le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Primero.- Jurisdicción y competencia.

Corresponde al orden jurisdiccional civil conocer del asunto en base al art. 36 Ley de Enjuiciamiento Civil y artículos 9, 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ).

Corresponde la competencia al Tribunal al que nos dirigimos conforme a lo dispuesto en los artículos 2 y 140 de la Ley 15/2015, de Jurisdicción voluntaria, en relación con lo dispuesto en el art. 85.1º LOPJ.

Deberá conocer el [ELEGIR: Letrado de la Administración de Justicia / Juez/a de Paz].

Segundo.- Capacidad y legitimación

a. Activa: Corresponde al solicitante en su calidad titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC.

b. Pasiva: Corresponde al requerido en su calidad titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC. Ambas partes tienen capacidad para ser parte conforme dispone el artículo 6.1.1º LEC, respecto a la actora, y 6.1.1º o 6.1.3 LEC respecto a la demandada.

Igualmente tiene la actora capacidad procesal según lo dispuesto en el artículo 7.1 LEC.

Tercero.- Representación y defensa

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Comparece la actora representada por Procurador y asistida de Letrado, a pesar de no ser preceptiva su intervención, según el artículo 141 de la L15/2015.

Comparece la parte solicitante por si mismo, dado que al amparo de lo dispuesto en el apartado 3 del artículo 141 Ley 15/2015, no es preceptiva su intervención.

Cuarto.- Cuantía

La cuantía de la presente solicitud se fija en [COMPLETAR] a los efectos del la competencia para conocer el mismo según lo dispuesto en el apartado 1 del artículo 140 Ley 15/2015.

Quinto.- Procedimiento

Conforme a lo dispuesto en los artículos 139 y ss Ley 15/2015, se trata de un acto de jurisdicción voluntaria debiendo seguirse por estos trámites conforme sus normas específicas de tramitación.

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con los documentos y copias que se acompañan, y a mí por comparecido y parte en la representación que ostento, se sirva admitirlo, tenga por formulada SOLICITUD DE CONCILIACIÓN en concepto de Cobro de lo indebido por importe de frente a [ACTO O RESOLUCIÓN], con domicilio en [LOCALIDAD] y
NIF
CIF
  y previos los trámites legales, se cite a los interesados señalando día y hora para acto de conciliación ante el [ELEGIR: Juez/a de Paz / Letrado de la Administración de Justicia del Tribunal de Instancia].

[OPCIONAL — incluir si procede]

OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC, y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICOAL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
