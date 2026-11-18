---
name: subsanacion-defectos-u-omisiones-solicitud-792
description: "Redacta el escrito «Subsanación de defectos u omisiones de la solicitud» (formulario 792 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Subsanación de defectos u omisiones de la solicitud

> Formulario 0792 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO (7 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, de la localidad de»; «…/»; «…, Libro»; «…, Libro [COMPLETAR], Tomo»; «…, Tomo [COMPLETAR], Folio»; «…de la localidad de»; «…. 2.- Finca Registral nº [NÚMERO], Libro»; «…, Libro [COMPLETAR], Tomo»; «…, Tomo [COMPLETAR], Folio»; «…de la localidad de»; «…. 3.- Finca Registral nº [NÚMERO], Libro»; …

## Elecciones que hay que hacer

- Firma de Abogado/a	Firma de Procurador/a

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 16.4 LJV
- art. 106.1 LJV
- art. 106.2 LJV
- art. 105.3 LJV
- Ley 15/2015

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

### Formulario 0792 · Subsanación de defectos u omisiones de la solicitud

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del solicitante subsanando defectos u omisiones en la solicitud de alegaciones a fin de que se resuelva continuar con el expediente, comunicando el inicio del expediente a todos los interesados para que puedan hacer las alegaciones y presentar las pruebas que estimen procedentes.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y al amparo de lo dispuesto en el ar. 16.4 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), procedo a SUBSANAR los defectos apreciados por el Letrado de la Administración de Justicia, con arreglo a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], insté ante el órgano judicial al cual tengo el honor de dirigirme, el deslinde la finca de mi propiedad, no inscrita en el Registro de la Propiedad, y sita en [LOCALIDAD], de la localidad de [COMPLETAR], con arreglo a los trámites establecidos en los arts. 104 y ss. LJV. Mediante diligencia de ordenación de fecha [FECHA], dictada por el Letrado de la Administración de Justicia, se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se me dio traslado, por plazo de cinco días para que procediera a subsanar la ausencia de certificación registral de las fincas colindantes que serán afectadas por el deslinde, y que se encuentran inscritas en el Registro de la Propiedad. Todo, de conformidad con lo dispuesto en el art. 16.4 LJV.

SEGUNDO.- Efectivamente, y por error únicamente imputable a esta parte, no se aportaron las certificaciones registrales de tres de las fincas colindantes que van a ser afectadas por el deslinde aquí pretendido, al no tener claro si las mismas estaban o no inscritas en el Registro de la Propiedad. Tal y como se ha podido comprobar posteriormente, tales fincas, a diferencia de las otras dos, están correctamente inscritas. Por ello, ante la posibilidad ofrecida de subsanación, y siguiendo lo ordenado en el art. 106.1 LJV, se aportan junto a este escrito las certificaciones registrales de las siguientes fincas:

1.- Finca Registral nº [NÚMERO], Libro [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], inscrita en el Registro de la Propiedad nº [NÚMERO] de la localidad de [COMPLETAR].
2.- Finca Registral nº [NÚMERO], Libro [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], inscrita en el Registro de la Propiedad nº [NÚMERO] de la localidad de [COMPLETAR].
3.- Finca Registral nº [NÚMERO], Libro [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], inscrita en el Registro de la Propiedad nº [NÚMERO] de la localidad de [COMPLETAR].

TERCERO.- Procede, en consecuencia, admitir la subsanación aquí presentada, uniendo a los autos las certificaciones registrales ahora aportadas, y, dado que se han hechos constar en la solicitud todas las circunstancias, y se han presentado todos los documentos exigidos legalmente; ha de continuarse con los trámites del expediente, comunicando, en virtud de lo dispuesto en el art. 106.2 LJV, el inicio del presente expediente a todos los interesados relacionados en la solicitud, o que puedan considerarse como tales, para que puedan, en el plazo de quince días, hacer las alegaciones y presentar las pruebas que estimen procedentes.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por subsanada la deficiencia apreciada mediante la unión de los documentos que se acompañan, de conformidad con el art. 16.4 LJV; se resuelva continuar con el expediente, comunicando el inicio del expediente a todos los interesados para que puedan, en el plazo de quince días, hacer las alegaciones y presentar las pruebas que estimen procedentes.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

[ELEGIR: Firma de Abogado/a	Firma de Procurador/a]

Firma del solicitante

NOTAS DEL FORMULARIO

(1) Resulta exigible ser asistido por abogado si el valor de la finca es superior a 6000 €, conforme art. 105.3 LJV.

========================================================================
