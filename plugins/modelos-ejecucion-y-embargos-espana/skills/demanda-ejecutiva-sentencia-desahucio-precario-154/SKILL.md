---
name: demanda-ejecutiva-sentencia-desahucio-precario-154
description: "Redacta el escrito «Demanda ejecutiva de la sentencia de desahucio por precario» (formulario 154 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva de la sentencia de desahucio por precario

> Formulario 0154 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (3 veces)
- [ ] Nº
- [ ] FECHA
- [ ] Nº DE RESOLUCIÓN
- [ ] PLAZO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, finca registral»; «…del Registro de la Propiedad de»; «…, referencia catastral»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 545.1 LEC
- art. 538.1 LEC
- art. 539.1 LEC
- arts. 703 y 704 LEC
- art. 703.1 LEC
- art. 438.6 LEC
- art. 539 LEC

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

### Formulario 0154 · Demanda ejecutiva de la sentencia de desahucio por precario

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda en solicitud de despacho de ejecución no dineraria de sentencia firme de desahucio por precario.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada, junto con la dirección letrada y las circunstancias personales, en los autos de juicio verbal de desahucio por precario, registrados con el número [NÚMERO], seguidos frente a D./Dña. [NOMBRE Y APELLIDOS], siguiendo instrucciones de mi mandante y como mejor proceda en derecho, DIGO:

Que mediante el presente escrito formulo demanda ejecutiva contra D./Dña. [NOMBRE Y APELLIDOS], a fin de que se proceda a su lanzamiento de la vivienda sita en [LOCALIDAD], todo ello según resulta de los siguientes:

HECHOS

PRIMERO.- Mi mandante D./Dña. [NOMBRE Y APELLIDOS], interpuso demanda de juicio verbal de desahucio por precario frente a D./Dña. [NOMBRE Y APELLIDOS], de la que ha conocido este Tribunal bajo el nº [Nº]

En el curso del referido procedimiento se dictó en fecha [FECHA] sentencia nº [Nº DE RESOLUCIÓN] en la que, en su parte dispositiva, se indicaba que estimando íntegramente la demanda, declaraba haber lugar el desahucio por precario de la vivienda sita en [LOCALIDAD], finca registral [COMPLETAR] del Registro de la Propiedad de [COMPLETAR], referencia catastral [COMPLETAR], condenando expresamente a que D./Dña. [NOMBRE Y APELLIDOS] dejara libre y a entera disposición del/de la demandante D./Dña. [NOMBRE Y APELLIDOS], la vivienda en el plazo de [PLAZO], siendo apercibido de que de no verificarlo voluntariamente se procedería a su lanzamiento judicial, y con expresa imposición de las costas procesales.

Dicha sentencia al no ser recurrida adquirió el carácter de firme.

SEGUNDO.- Dado que hasta la fecha no se ha dado cumplimiento voluntario a la resolución por el condenado, con la entrega de la posesión y el consiguiente desalojo de la vivienda a la que se alude en la sentencia dictada, habiendo transcurrido con exceso el mencionado plazo, me veo en la necesidad de formular demanda ejecutiva, para que acuerde la ejecución y se entregue el inmueble a mi representado.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Según el art. 545.1 LEC, será competente para la ejecución de resoluciones judiciales el tribunal que conoció del asunto en primera instancia.

Por eso se presenta esta demanda ante el Tribunal al que gustosamente me dirijo, ya que fue quien dictó la sentencia de condena que sirve de título para la presente ejecución.

II.- CAPACIDAD Y LEGITIMACIÓN.

Se cumplen los requisitos de capacidad, en tanto que personas físicas ejecutante y ejecutado, mayores de edad en pleno disfrute de sus derechos civiles (arts. 6.1.1º y 7.1 LEC), que fueron partes en el proceso declarativo del que surge la ejecutoria, legitimadas conforme al art. 538.1 LEC.

III.- POSTULACIÓN.

Conforme a lo dispuesto en el art. 539.1 LEC, la demanda viene firmada por abogado y procurador, ya que estamos ante la ejecución de una resolución dictada en un proceso en que es preceptiva la intervención de dichos profesionales.

IV.- TÍTULO DE EJECUCIÓN.

El art. 517.2.1º LEC enumera como uno de los títulos que lleva aparejada ejecución la sentencia de condena firme, como la que sirve de fundamento a esta demanda.

V. PROCEDIMIENTO.

Procede seguir los trámites establecidos en los arts. 699 y ss. y concordantes, en relación a la ejecución no dineraria, expresamente en relación a lo dispuesto en el los arts. 703 y 704 LEC.

VI. EJECUCIÓN DE DEBER DE ENTREGA DE BIENES INMUEBLES.

Si el título dispusiere la transmisión o entrega de un bien inmueble, el tribunal ordenará de inmediato lo que proceda según el contenido de la condena -desalojo del demandado- y, en su caso, dispondrá lo necesario para adecuar el Registro al título ejecutivo.

Si en el inmueble que haya de entregarse hubiere cosas que no sean objeto del título, el tribunal requerirá al ejecutado para que las retire dentro del plazo que se señale. Si no las retirare, se considerarán bienes abandonados a todos los efectos (art. 703.1 LEC).

Por lo demás, el art. 438.6 LEC prevé que, en todos los casos de desahucio, el Letrado de la Administración de Justicia habrá fijado ya en la resolución que se dicte teniendo por opuesto al demandado el día y hora para que tenga lugar el lanzamiento, que deberá ser inferior a un mes desde la fecha de la vista.

VII. COSTAS.

Serán impuestas a la parte ejecutada, conforme al art. 539 LEC.

Por todo ello,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con su copia, se sirva admitirlo, ordenando se entiendan conmigo las sucesivas diligencias y, en nombre de mi patrocinado, se tenga por presentada demanda ejecutiva para que, una vez examinados los requisitos y presupuestos procesales, el título ejecutivo y los actos de ejecución que se solicitan, así como la propia competencia, se dicte mediante auto orden general de ejecución y despacho de la misma, y una vez acordado, por el Letrado de la Administración de Justicia Judicial responsable de la ejecución se ordene el lanzamiento inmediato del demandado D./Dña. [NOMBRE Y APELLIDOS] del inmueble sito en [LOCALIDAD] en la fecha y hora que previamente se haya determinado en la resolución que tuvo por opuesto al demandado, requiriendo al ejecutado para que retire las cosas o bienes que no sean objeto del título. Todo ello con imposición de las costas derivadas de esta ejecución al ejecutado.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
