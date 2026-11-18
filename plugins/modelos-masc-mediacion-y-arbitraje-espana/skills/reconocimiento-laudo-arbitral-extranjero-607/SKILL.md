---
name: reconocimiento-laudo-arbitral-extranjero-607
description: "Redacta el escrito «Reconocimiento de laudo arbitral extranjero» (formulario 607 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconocimiento de laudo arbitral extranjero

> Formulario 0607 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (5 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] FECHA (7 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, calle [CALLE], número [NÚMERO], piso»; «…con número de colegiado/a»; «…dictado por la Corte de Arbitraje de»; «…, calle [CALLE], número [NÚMERO], piso»; «…do arbitral por la Corte de Arbitraje de»; «… arbitraje ante la Corte de Arbitraje de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 46 de la Ley 60/2003
- arts. 54 y 55 de la Ley 29/2015

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

### Formulario 0607 · Reconocimiento de laudo arbitral extranjero

- Año del modelo: 2016
- Revisión 17-11-2026: 31 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de exequatur de laudo arbitral extranjero conforme al Convenio sobre reconocimiento y ejecución de las sentencias arbitrales extranjeras, hecho en Nueva York, el 10 de junio de 1958.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurado/a de los Tribunales, que actúa en nombre y representación de D./DÑA./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], piso [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO]; siendo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD] con número de colegiado/a [COMPLETAR], con despacho profesional abierto en esta capital sito en [LOCALIDAD], ante la Sala comparezco y como mejor proceda en derecho, DIGO:

Que, al amparo de lo dispuesto en el art. 46 de la Ley 60/2003, de 23 de diciembre, de Arbitraje (en adelante, LA), por medio del presente escrito se formula SOLICITUD DE RECONOCIMIENTO del laudo arbitral de fecha [FECHA] dictado por la Corte de Arbitraje de [COMPLETAR], solicitud que dirijo frente a D./DÑA./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], piso [COMPLETAR], en base a los siguientes:

HECHOS

PRIMERO.- En fecha [FECHA] se dictó laudo arbitral por la Corte de Arbitraje de [COMPLETAR] (acompaño como documento número [Nº DE DOCUMENTO] testimonio del laudo dictado y traducción oficial del mismo).

SEGUNDO.- El citado laudo se dictó en virtud de convenio arbitral de fecha [FECHA] en el que ambas partes se comprometen a la resolución de las controversias derivadas del contrato de fecha [FECHA] por vía de arbitraje ante la Corte de Arbitraje de [COMPLETAR], habiéndose comunicado al demandado la iniciación del procedimiento y siguiéndose el mismo con intervención de ambas partes de forma contradictoria, siendo notificado en fecha [FECHA] (acompaño como documento número [Nº DE DOCUMENTO] testimonio del procedimiento arbitral seguido y traducción oficial del mismo).

TERCERO.- Dicho laudo es firme, tal como se acredita por la diligencia extendida por la Secretaría de la Corte que se acompaña como documento número [Nº DE DOCUMENTO]

FUNDAMENTOS JURÍDICOS

I.- COMPETENCIA.

El art. 8.6 LA establece que "Para el reconocimiento de laudos o resoluciones arbitrales extranjeros será competente la Sala de lo Civil y de lo Penal del Tribunal Superior de Justicia de la Comunidad Autónoma del domicilio o lugar de residencia de la parte frente a la que se solicita el reconocimiento o del domicilio o lugar de residencia de la persona a quien se refieren los efectos de aquellos, determinándose subsidiariamente la competencia territorial por el lugar de ejecución o donde aquellos laudos o resoluciones arbitrales deban producir sus efectos"; de ahí que la competencia corresponda a la Sala a la que me dirijo al ser la del domicilio del demandado.

II.- PROCEDIMIENTO.

Son de aplicación los arts. 54 y 55 de la Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil.

III.- RECONOCIMIENTO DEL LAUDO EXTRANJERO.

El art. 46.2 LA establece que "El exequátur de laudos extranjeros se regirá por el Convenio sobre reconocimiento y ejecución de las sentencias arbitrales extranjeras, hecho en Nueva York, el 10 de junio de 1958, sin perjuicio de lo dispuesto en otros convenios internacionales más favorables a su concesión, y se sustanciará según el procedimiento establecido en el ordenamiento procesal civil para el de sentencias dictadas por tribunales extranjeros".

El laudo ha sido dictado con todas las garantías y requisitos legales que establece dicho Convenio, cuyo art. V describe la únicas causas para oponerse al reconocimiento y ejecución de un laudo dictado en país extranjero, basadas en la falta de posibilidad de que el conflicto sea susceptible de arbitraje, que la ejecución sea contraria al orden público, incapacidad de las partes, invalidez del contrato, falta de notificación e intervención de la parte en el procedimiento arbitral, que la sentencia sobrepase el objeto del compromiso suscrito, falta de sujeción del procedimiento arbitral al acuerdo de las partes o Ley aplicable, falta de firmeza o ejecutoriedad de la sentencia, ninguna de las cuales concurre en este supuesto, siendo el laudo de incuestionable ejecutoriedad, por lo que se pretende su reconocimiento.

Por todo ello,

SUPLICO A LA SALA

que teniendo por presentada esta solicitud con sus documentos y copias, la admita a trámite, me tenga por comparecido como parte, en representación de D./DÑA. [NOMBRE Y APELLIDOS], entienda conmigo las sucesivas actuaciones, y tras los trámites legalmente previstos, con audiencia del demandado y con intervención del Ministerio Fiscal, dicte resolución otorgando el reconocimiento del laudo arbitral extranjero de fecha [FECHA] dictado por la Corte de Arbitraje de

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
