---
name: prueba-pericial-anticipada-propiedad-horizontal-antes-104
description: "Redacta el escrito «Prueba pericial anticipada en propiedad horizontal antes del proceso» (formulario 104 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Prueba pericial anticipada en propiedad horizontal antes del proceso

> Formulario 0104 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D.»; «…a a la interposición de la demanda de D.»; «…de»; «…ismos y por comparecido al Procurador D.»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 293 LEC
- art. 10.1 a) LPH
- art. 293.2 LEC
- art. 293.1 LEC
- art. 339.2 LEC
- arts. 293 y 294 LEC
- art. 295 LEC
- arts. 346 y 347 LEC

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

### Formulario 0104 · Prueba pericial anticipada en propiedad horizontal antes del proceso

- Año del modelo: 2022
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 8 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que cualquiera de las partes solicita, al amparo del artículo 293 de la Ley de Enjuiciamiento Civil, la admisión y práctica de prueba pericial anticipada, antes del inicio del proceso, en materia de propiedad horizontal.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DEQ.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [COMPLETAR], Procurador de los Tribunales, actuando en representación de D. según se acredita mediante copia electrónica del poder notarial de representación digitalizada que se acompaña y se solicita sea devuelta una vez testimoniada en autos, ante el Tribunal comparezco y por medio del presente escrito formulo solicitud de práctica de prueba pericial de designación judicial anticipada previa a la interposición de la demanda de D. [COMPLETAR], con domicilio en [LOCALIDAD], al amparo de lo dispuesto en el art. 293 LEC; todo ello con fundamento en los siguientes:

Hechos y consideraciones jurídicas

1º) Mi representado piensa entablar demanda de juicio declarativo ejercitando acción personal de condena no pecuniaria y pecuniaria frente a la Comunidad de Propietarios del inmueble nº [NÚMERO] de [COMPLETAR], por las humedades y goteras que sufre el actor en su vivienda, fruto del mal estado en el que se encuentra -a fecha de hoy- la cubierta y fachada del edificio, lo que genera la responsabilidad de la Comunidad demandada al amparo de lo previsto en el art. 10.1 a) LPH, mas para la interposición de la demanda se considera imprescindible el hacer una valoración de los defectos apreciados así como del coste que la reparación comportará; valoración pericial que es necesario verificar en este momento ya que el estado de deterioro de la cubierta es de tal magnitud que es posible que ello ocasione importantes perjuicios no solamente a mi mandante sino incluso a las personas que circulen por las inmediaciones del inmueble lo que hace que la verificación de las reparaciones más urgentes se considere como imprescindible y con ello la realización de la pericial de forma anticipada a fin de que por parte del perito se constate el estado de la citada cubierta. al poder desaparecer los vestigios de los desperfectos por la realización de las medidas de seguridad más urgentes. A tal efecto se interesa la designación de un perito arquitecto técnico a fin de que informe sobre la relación de causa-efecto de los citados desperfectos en la vivienda de mi representado con el mal estado actual de la cubierta y fachada del edificio de la demandada, y en el caso de existir proceda a la constatación de los defectos existentes en la vivienda de mi mandante sita en [LOCALIDAD] así como a la determinación de las labores necesarias para proceder a su corrección y el coste económico de las mismas.

2º) Que es competente el Tribunal al que me dirijo al ostentarla también para conocer del procedimiento principal (art. 293.2 LEC) por ser el del partido judicial en que radica la finca (art. 52.1.8º LEC).

3º) Que esta parte está legitimada para formular la presente solicitud por ser el futuro demandante en el pleito que se pretende interponer (art. 293.1 LEC).

4º) Que la presente solicitud deberá tramitarse conforme a lo previsto en los arts. 293 y ss. LEC, operando en cuanto a la pericial de designación judicial lo previsto en el art. 339.2 LEC.

5º) Que concurren los requisitos que para acordar la práctica de la prueba pericial anticipada se fijan en los arts. 293 y 294 LEC, en cuanto el estado de la cubierta y fachada hace necesaria la realización de las medidas de seguridad más urgentes habiéndose proporcionado la completa identificación de la parte que va a ser demandada con la finalidad de que pueda participar en la práctica de la prueba tal y como establece el art. 295 LEC y en concreto en la forma prevista en los arts. 346 y 347 LEC.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito y documentos adjuntos al mismos y por comparecido al Procurador D. [COMPLETAR], en representación de D. [NOMBRE Y APELLIDOS] y en base a lo en él señalado se tenga a bien acordar la práctica de la prueba pericial procediendo a la designación de un perito arquitecto técnico a los efectos señalados haciendo saber a la entidad que se pretende demandar a fin de que pueda intervenir en esta prueba en la forma legalmente prevista.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
