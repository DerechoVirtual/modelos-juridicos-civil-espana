---
name: separacion-divorcio-mutuo-acuerdo-sin-hijos-menores-ni-801
description: "Redacta el escrito «Separación o divorcio de mutuo acuerdo sin hijos menores ni con apoyos dependientes» (formulario 801 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Separación o divorcio de mutuo acuerdo sin hijos menores ni con apoyos dependientes

> Formulario 0801 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] DNI/NIE (2 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] FECHA (2 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…bre y representación de los cónyuges Don»; «…, con domicilio en [LOCALIDAD], y Doña»; «… en los siguientes: HECHOS PRIMERO.- Don»; «…y Doña»; «…en»; «… De dicha unión nació un hijo, de nombre»; «…, nacido el»; «…DE MUTUO ACUERDO de Don»; «… MUTUO ACUERDO de Don [COMPLETAR] y Doña»

## Elecciones que hay que hacer

- DIVORCIO / SEPARACIÓN
- civil / canónico
- la extinción del vínculo matrimonial por medio de divorcio / separarse
- divorcio / separación
- el divorcio / la separación

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de divorcio / En caso de separación / Selecciona una u otra opción — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de divorcio / En caso de separación — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 769.2 LEC
- art. 777 LEC
- art. 87 CCiv
- art. 82 CCiv
- art. 90 CCiv

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

### Formulario 0801 · Separación o divorcio de mutuo acuerdo sin hijos menores ni con apoyos dependientes

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 7 desplegables convertidos en elección en blanco; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 20 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda consensual de separación o divorcio de mutuo acuerdo sin hijos menores de edad no emancipados o con medidas judiciales de apoyo para el ejercicio de su capacidad jurídica que dependan de los progenitores.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de los cónyuges Don [COMPLETAR], provisto de DNI n.º [DNI/NIE], con domicilio en [LOCALIDAD], y Doña [COMPLETAR], provista de DNI n.º [DNI/NIE], con domicilio en [LOCALIDAD], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA SOBRE [ELEGIR: DIVORCIO / SEPARACIÓN] DE MUTUO ACUERDO de los cónyuges arriba indicados, a la que se acompaña PROPUESTA DE CONVENIO REGULADOR, con base en los siguientes:

HECHOS

PRIMERO.- Don [COMPLETAR] y Doña [COMPLETAR] contrajeron matrimonio [ELEGIR: civil / canónico] en [COMPLETAR], el día [FECHA].

Se acompaña la correspondiente certificación de matrimonio expedida por el Registro Civil de [LOCALIDAD], como documento n.º [NÚMERO].

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

De dicha unión no ha habido descendencia.

De dicha unión nació un hijo, de nombre [COMPLETAR], nacido el [COMPLETAR], por lo que es mayor de edad, que ha salido de la convivencia con sus padres y se gana el sustento con independencia. Se adjunta la correspondiente certificación de nacimiento que ha emitido el Registro Civil de [LOCALIDAD], como documento n.º [Nº DE DOCUMENTO]

SEGUNDO.- Por circunstancias que los cónyuges han valorado debidamente, y que son inaprensibles para los demás, tienen la voluntad de proceder a [ELEGIR: la extinción del vínculo matrimonial por medio de divorcio / separarse].

TERCERO.- Se ha redactado y suscrito por ambos cónyuges el correspondiente convenio regulador, con el deseo expreso de su formalización por el Letrado de la Administración de Justicia, y se adjunta copia como documento n.º [Nº DE DOCUMENTO]

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Es competente el Tribunal al que nos dirigimos, al corresponder al lugar del último domicilio conyugal, en un caso de [ELEGIR: divorcio / separación] de mutuo acuerdo, en que no existen posiciones procesales enfrentadas, conforme al art. 769.2 LEC.

II.- PROCEDIMIENTO

El procedimiento adecuado es el del art. 777 LEC para conocer de las peticiones de [ELEGIR: divorcio / separación] de mutuo acuerdo.

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de divorcio / En caso de separación / Selecciona una u otra opción — el texto de cada opción no venía en el formulario original]

En caso de divorcio

IV.- FONDO DEL ASUNTO

El fondo de la pretensión consiste en la declaración de divorcio, causa de disolución del matrimonio, por mutuo acuerdo de los cónyuges, lo cual procede por la libre voluntad de los casados, con arreglo al art. 87 CCiv por relación con el art. 82, ambos CCiv, después de transcurridos tres meses desde la celebración del matrimonio.

El art. 82 CCiv habilita, no existiendo hijos menores no emancipados o hijos mayores respecto de los que se hayan establecido judicialmente medidas de apoyo atribuidas a sus progenitores, como es el caso, que los cónyuges puedan acordar su separación de mutuo acuerdo transcurridos tres meses desde la celebración del matrimonio mediante la formalización de un convenio regulador ante el Letrado de la Administración de Justicia, en el que, junto a la voluntad inequívoca de separarse, determinarán las medidas que hayan de regular los efectos derivados de la separación en los términos establecidos en el art. 90 CCiv.

Los cónyuges también podrán acordar su divorcio de mutuo acuerdo, sin intervención judicial, conforme establece el art. 87 CCiv, mediante la formalización de un convenio regulador ante el Letrado de la Administración de Justicia, en la forma y con el contenido regulado en el art. 82 CCiv, debiendo concurrir los mismos requisitos y circunstancias exigidas en él.

En ambos casos, los cónyuges deberán intervenir en el otorgamiento de modo personal, sin perjuicio de que deban estar asistidos por Letrado en ejercicio, prestando su consentimiento ante el Letrado de la Administración de Justicia.

(En caso de separación)
[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de divorcio / En caso de separación — el texto de cada opción no venía en el formulario original]

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovido EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA SOBRE [ELEGIR: DIVORCIO / SEPARACIÓN] DE MUTUO ACUERDO de Don [COMPLETAR] y Doña [COMPLETAR], previa ratificación de los cónyuges por separado, se dicte decreto por el Letrado de la Administración de Justicia que declare [ELEGIR: el divorcio / la separación] de los citados cónyuges, formalizando el convenio regulador aportado, como medidas definitivas en cuanto a los efectos de dicho divorcio, como es Justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
