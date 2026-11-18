---
name: intervencion-judicial-herencia-tras-declaracion-860
description: "Redacta el escrito «Intervención judicial de la herencia tras la declaración de herederos» (formulario 860 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Intervención judicial de la herencia tras la declaración de herederos

> Formulario 0860 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NÚMERO (3 veces)
- [ ] Nº (2 veces)
- [ ] PROFESIÓN (2 veces)
- [ ] DNI/NIE
- [ ] CALLE
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…entes ANTECEDENTES DE HECHO Con fecha de»; «…falleció en»; «… y dejando dos únicos hijos llamados Dña»; «…—mi representada— y D»; «…como únicos y universales herederos de D»; «…a sus dos hijos, Dña»; «…—mi poderdante— y D»; «…Es heredero legal del causante D»; «…, además de mi mandante, su hermano D»; «…abintestato y hermano de mi poderdante D»; «…mo bienes relictos al fallecimiento de D»; «… el nombramiento como Administrador de D»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 792 de la LEC
- art. 791 de la LEC

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

### Formulario 0860 · Intervención judicial de la herencia tras la declaración de herederos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito presentado ante el Tribunal de Instancia por quien ha promovido declaración de herederos abintestato ante notario, solicitando la intervención judicial de los bienes del fallecido.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

D./Dña [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, interviniendo en nombre de D./Dña [NOMBRE Y APELLIDOS], cuyas circunstancias constan en la escritura de poder que acompaño para acreditar mi representación y cuya devolución solicito previo su testimonio en autos, ante el Tribunal comparezco bajo la dirección del Letrado D./Dña [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que amparándome en lo dispuesto en el art. 792 de la LEC, en nombre de mi representada solicito mediante el presente escrito la INTERVENCIÓN JUDICIAL DE LA HERENCIA DE D./Dña [NOMBRE Y APELLIDOS], interesando la adopción de las medidas que se detallan en la presente solicitud, que baso en los siguientes

ANTECEDENTES DE HECHO

Con fecha de [COMPLETAR] falleció en [COMPLETAR] D./Dña [NOMBRE Y APELLIDOS], padre de mi representada. Acredito este extremo con certificación de defunción que acompaño reseñada como documento n.º [NÚMERO] Dicho causante falleció en estado de viudo y dejando dos únicos hijos llamados Dña [COMPLETAR] —mi representada— y D [COMPLETAR] Acredito estos extremos con el Libro de Familia que acompaño reseñado como documento n.º [NÚMERO] No otorgó testamento, conforme se desprende del Certificado del Registro de Actos de Última Voluntad que acompaño referenciado con n.º [Nº]

Al haber fallecido el causante sin haber otorgado testamento, mi mandante ha instado la declaración notarial de herederos del causante D./Dña [NOMBRE Y APELLIDOS], extremo que acredito con acta notarial de requerimiento para la declaración como únicos y universales herederos de D [COMPLETAR] a sus dos hijos, Dña [COMPLETAR] —mi poderdante— y D [COMPLETAR] que acompaño reseñada con n.º [Nº]

Es heredero legal del causante D [COMPLETAR], además de mi mandante, su hermano D [COMPLETAR], mayor de edad, de profesión [PROFESIÓN], provisto de DNI [DNI/NIE], que podrá ser citado en su domicilio sito en C/ [CALLE] n.º [NÚMERO] de

A los hechos antecedentes son de aplicación los siguientes

PRESUPUESTOS Y FUNDAMENTOS JURÍDICOS

Amparo esta petición en lo dispuesto en el art. 792 de la LEC, que permite, una vez acreditado que se ha promovido declaración notarial de herederos abintestato, solicitar la adopción de las medidas previstas en el art. 791 de la LEC.

Está legitimado mi mandante para formular esta solicitud en su condición de heredero abintestato del causante (art. 792 de la LEC).

Las medidas concretas —previstas en el art. 791 de la LEC— cuya adopción se interesan son:

1.º Ocupación de los documentos del causante, que se encuentran en su último domicilio sito en [LOCALIDAD] El coheredero abintestato y hermano de mi poderdante D [COMPLETAR], que se deja circunstanciado, dispone del único juego de llaves del mencionado domicilio existente tras el fallecimiento del causante, por lo que podrá hacerse efectivo el acceso al domicilio requiriendo judicialmente su colaboración.

2.º Inventario y depósito de bienes del causante. A tal efecto designo como bienes relictos al fallecimiento de D [COMPLETAR]:

A) EFECTIVO Y DEPOSITOS BANCARIOS:

B) BIENES MUEBLES:

C) BIENES INMUEBLES:

3.º Administración judicial de la herencia. La existencia de cuantiosos depósitos bancarios y de alquileres en los inmuebles del causante requieren una urgente y activa gestión para evitar su pérdida de productividad, por lo que parece necesario designar persona que se haga cargo de su administración. A tal efecto, y siendo las cuotas de participación hereditaria de ambos herederos legítimos idénticas, esta parte propone el nombramiento como Administrador de D [COMPLETAR], mayor de edad, de profesión [PROFESIÓN] y domiciliado en

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito y documentos adjuntos con sus copias preceptivas, se sirva admitir todo ello, teniendo por solicitada la INTERVENCIÓN JUDICIAL DE LA HERENCIA de D [COMPLETAR], acordando la adopción de las medidas de ocupación de documentos del causante interesadas en el cuerpo del presente escrito y la citación de esta parte y del coheredero D [COMPLETAR] para la formación del inventario, y realizado éste, acordar el depósito de los bienes inventariados y lo que resulte procedente para la administración del caudal hereditario.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
