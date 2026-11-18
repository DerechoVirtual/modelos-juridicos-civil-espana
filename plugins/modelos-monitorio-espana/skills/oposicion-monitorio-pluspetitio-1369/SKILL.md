---
name: oposicion-monitorio-pluspetitio-1369
description: "Redacta el escrito «Oposición al monitorio por pluspetitio» (formulario 1369 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al monitorio por pluspetitio

> Formulario 1369 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] Nº (3 veces)
- [ ] NIF
- [ ] IMPORTE (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…do las cuotas ordinarias de los meses de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 815 de la LEC
- artículo 818 de la LEC
- Real Decreto 467/2006

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

### Formulario 1369 · Oposición al monitorio por pluspetitio

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 7 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio monitorio/

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Que mediante el presente escrito, dentro del plazo legalmente establecido por el artículo 815 de la Ley de Enjuiciamiento Civil (LEC), y según se expresa en providencia de fecha formulo oposición parcial por pluspetitio a la reclamación de cantidad presentada por la Comunidad de Propietarios de la C/ n.º [Nº], con CIF nº [NIF] procediendo a consignar en la cuenta del Tribunal la cantidad de [IMPORTE] euros como cifra realmente adeudada. Baso la oposición en los siguientes correlativos:

Cuando la presentación de escritos se realice por vía telemática:) Con carácter previo se hace constar que como documento nº 1 se presente el listado de documentos que acompañan a esta oposición.

En fecha se acordó por la Comunidad de Propietarios reunida en Junta realizar obras de reparación consistentes en y en el portal, consistentes en.

En ese momento, tal como consta en el acta que acompaño como documento n.º [Nº], voté en contra porque, tal como había expuesto, las obras debían extenderse también a la reparación de la fachada que sufre problemas de y que afectan a la estética de todo el edificio en general y del local del que soy propietario en particular.

Al votar en contra la mayoría de los vecinos a la ampliación de las obras, manifesté que me negaba a pagar las cuotas ordinarias como medida de presión ante una actuación que consideraba y considero necesaria, motivo por el cual el citado acuerdo está impugnado ante los Tribunales, tal como acredito con copia de la demanda que acompaño como documento n.º [Nº DE DOCUMENTO].

La Comunidad ha decidido a la vista de este juicio planteado por mi parte acelerar la reclamación de cuotas, y en este sentido he de manifestar que, al ser cierto que adeudo las cuotas ordinarias de los meses de [COMPLETAR], procedo a consignar tales cantidades en la cuenta de consignaciones y depósitos de Tribunal, al igual que la parte que me corresponde por arreglo del tejado de la cuota extraordinaria que se estableció en su día [FECHA].

La oposición se basa en que esta parte no está obligada a contribuir a los gastos derivados de elementos comunes que afecten únicamente a los vecinos que tienen acceso al portal. Al ser propietario de un local con entrada independiente no he de contribuir a liquidar el precio de la obra que se está realizando para reparar y redecorar el portal. Así se deduce de la escritura de propiedad del local que acompaño como documento n.º [Nº DE DOCUMENTO].

La deuda asciende a [IMPORTE] euros que abono en este momento, y no a la cantidad que se me reclama. En definitiva, esta parte no adeuda los euros que se le reclaman de más.

Por este motivo me veo obligado a oponerme parcialmente a la reclamación.

FUNDAMENTOS DE DERECHO

Conforme con el correlativo.

PRIMERO.— El artículo 818.1, párrafo final, de la LEC afirma que cuando la oposición se funda en pluspetitio se debe actuar conforme previene el artículo 21.2 del mismo texto legal, es decir, como si se tratara de un allanamiento parcial.

SEGUNDO.— El ingreso de la cantidad con la que esta parte muestra conformidad se lleva a cabo en la forma permitida por el Real Decreto 467/2006, de 21 de abril, que regula los depósitos y consignaciones judiciales en metálico, de efectos o valores.

TERCERO.— Se presenta este escrito de oposición dentro del plazo legalmente establecido por el artículo 815 de la LEC de 20 días.

CUARTO.— Tal como establece el artículo 818.1, párrafo 2.º, de la LEC este escrito no va firmado por Procurador y Abogado en atención a la cuantía reclamada que es inferior a 2.000 euros.

QUINTO.— Por la cuantía reclamada y según establece el artículo 818 de la LEC, presentado el escrito de oposición dentro de plazo, el Secretario dictará decreto dando por terminado el proceso monitorio, acordando seguir la tramitación del juicio verbal, dando traslado de este escrito a la actora.

PRIMERO.— Los estatutos de la Comunidad, norma que rige su funcionamiento, establecen en su punto n.º [Nº] que.

SEGUNDO.— El artículo 9.1.e) de la Ley de Propiedad Horizontal (LPH) obliga a los propietarios a contribuir a los gastos comunes según su cuota de participación. Dentro de la que le corresponde a mi representado no se incluyen los gastos de porque.

OTROSÍ DIGO: que de conformidad con lo establecido en el artículo 818.2 de la Ley de Enjuiciamiento Civil, interesa la convocatoria de las partes para la celebración de vista, siguiéndose los trámites previstos en los artículos 438 y siguientes de la LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por deducida la anterior solicitud, y tras los trámites oportunos convoque a las partes a la celebración de vista.

Es Justicia que pido en el miso lugar y fecha.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

RECUERDA QUE…

En los supuestos de pluspetitio exige la ley que, con respecto a la cantidad que sí se considere debida, se actúe según se regula el allanamiento parcial.

La oposición se formaliza mediante escrito firmado por Procurador y Abogado si su intervención es preceptiva por la cuantía, es decir, si la reclamación supera los 2.000 euros, y debe presentarse dentro de los veinte días siguientes a aquel en que se dio al demandado traslado de la providencia de requerimiento de pago. El escrito deberá contener de forma fundada y motivada las razones de oposición.

Tras la presentación de la oposición, si la cuantía reclamada supera los 15.000 euros, el demandante, si quiere continuar la tramitación, deberá formular demanda de juicio ordinario en el plazo de un mes, en caso contrario, se acordará el sobreseimiento de las actuaciones y, si la cifra fuera inferior, el Tribunal procede a seguir la tramitación conforme a lo previsto para el convocar a juicio verbal.

Cuando se deba realizar la presentación de escritos por vía telemática hay que tener en cuenta las siguientes consideraciones:

•Como documento nº 1 se presentará el listado de los documentos que se aporten con cualquier escrito de partes (especialmente demanda y contestación), siempre que se trate de más de un documento. Lo documentos se presentan escaneados y con el escrito principal.

• La demanda debe ir firmada por vía telemática por el letrado, además de por el procurador.

• Debe identificarse a las partes con sus DNI porque el procurador al presentar el escrito debe rellenar obligatoriamente los campos relativos a esos datos.

• La presentación telemática de la demanda determina una reducción del 10 % del importe de la tasa judicial.

========================================================================
