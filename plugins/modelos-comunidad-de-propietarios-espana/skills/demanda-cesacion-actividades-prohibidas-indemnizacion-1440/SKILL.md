---
name: demanda-cesacion-actividades-prohibidas-indemnizacion-1440
description: "Redacta el escrito «Demanda de cesación de actividades prohibidas con indemnización de daños» (formulario 1440 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de cesación de actividades prohibidas con indemnización de daños

> Formulario 1440 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (13 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (9 veces)
- [ ] PROFESIÓN (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE
- [ ] IMPORTE (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] DESCRIBIR
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…propietario del inmueble sito en el piso»; «…, letra»; «…. Desde»; «…. Desde [COMPLETAR] tiene alquilado»; «… usuario del inmueble ha instalado en él»; «…dedicado a»; «…munica al Presidente de la Comunidad que»; «…, que los vecinos»; «…scritura pública de compraventa del piso»; «…puesto, redactado de la siguiente manera»; «…euros, según»; «…, titulado en»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Justificante / Exento — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 2 y 6.3 de la Ley 10/2012
- art. 5 de la Ley Orgánica 1/2025
- Ley 8/1999

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

### Formulario 1440 · Demanda de cesación de actividades prohibidas con indemnización de daños

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 53 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de la Comunidad de Propietarios de la C/ [CALLE], n.º [NÚMERO], según acredito mediante poder notarial otorgado por su Presidente D./Dña. [NOMBRE Y APELLIDOS], en nombre de la misma, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y en aplicación del artículo 7.2 de la Ley de Propiedad Horizontal, interpongo demanda a tramitar por el cauce del juicio ordinario en ejercicio de acción de cesación de actividades prohibidas contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN] y con domicilio en [LOCALIDAD] y contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE], así como acción de reclamación de indemnización por los perjuicios causados a esta comunidad en el ejercicio de tal actividad, que ciframos en [IMPORTE] euros, todo ello con base en los siguientes

HECHOS

 Se presenta listado de documentos que acompañan a la demanda como documento 0 o 1.

D./Dña. [NOMBRE Y APELLIDOS] es propietario del inmueble sito en el piso [COMPLETAR], letra [COMPLETAR] de la C/ [CALLE] de esta ciudad, tal como se acredita con nota simple del Registro de la Propiedad que acompañamos como documento n.º [NÚMERO].

Desde [COMPLETAR] tiene alquilado [COMPLETAR] a D./Dña. [NOMBRE Y APELLIDOS], según notificó a la Comunidad de Propietarios a través de su Administrador. (Doc. n.º [NÚMERO])

Desde hace unos meses el usuario del inmueble ha instalado en él [COMPLETAR] dedicado a [COMPLETAR], que ocasiona graves molestias a los vecinos consistentes en

Consultada la Sección de Urbanismo del Ayuntamiento de esta ciudad sobre el otorgamiento de licencia de actividad a D./Dña. [NOMBRE Y APELLIDOS], de forma verbal comunica al Presidente de la Comunidad que [COMPLETAR].

Los Estatutos de la Comunidad de Vecinos, cuya copia aportamos como doc. n.º [NÚMERO], prohíben expresamente en su apartado n.º [NÚMERO], que los vecinos [COMPLETAR]. Por este motivo se requirió por el Presidente de la Comunidad a D./Dña. [NOMBRE Y APELLIDOS] para que cesara en el uso molesto para los vecinos, con apercibimiento de utilizar la vía judicial en caso contrario, según se justifica con el documento n.º [Nº DE DOCUMENTO]

Esta limitación se hacía constar también en los documentos públicos de adquisición del inmueble. Acompañamos a efectos acreditativos escritura pública de compraventa del piso [COMPLETAR], donde aparece lo expuesto, redactado de la siguiente manera [COMPLETAR]. En iguales o similares términos aparece en el resto de los contratos de enajenación de los inmuebles del edificio.

Transcurrido un mes desde tal notificación, el vecino no realizó ningún cambio en su negocio. Por este motivo se convocó reunión extraordinaria de la Junta de Vecinos en cuyo orden del día se incluyó dentro de los puntos a tratar, el de autorizar al Presidente para entablar la presente acción y otorgar poder general para pleitos a favor del Procurador que encabeza la demanda. Adjuntamos como docs. n.º [NÚMERO] copia de la convocatoria y certificación del acuerdo adoptado. A esta reunión fue debidamente convocado el demandado, tal como se acredita mediante citación personal con el recibí firmado por él (doc. n.º [NÚMERO])

:

Al no acudir a la reunión, se entregó a D./Dña. [NOMBRE Y APELLIDOS] copia del acta (Doc. n.º [NÚMERO]) Este se limitó a recogerla sin hacer objeción alguna.

La actividad no sólo ha resultado molesta de forma genérica, sino que ha causado unos daños a la Comunidad consistentes en [DESCRIBIR], y cuya reparación se valora en [IMPORTE] euros, según [COMPLETAR].

El informe del perito D./Dña. [NOMBRE Y APELLIDOS], titulado en [COMPLETAR] que acompañamos con el n.º [NÚMERO] acredita estos extremos.

Previamente a la interposición de la presente demanda, se han intentado todas las soluciones extraprocesales posibles sin que se haya alcanzado el propósito deseado, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial y 36 de la Ley de Enjuiciamiento Civil atribuyen con carácter general a la jurisdicción española y al orden civil el conocimiento de esta materia. Los artículos 85.1º de la Ley Orgánica del Poder Judicial y 45 de la Ley de Enjuiciamiento Civil designan a los Tribunales de Instancia como los órganos que específicamente resolverán estos pleitos. Finalmente el artículo 52.1.8.º de la Ley de Enjuiciamiento Civil dice que en los juicios en materia de propiedad horizontal, será competente el Tribunal del lugar en que radique la finca.

El artículo 7.2 de la Ley de Propiedad Horizontal, reformado por la Disposición final 1.ª de la Ley de Enjuiciamiento Civil remite la tramitación de estos pleitos al cauce del juicio ordinario, al igual que el artículo 249.1.8.º de la Ley de Enjuiciamiento Civil.

La cuantía se fija en [IMPORTE] euros, en aplicación del artículo 251.11.ª de la Ley de Enjuiciamiento Civil a sensu contrario.

Respecto a la tasa por el ejercicio de la potestad jurisdiccional regulado en los artículos 2 y 6.3 de la Ley 10/2012, de 20 de noviembre y en la Orden HAP/2662/2012, de 13 de diciembre:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Justificante / Exento — el texto de cada opción no venía en el formulario original]

El artículo 10 de la Ley de Enjuiciamiento Civil legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. La propia Ley de Propiedad Horizontal faculta al presidente para que en nombre de la Comunidad accione contra quien realiza acciones prohibidas o dañosas para ésta así como contra el titular del inmueble, cuando sean personas distintas.

El artículo 71.2 de la Ley de Enjuiciamiento Civil permite la acumulación de acciones realizadas.

En aplicación de los artículos 23 y 31 de la Ley de Enjuiciamiento Civil las partes deberán comparecer representadas por procurador y asistidas por letrado.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Primero.— Los Estatutos de la Comunidad de Propietarios prohíben en su punto [COMPLETAR].

Tales Estatutos fueron aprobados por unanimidad en reunión constituyente de fecha [FECHA], a la que acudieron todos los vecinos.

Además, en los contratos de compraventa del inmueble, debidamente elevados a escritura pública e inscritos en el Registro de la Propiedad, ya se hacía constar esta limitación, tal como permite el artículo 5 de la Ley de Propiedad Horizontal.

Segundo.— El artículo 7 del mismo texto, reformado por la Ley 8/1999, de 6 de abril, prohíbe al propietario y al ocupante de un piso o local «desarrollar en él o en el resto del inmueble actividades prohibidas en los Estatutos, que resulten dañosas para la finca o que contravengan las disposiciones generales sobre actividades molestas, insalubres, nocivas, peligrosas o ilícitas».

La actuación descrita del vecino choca frontalmente con lo preceptuado en los Estatutos que rigen la vida de la Comunidad. Por este motivo entendemos que se le debe obligar a cesar en su actividad.

Tercero.— En el mismo sentido el artículo 9.1. a) y b) de la Ley de Propiedad Horizontal impone al propietario la obligación de hacer un uso adecuado de las instalaciones generales y la de mantener en buen estado de conservación el propio piso o local en términos que no perjudiquen a la Comunidad o a los otros propietarios.

Cuarto.— Se han cumplido las formalidades exigidas por la Ley consistentes, según el artículo 7.2 de la Ley de Propiedad Horizontal en:

—Requerimiento por el Presidente de la Comunidad al usuario para que cese inmediatamente su actividad, con apercibimiento de iniciar acciones judiciales si continuaba con el uso prohibido.

—Autorización de la Junta de Vecinos al Presidente para presentar demanda.

Quinto.— [COMPLETAR]. El artículo 27 de la Ley de Arrendamientos Urbanos de 1994, permite en su n.º 2.e) resolver el contrato de arrendamiento cuando se realicen en el inmueble «actividades molestas, insalubres, nocivas, peligrosas o ilícitas».

Teniendo en cuenta que el fin primordial del arrendamiento del local fue la instalación del negocio cuya actividad pretendemos que cese deberá resolverse, sin más, el contrato de arrendamiento.

Sexto.— El usuario y el propietario son responsables de los daños causados según lo establecido en el ya citado artículo 7.2 de la Ley de Propiedad Horizontal, que incluye dentro del contenido de la sentencia la valoración de los daños y perjuicios que procedan. Tal condena deberá ser conjunta y solidaria, sin perjuicio de sus relaciones internas.

Séptimo.— Artículo 1902 del Código Civil sobre la obligación de reparación de daños y perjuicios.

En aplicación del artículo 394 de la Ley de Enjuiciamiento Civil deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, admita a trámite el Letrado de la Administración de Justicia la presente demanda, y previos los trámites pertinentes con el recibimiento del juicio a prueba que expresamente se deja interesado, en su día se dicte sentencia por la que:

1.º se declare que la actividad realizada por D./Dña. [NOMBRE Y APELLIDOS],

2.º se requiera al demandado para que cese inmediatamente en el ejercicio de la actividad [COMPLETAR], extendiendo este requerimiento a D./Dña. [NOMBRE Y APELLIDOS]) para que exija del arrendatario la cesación de la actividad.

3.º [COMPLETAR],

4.º se condene a los demandados a indemnizar a la comunidad actora en la suma de [IMPORTE] euros más sus intereses legales por los daños y perjuicios causados,

5.º y se condene expresamente en costas a los demandados.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
