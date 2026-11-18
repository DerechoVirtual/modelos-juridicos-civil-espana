---
name: recurso-apelacion-division-cosa-comun-135
description: "Redacta el escrito «Recurso de apelación en la división de cosa común» (formulario 135 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso de apelación en la división de cosa común

> Formulario 0135 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] FECHA DE LA SENTENCIA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CION CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…s Tribunales, actuando en nombre de Doña»; «…editada en los autos de juicio ordinario»; «…ntegridad la demanda interpuesta por Don»; «…ara recurrir. Es de Justicia que pido en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458.1 LEC
- art. 458.1 y 3 LEC
- arts. 23.1 y 31.1 LEC
- arts. 222 LEC
- art. 276 LEC
- art. 464 LEC

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

### Formulario 0135 · Recurso de apelación en la división de cosa común

- Año del modelo: 2022
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 9 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA DE LA SENTENCIA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de interposición de un recurso de apelación contra una sentencia estimatoria dictada en un proceso declarativo de división de cosa común. En la práctica forense, la resistencia a una demanda en la que se ejercita una acción de división de cosa común se articula alegando siempre los mismos motivos: a) imposibilidad material, b) que la división inutilice la cosa para su uso o c) la existencia de un pacto de indivisión, que es la que sirve de fundamento al presente modelo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCION CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Don/Doña [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de Doña [COMPLETAR], cuya representación tengo acreditada en los autos de juicio ordinario [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que, mediante el presente escrito y en la indicada representación interpongo, en el plazo conferido al efecto, y conforme a los arts. 458 y ss. LEC, RECURSO DE APELACIÓN contra Sentencia de fecha [FECHA], notificada a esta parte en fecha

REQUISITOS PROCESALES

I.- Se presenta este escrito de interposición ante ese Tribunal, que es el competente para conocer del recurso, con arreglo al art. 458.1 LEC.

II.- Se presenta este escrito de interposición dentro del plazo de veinte días contados desde el día siguiente a la notificación de la resolución impugnada (art. 458.1 y 3 LEC).

III.- Esta parte se halla legitimada por afectarle desfavorablemente la resolución impugnada, conforme exige el 448.1 LEC.

IV.- Las exigencias de postulación se llenan para este escrito de interposición, ya que está comparecida esta parte mediante Procurador de los Tribunales, y asistida de abogado en ejercicio, ambos colegiados y habilitados para ejercer ante el Tribunal (arts. 23.1 y 31.1 LEC).

FUNDAMENTOS DEL RECURSO

ÚNICO

Por infracción, en concepto de interpretación errónea y consecuente inaplicación, de los arts. 222 LEC y 400 CCiv, que eran aplicable para resolver la cuestión objeto de debate, en tanto la sentencia de instancia no reconoce la validez del pacto de conservar la cosa indivisa, como excepción a la facultad de pedir la división de la cosa común.

Así, debe tenerse en cuenta que las partes firmaron un convenio regulador aprobado judicialmente (documento nº [Nº DE DOCUMENTO] de la contestación a la demanda) en el que, por lo que interesa al caso de autos, acuerdan sobre la finca objeto de litigio, domicilio familiar y propiedad de ambos, su atribución a la madre que ostenta la guarda y custodia de las menores y que la atribución de la vivienda sería hasta que las menores alcancen la independencia económica, momento a partir del cual los propietarios decidirán sobre la enajenación o no del inmueble. Esta última parte del acuerdo contiene, en puridad, un pacto de indivisión. Dicho pacto ha sido aprobado judicialmente. No considera esta parte que estemos ante un supuesto de cosa juzgada en sentido negativo pues ninguna resolución judicial ha resuelto sobre la acción de división común que se ejercita en la demanda, sin que haya identidad de causa de pedir.

Sí considera esta parte que la sentencia dictada en el proceso de menores que aprueba el convenio ha de tener efectos en este juicio. Estamos ante un supuesto de cosa juzgada material en sentido positivo, con efectos prejudiciales, que impone el respeto a las decisiones judiciales firmes en los enjuiciamientos conexos que se producen con posterioridad, impidiendo al actor ejercitar la acción de división común en virtud del pacto de indivisión que acordaron los progenitores en el anterior proceso.

En consecuencia, considera esta parte, que en virtud del pacto de indivisión aprobado judicialmente en un proceso anterior, el actor, actualmente, no tiene acción para pedir la división de lacosa común, por lo que estimando en consecuencia la apelación, debe revocarse la sentencia de instancia.

Por lo expuesto,

SUPLICO A LA SALA

Que, teniendo por presentado este escrito con su copia, y documento/s acompañado/s, de lo que se ha dado traslado al Procurador de la parte contraria en la forma que previene el art. 276 LEC, se sirva tener por INTERPUESTO RECURSO DE APELACIÓN contra la sentencia de fecha [FECHA DE LA SENTENCIA], y

SUPLICO A LA AUDIENCIA PROVINCIAL

Que, seguido que sea el legal procedimiento, dicte sentencia que revoque la de instancia, y resolviendo sobre la cuestión que es objeto de proceso, desestime en su integridad la demanda interpuesta por Don [COMPLETAR] contra mi representada, y todo ello con imposición de las costas causadas al demandante, procediendo a la devolución del depósito constituido para recurrir.

Es de Justicia que pido en [COMPLETAR]

OTROSÍ PRIMERO DIGO,

Que se acompaña a este escrito resguardo acreditativo del pago del depósito de 50 euros en la Cuenta de Depósitos y Consignaciones del Tribunal al que se dirige, conforme exige la disposición adicional 15.ª LOPJ, por lo que,

SUPLICO A LA SALA

Que tenga por causada la manifestación anterior a los efectos oportunos.

OTROSÍ SEGUNDO DIGO,

que de conformidad con lo dispuesto en el art. 464 LEC solicito que se acuerde la celebración de vista pública, por lo que,

SUPLICO A LA AUDIENCIA PROVINCIAL

Que teniendo por causada la manifestación anterior a los efectos oportunos, se sirva acordar de conformidad, como es procedente en Justicia que reitero.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
