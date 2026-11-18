---
name: documento-extincion-pareja-estable-no-casada-aragon-348
description: "Redacta el escrito «Documento de extinción de pareja estable no casada (Aragón)» (formulario 348 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Documento de extinción de pareja estable no casada (Aragón)

> Formulario 0348 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] NIF (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº (2 veces)
- [ ] CALLE (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, a [FECHA]. REUNIDOS De una parte, Don»; «…Y de la otra, Doña»; «…critura notarial con numero de protocolo»; «…años, y que tienen»; «…de»; «…scrita en el Registro de la Propiedad de»; «…con numero de finca»; «…se atribuye a Doña»; «…cuidado de los menores por parte de Doña»; «…las partes acuerdan que Don»; «…número [NÚMERO] con una superficie de»; «…metros cuadrados. Cuota de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 6/1999

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

### Formulario 0348 · Documento de extinción de pareja estable no casada (Aragón)

- Año del modelo: 2019
- Revisión 17-11-2026: restos de formato retirados; 1 rangos de artículos despegados («25 a31» → «25 a 31»); notas del formulario agrupadas al final (1); 35 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escritura en la que dos personas que tienen la condición legal de pareja estable o unión de hecho acuerdan disolver o extinguir la relación de pareja, conforme al Derecho foral de Aragón.

En [LUGAR], a [FECHA].

REUNIDOS

De una parte, Don [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD], vecindad civil aragonesa, y NIF número [NIF]

Y de la otra, Doña [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD], vecindad civil aragonesa, y NIF número [NIF]

INTERVIENEN

Ambos en su propio nombre y derecho, teniendo la capacidad legal necesaria para otorgar el presente documento y, a tal efecto,

EXPONEN

I.- Que el pasado [FECHA] se constituyeron en pareja de hecho, mediante escritura notarial con numero de protocolo [COMPLETAR], otorgada ante el Notario D. [NOMBRE Y APELLIDOS] y posterior trámite de inscripción en el Registro de parejas estables no casadas de la Comunidad Autónoma de Aragón, tal y como figura en el certificado que se acompaña.

II.- Que mediante dicha inscripción se constituyeron voluntariamente en pareja de hecho, tal y como regula el Código de Derecho foral de Aragón, aprobado por Decreto Legislativo 1/2011 de 22 de marzo, y manifestaron que no se hallaban incursos en ninguno de los impedimentos recogidos en la misma norma.

III.- Que llevan conviviendo [Nº] años, y que tienen [COMPLETAR] hijos comunes, siendo uno de ellos menor de edad.

IV.- Que ambas partes deciden extinguir de común acuerdo su pareja de hecho, y pactan, para ello, las siguientes (1)

ESTIPULACIONES

PRIMERA. Vivienda familiar

El uso de la vivienda familiar, sita en la calle [CALLE] de [COMPLETAR] e inscrita en el Registro de la Propiedad de [COMPLETAR] con numero de finca [COMPLETAR] se atribuye a Doña [COMPLETAR] junto con el ajuar, habida cuenta de que se le atribuye la custodia del hijo común menor, hasta que éste cumpla la mayoría de edad.

SEGUNDA. Pensión

Habida cuenta del desempeño de las labores del hogar y cuidado de los menores por parte de Doña [COMPLETAR] las partes acuerdan que Don [COMPLETAR], le abone una pensión periódica de [IMPORTE] euros/mes, por un plazo de [Nº] años.

TERCERA. Liquidación de patrimonio

Los comparecientes han adquirido durante su convivencia, un inmueble sito en [LOCALIDAD], calle [CALLE] número [NÚMERO] con una superficie de [COMPLETAR] metros cuadrados.

Cuota de [COMPLETAR] % en el valor del bloque donde está ubicado la citada vivienda y elementos comunes.

Inscripción: Está inscrita en el Registro de la Propiedad número [NÚMERO] de [COMPLETAR] en el tomo [COMPLETAR] libro [COMPLETAR] folio [COMPLETAR] finca [COMPLETAR]

Referencia catastral: según consta en la referencia del último recibo del Impuestos sobre bienes Inmuebles.

Cargas: La referida finca se encuentra libre de cargas y gravámenes.

Valor: [IMPORTE] euros.

Mediante la presente escritura deciden adjudicar el inmueble a Don/Doña [NOMBRE Y APELLIDOS] a cambio de compensar económicamente a Don/Doña [NOMBRE Y APELLIDOS] mediante el pago de [IMPORTE] euros, fijados en dictamen pericial por [COMPLETAR] al objeto de extinguir el condominio referido.

Firma del conviviente	Firma de la conviviente

NOTAS DEL FORMULARIO

(1) Las parejas estables no casadas se regulan en el Título VI del Libro II del Decreto Legislativo 1/2011, de 22 de marzo, del Gobierno de Aragón, por el que se aprueba, con el título de "Código del Derecho Foral de Aragón", el Texto Refundido de las Leyes civiles aragonesas (en adelante, CDFA), arts. 303 a 315 CDFA, aplicables desde el 6 de octubre de 1999, fecha de entrada en vigor de la Ley 6/1999, de 26 de marzo, relativa a Parejas estables no casadas, cuyas normas abroga. Se regulan, entre otros, los siguientes aspectos:

1.- Efectos económicos si cesa la convivencia por causa distinta de la muerte: Derecho a una pensión si se produce desigualdad y un miembro ha contribuido económicamente o con su trabajo a la adquisición, conservación o mejora de cualquiera de los bienes comunes o privativos del otro o cuando sin retribución o con retribución insuficiente se ha dedicado al hogar o a los hijos comunes o del otro conviviente o ha trabajado para éste.

2.- Otros efectos: La extinción de la pareja estable no casada implica la revocación de los poderes que cualquiera de los miembros haya otorgado a favor del otro.

3. Causas de extinción: a) Por la muerte o declaración de fallecimiento de uno de los integrantes; b) Por mutuo acuerdo. c) Por decisión unilateral; d) por separación de hecho de más de un año; e) Por matrimonio uno de sus miembros.
