---
name: partija-contador-partidor-documento-privado-galicia-567
description: "Redacta el escrito «Partija del contador-partidor en documento privado (Galicia)» (formulario 567 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Partija del contador-partidor en documento privado (Galicia)

> Formulario 0567 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] IMPORTE (49 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] ÓRGANO
- [ ] DESCRIBIR
- [ ] Otros 73 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ento del causante en la cuenta corriente»; «…ento del causante en la cuenta corriente»; «…euros. 3. 1000 acciones de la sociedad»; «…,»; «…euros. 4. Un reloj de oro»; «…5. La biblioteca de carácter profesional»; «…euros. 6. Un turismo»; «…O del Estado de fecha 31 de diciembre de»; «…uros. 7. Terreno sito en [LOCALIDAD], de»; «…e linda: Norte, con pista; Sur, calle de»; «…; Este, pista; y Oeste, finca»; «…, de la misma calle, de»; …

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0567 · Partija del contador-partidor en documento privado (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 114 campos de relleno marcados en blanco; 15 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

PARTIJA POR CONTADOR PARTIDOR EFECTUADA EN DOCUMENTO PRIVADO

En [LUGAR], a [DÍA] de [MES] de [AÑO].

INVENTARIO Y AVALUO (El/los contadores-partidores pueden efectuar por sí solo/s el inventario aun en el caso de que existan personas sujetas a patria potestad, tutela o curatela; cfr. art. 291 LDCG)

1. El saldo existente en la fecha de fallecimiento del causante en la cuenta corriente [COMPLETAR] que importaba [IMPORTE] euros.

2. El saldo existente en la fecha de fallecimiento del causante en la cuenta corriente [COMPLETAR] que importaba [IMPORTE] euros.

3. 1000 acciones de la sociedad [COMPLETAR], [COMPLETAR] que según su cotización el día del fallecimiento del causante tenían el valor de [IMPORTE] euros.

4. Un reloj de oro [COMPLETAR], valorado en [IMPORTE] euros.

5. La biblioteca de carácter profesional [COMPLETAR], valorada en un total de [IMPORTE] euros.

6. Un turismo [COMPLETAR], con un año de antigüedad, cuyo valor en la tasación inserta en el BO del Estado de fecha 31 de diciembre de [COMPLETAR] es de [IMPORTE] euros.

7. Terreno sito en [LOCALIDAD], de [COMPLETAR] metros cuadrados de superficie que linda: Norte, con pista; Sur, calle de [COMPLETAR]; Este, pista; y Oeste, finca [COMPLETAR], de la misma calle, de [COMPLETAR].

Referencia catastral. Tiene asignada referencia catastral número [NÚMERO], según resulta de la fotocopia que se incorpora a este documento.

Título. Compra en escritura pública otorgada ante el Notario [COMPLETAR] de [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR]; liquidado el impuesto correspondiente en la oficina liquidadora de [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR].

Referencia registral. Registro de la Propiedad de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Arrendamientos. No está arrendado.

Cargas. Está afecto a un crédito hipotecario concertado con [COMPLETAR] de [COMPLETAR], Urbana [COMPLETAR], del cual, en la fecha del fallecimiento del causante quedaba por amortizar la suma de [IMPORTE] euros.

8. Finca [COMPLETAR] del plano de Concentración Parcelaria de [COMPLETAR], con una extensión superficial de [COMPLETAR] áreas, y que linda: Norte, con arroyo; Sur, con camino; Este, con camino peatonal; y Oeste, con [COMPLETAR].

Referencia registral. Registro de la Propiedad de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Cargas. Está afecta a una servidumbre de paso permanente de tres metros de anchura a todo lo largo del lindero Este como predio sirviente, a favor de la finca con que linda por dicho aire, propiedad de Don [COMPLETAR] como predio dominante.

PARTICIÓN

Fallecimiento y testamento del causante.

El causante [ÓRGANO], falleció en [COMPLETAR], el [COMPLETAR] de [COMPLETAR] de [COMPLETAR] en estado de casado con [COMPLETAR] y de cuyo matrimonio nacieron y viven tres hijos llamados [COMPLETAR], [COMPLETAR] y [COMPLETAR].

A su fallecimiento, dicho causante había otorgado testamento único y válido ante el Notario de [COMPLETAR], con [COMPLETAR] de [COMPLETAR] de [COMPLETAR], y en el que disponía lo siguiente:

- La institución de únicos y universales herederos a sus tres citados hijos [COMPLETAR], [COMPLETAR] y [COMPLETAR].

- Un legado a favor de su esposa [COMPLETAR] en pleno dominio, de un tercio de su herencia.

- El nombramiento como, contadores-partidores de su herencia a [COMPLETAR] y [COMPLETAR].

Se une a este cuaderno certificación de la defunción del causante, copia autorizada de su testamento y certificación del Registro General de Actos de Última Voluntad.

Calidad de los bienes de la herencia.

Todos los bienes inventariados, a excepción de la finca que lo está al número 8 del inventario tienen la condición de bienes gananciales; sólo esta última es bien privativo del causante. El régimen económico matrimonial por que el matrimonio se rigió fue el de gananciales.

Deudas de la Sociedad.

Al fallecimiento del causante sólo existía y existe, como deuda de la sociedad de gananciales, la suma de [IMPORTE] euros que falta por amortizar del préstamo hipotecario que grava el terreno inventariado que se menciona en el número 7.

Liquidación de la Sociedad de Gananciales.

Conforme a lo anteriormente expuesto, se liquida la sociedad de gananciales en la forma siguiente:

Total caudal inventariado: [IMPORTE] euros.

Bajas: Bien privativo del marido: [IMPORTE] euros.

Deuda de la sociedad: [IMPORTE] euros.

Resto: [IMPORTE] euros.

De lo que corresponde la mitad a cada cónyuge, que supone [IMPORTE] euros.

Liquidación de la herencia.

Importe de la mitad de gananciales correspondiente al causante: [IMPORTE] euros.

Valor del bien privativo señalado en el número 8: [IMPORTE] euros.

Total del caudal hereditario: [IMPORTE] euros.

Cada tercio supone [IMPORTE] euros.

Corresponde percibir a la viuda [COMPLETAR]:

Por su mitad de gananciales: [IMPORTE] euros.

Por su legado del tercio de la herencia del causante: [IMPORTE] euros.

Total: [IMPORTE] euros.

Corresponde al heredero [IMPORTE]: euros.

Corresponde al heredero [IMPORTE]: euros.

Corresponde a la heredera [IMPORTE]: euros.

Adjudicaciones.

Cupo de la viuda [COMPLETAR]:

Ha de recibir un total de [IMPORTE] euros, por su mitad de gananciales y por el legado del tercio de la herencia del causante. Y para su pago se le adjudican en pleno dominio los siguientes bienes:

1. El inventariado al número 7 consistente en [DESCRIBIR]. Valorado en [IMPORTE] euros.

2. Los inventariados en el número 5: la biblioteca de carácter profesional valorada en un total de [IMPORTE] euros.

3. Metálico correspondiente a la cuenta corriente inventariada en el número 1 por el importe de [IMPORTE] euros.

Total adjudicado: [IMPORTE] euros. Igual a su haber por lo que queda totalmente pagada.

Cupo del hijo y heredero [COMPLETAR]:

Ha de recibir la suma de [IMPORTE] euros y para su pago se le adjudican en pleno dominio los siguiente bienes:

1. La finca inventariada al número 8 cuyo valor asciende a [IMPORTE] euros.

2. Metálico correspondiente a la cuenta corriente inventariada en el número 1 por el importe de [IMPORTE] euros.

Total adjudicado [IMPORTE] euros. Igual a su haber por lo que queda totalmente pagado.

Cupo del hijo y heredero [COMPLETAR]:

Ha de recibir la suma de [IMPORTE] euros y para su pago se le adjudican en pleno dominio los siguiente bienes:

1. Un turismo [COMPLETAR], con un año de antigüedad, cuyo valor en la tasación inserta en el BO del Estado de fecha 31 de diciembre de [COMPLETAR] es de [IMPORTE] euros.

2. Un reloj de oro [COMPLETAR], valorado en [IMPORTE] euros.

3. 1000 acciones de la sociedad [COMPLETAR], [COMPLETAR] que según su cotización el día del fallecimiento del causante tenían el valor de [IMPORTE] euros.

4. Metálico correspondiente a la cuenta corriente inventariada en el número 2 por el importe de [IMPORTE] euros.

Total adjudicado: [IMPORTE] euros. Igual a su haber por lo que queda totalmente pagado.

Cupo de la hija y heredera [COMPLETAR]:

Ha de recibir la suma de [IMPORTE] euros y para su pago se le adjudican en pleno dominio los siguiente bienes:

1. Metálico correspondiente a la cuenta corriente inventariada en el número 1 por el importe de [IMPORTE] euros.

2. Metálico correspondiente a la cuenta corriente inventariada en el número 2 por el importe de [IMPORTE] euros.

Total adjudicado [IMPORTE] euros. Igual a su haber por lo que queda totalmente pagada.

Comprobación:

Adjudicado a la viuda [IMPORTE]: euros.

Adjudicado al heredero [IMPORTE]: euros.

Adjudicado al heredero [IMPORTE]: euros.

Adjudicado a la heredera [IMPORTE]: euros.

Total adjudicado: [IMPORTE] euros.

Caudal hereditario: [IMPORTE] euros.

Resto: [IMPORTE] euros para el pago de la deuda inventariada en el número 7.

Por medio del presente documento queda entregado el legado del tercio de la herencia del causante correspondiente a la viuda [COMPLETAR].

DISPOSICIONES FINALES

1. No se conocen más bienes que los que han sido iados. Si en lo sucesivo apareciere alguno más, se distribuirá en la forma que, con los inventariados, se ha realizado.

2. A efectos fiscales se hace constar que el Impuesto de Sucesiones fue abonado por autoliquidación en la Oficina Liquidadora de esta ciudad, con [COMPLETAR] de [COMPLETAR] de [COMPLETAR] cartas de pago números [COMPLETAR] y [COMPLETAR].

3. La protocolización de las presentes operaciones particionales se realizará en el protocolo del Notario de esta ciudad [COMPLETAR] y lo que ello suponga, así como la expedición de copias, se abonará por los cuatro interesados con arreglo a la ley.

Con lo cual se dan por terminadas las presentes operaciones particionales que firmamos los contadores-partidores, y también la viuda del causante Doña [COMPLETAR] en prueba de su plena conformidad con la liquidación de la sociedad de gananciales incluida en el presente documento y en la que ha intervenido y que ratificará en el acta de protocolización anteriormente mencionada.

Firmas

========================================================================
