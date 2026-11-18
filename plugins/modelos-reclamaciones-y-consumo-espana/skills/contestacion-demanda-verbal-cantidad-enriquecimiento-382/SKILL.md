---
name: contestacion-demanda-verbal-cantidad-enriquecimiento-382
description: "Redacta el escrito «Contestación a la demanda verbal de cantidad por enriquecimiento injusto» (formulario 382 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda verbal de cantidad por enriquecimiento injusto

> Formulario 0382 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] COLEGIO (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A (3 veces)
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO
- [ ] ÓRGANO
- [ ] Sentencia Tribunal Supremo, Sala Primera, de lo Civil, de 13 Dic. 1991 ) y Sentencia Tribunal Supremo, Sala Primera, de lo Civil, de 4 Jun. 1993 
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D./Dña. [NOMBRE Y APELLIDOS]:»

## Elecciones que hay que hacer

- NIF / CIF

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 394 LEC
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

### Formulario 0382 · Contestación a la demanda verbal de cantidad por enriquecimiento injusto

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 14 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a la demanda de juicio verbal en ejercicio de acción de enriquecimiento injusto derivada de condictio por inversión o por expensas en supuesto de ruptura de pareja de hecho.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS]: [COMPLETAR], Procurador/a de los Tribunales, Coleg. del Ilustre Colegio de Procuradores de [COLEGIO], actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF], en virtud de como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección letrada de D/D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparece y como mejor proceda en Derecho DICE

Que habiendo sido notificado y emplazado mediante [ÓRGANO], por medio del presente escrito, vengo a formular CONTESTACIÓN A LA DEMANDA DE JUICIO VERBAL EN EJERCICIO DE ACCIÓN DE ENRIQUECIMIENTO INJUSTO presentada por D./D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], en base a las siguientes

HECHOS

PRELIMINAR

Esta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito

PRIMERO

Conforme con el correlativo de la demanda en relación a la constitución e inscripción de la pareja de hecho y el inicio de la convivencia.

SEGUNDO

Disconforme con el correlativo de la demanda. Si bien manifiesta la actora que mi representado constituyó una empresa con domicilio social en el domicilio común, lo cierto es que, dicha constitución, se realizó previo acuerdo entre ambos miembros de la pareja, y a fin de ahorrar costes, acordando lo conviviente establecer el centro de trabajo en dicho domicilio.

TERCERO

Disconforme con el correlativo de la demanda. La actora alega que solicita una excedencia con la finalidad de colaborar con la empresa de su pareja, sin embargo, la excedencia se solicita con anterioridad a la constitución de la empresa de mi mandante, por lo que no se puede establecer que la única finalidad de la excedencia solicitada por la actora fuese la de invertir su trabajo en el negocio de la demandada.

CUARTO

Conforme con el correlativo en relación ruptura de la unión de pareja, así como en el cese de la convivencia.

QUINTO

Disconforme con el correlativo de la demanda. No se puede hablar de enriquecimiento injusto cuando ambos miembros de la pareja han disfrutado del escaso beneficio patrimonial obtenido, además, ambos pactaron libremente la constitución de la sociedad así, como la dedicación del actor en exclusiva a la misma. La actora, cesa en su trabajo tras solicitar una excedencia sin que pueda decirse que ha colaborado activamente invirtiendo su trabajo en el negocio constituido por ambos.

A los anteriores le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO

Conformes a los correlativos a la demanda sobre jurisdicción, competencia oponiéndose al resto de los alegados por no ser de aplicación o serlo "a sensu contrario"

SEGUNDO

Conforme con el correlativo de la demanda sobre capacidad y legitimación.

TERCERO

Conforme con el correlativo sobre representación y defensa, así como procedimiento.-

CUARTO

Oponiéndonos a los fundamentos jurídico-materiales alegados en relación al fondo del asunto por no ser de aplicación o ser de aplicación a sensu contrario

Con carácter general, la ruptura de la unión de hecho no implica deber de indemnización alguna, ya que los convivientes son los que han aceptado crear una unión al margen del matrimonio legalmente establecido, que, si crea derechos y obligaciones, aunque si admite el pacto para la determinación del resarcimiento económico en aso de ruptura de la convivencia de la unión de hecho.

La jurisprudencia ha establecido [Sentencia Tribunal Supremo, Sala Primera, de lo Civil, de 13 Dic. 1991 ) y Sentencia Tribunal Supremo, Sala Primera, de lo Civil, de 4 Jun. 1993 ] para que proceda la compensación por la vía del enriquecimiento injusto en los supuestos de las rupturas de las parejas de hecho, es necesario, estando a la existencia de pactos, promesas o la creación y el sostenimiento de situaciones de facto de las que, por la vía de la facta concludentia, se pueda deducir que hubo ese proyecto de vida en común, y que se ha producido lo que se denomina la "pérdida de oportunidad", que sería el factor que vendría de algún modo a sustituir al concepto de empeoramiento que equivale al desequilibrio en el régimen económico matrimonial.

Por tanto, para la apreciación de la existencia del enriquecimiento injusto, debería existir un empobrecimiento correlativo de la actora, que en este caso no concurre, pudiendo afirmar que no sí ha existido enriquecimiento de mi mandante habrá sido a consecuencia de su buen hacer en los negocios.

QUINTO. Costas

Se condenado el actor a las costas de la primera instancia por la temeridad y mala fe conforme el artículo 394 LEC.

Por lo expuesto

SUPLICA AL TRIBUNAL,

que me tenga por personado y comparecido en tiempo y forma en representación de [NOMBRE DEL REPRESENTADO/A] y por CONTESTADA LA DEMANDA, y tras el curso legal, se dicte sentencia por la que se desestime la demanda interpuesta y condene a la actora al pago de las costas ocasionadas en la instancia.

Por ser Justicia que pide en [LUGAR], a [FECHA].

( (Seleccionar una o varias opciones))

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

OTROSÍ DIGO: Que interesa a esta parte la celebración de vista, al existir controversia sobre los hechos y ser necesaria la práctica de prueba para la resolución de este proceso.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente, se sirva señalar la celebración de vista

OTROSÍ DIGO: Que esta parte no considera necesaria la celebración de vista.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente, se tenga por realizada a los efectos oportunos.

SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC., y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.

Firma del Abogado/a	Firma del Procurador/a
