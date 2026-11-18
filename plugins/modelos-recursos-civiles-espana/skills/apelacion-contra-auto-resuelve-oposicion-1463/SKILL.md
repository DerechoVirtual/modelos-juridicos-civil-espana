---
name: apelacion-contra-auto-resuelve-oposicion-1463
description: "Redacta el escrito «Apelación contra el auto que resuelve la oposición» (formulario 1463 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto que resuelve la oposición

> Formulario 1463 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA (5 veces)
- [ ] IMPORTE
- [ ] LUGAR

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 561.4 LEC
- art. 458 LEC
- art. 557.1 LEC
- art. 326.1 LEC
- art. 561.3 LEC

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

### Formulario 1463 · Apelación contra el auto que resuelve la oposición

- Año del modelo: 2014
- Revisión 17-11-2026: 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
ALEGACIONES
SUPLICO A LA SALA
Firmas

Recurso de apelación contra el auto que resuelve la oposición por motivos de fondo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], como tengo debidamente acreditado en autos de proceso de ejecución n.º [Nº DE PROCEDIMIENTO]/[AÑO], ante la Sala comparezco y DIGO:

I.-Que con fecha [FECHA] ha sido notificado a esta parte auto de fecha [FECHA] cuya parte dispositiva es del tenor literal siguiente:

"Que desestimado la oposición a la ejecución por motivos de fondo interpuesta por D./Dña. [NOMBRE Y APELLIDOS], debo declarar y declaro procedente que la ejecución siga adelante por las cantidades establecidas en el auto despachando la ejecución, con expresa imposición de costas a la parte ejecutada".

II.-Que de acuerdo con lo establecido en el art. 561.4 LEC "contra el auto que resuelva la oposición podrá interponerse recurso de apelación, que no suspenderá el curso de la ejecución si la resolución recurrida fuera desestimatoria de la oposición".

III.-Que entendiendo que dicha resolución no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN impugnando el pronunciamiento desestimatorio de la oposición a la ejecución ordenando continuar adelante la ejecución despachada.

IV.-Que cumpliendo la exigencia del art. 458 LEC, se hace constar que la base impugnatoria del presente recurso descansa en las siguientes:

ALEGACIONES

ÚNICA.-

Infracción del art. 557.1 LEC.

El art. 557.1 LEC establece que "cuando se despache ejecución por los títulos previstos en los números 4.º, 5.º, 6.º y 7.º, así como por otros documentos con fuerza ejecutiva a que se refiere el número 9.º del apartado 2 del artículo 517, el ejecutado sólo podrá oponerse a ella, en el tiempo y en la forma prevista en el artículo anterior, si se funda en alguna de las causas siguientes: 1.ª Pago, que pueda acreditar documentalmente".

Pues bien, el pasado día [FECHA] esta parte, después de presentada la demanda, pero antes de que se le notificara el despacho de la ejecución, efectuó transferencia bancaria por importe de [IMPORTE] euros, que cubre todas las cantidades reclamadas, como se acreditó tempestivamente en el momento de formular oposición a la ejecución despachada acompañándose resguardo de la mencionada transferencia.

El Tribunal no puede exigir para una causa de oposición un documento distinto del prevenido por la Ley procesal, de forma que si el pago se ha acreditado con documento, aunque no sea público, debe tener plena eficacia como prueba de la causa de oposición; al no estimarse la oposición se infringe el citado precepto, pretensión que reproducimos en esta alzada.

En el presente caso, la parte ejecutante no ha impugnado los documentos aportados por esta parte; es más no niega que en el título ejecutivo consta la cuenta corriente en la que se harían los pagos, coincidente con el que aparece en el recibo de transferencia.

Conforme al art. 326.1 LEC "los documentos privados harán prueba plena en el proceso, en los términos del artículo 319, cuando su autenticidad no sea impugnada por la parte a quien perjudiquen", por lo que no constando acreditada esta impugnación, ni la presentación de prueba de que el pago no llegó a efectuarse en la cuenta corriente designada por el ejecutante, la causa de oposición debió estimarse.

En virtud de todo lo expuesto,

SUPLICO A LA SALA

que teniendo por presentado este escrito con sus copias lo admita y tenga por interpuesto en tiempo y forma RECURSO DE APELACIÓN contra el auto de fecha [FECHA] y, previa elevación de los autos a la Audiencia Provincial de [LOCALIDAD] se dicte por ésta auto en el que, revocando el impugnado, se estime la oposición a la ejecución planteada por esta parte, declarando improcedente la ejecución despachada contra la apelante, dejando la misma sin efecto y alzando los embargos acordados y demás medidas de ejecución adoptadas, con todos los demás efectos inherentes a esta declaración conforme al art. 561.3 LEC.

OTROSÍ DIGO que en cumplimiento de lo establecido en la disposición adicional decimoquinta, apartado tercero, de la Ley Orgánica del Poder Judicial, se acompaña resguardo acreditativo de haber de consignado como depósito la cantidad de 50 euros.

En su virtud,

SUPLICO A LA SALA que tenga por acreditada la consignación exigida para la admisión a trámite del presente recurso, sin perjuicio de que, en caso de estimación, disponga su devolución conforme a lo establecido en el apartado octavo de dicha disposición.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
