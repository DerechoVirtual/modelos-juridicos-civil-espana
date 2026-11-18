---
name: autorizacion-judicial-fecundacion-post-mortem-material-130
description: "Redacta el escrito «Autorización judicial de fecundación post mortem con material del cónyuge fallecido» (formulario 130 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial de fecundación post mortem con material del cónyuge fallecido

> Formulario 0130 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (5 veces)
- [ ] NÚMERO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…numeración del juzgado de procedencia).]»; «…al reproductor de su cónyuge fallecido D»; «…, depositado en la clínica»; «… representada es cónyuge del fallecido D»; «…difunto cónyuge depositado en la clínica»; «…i representada contrajo matrimonio con D»; «…. (acompaño como documentos»; «… criopreservación de semen en la clínica»; «…umana asistida. (acompaño como documento»; «…pública ante el notario de esta ciudad D»; «…teresadas en el expediente, son: Clínica»; «… del material reproductor de su marido D»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 9 de la Ley 14/2006
- art. 14.2 LJV
- art. 1 de la LJV
- art. 3 de la LJV
- art. 9.2 de la Ley 14/2006

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

### Formulario 0130 · Autorización judicial de fecundación post mortem con material del cónyuge fallecido

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 28 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D/Dª [NOMBRE Y APELLIDOS], según acredito por apoderamiento apud-acta que acompaño, y bajo la dirección Letrada de D/Dª [NOMBRE Y APELLIDOS], ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito promueve expediente de jurisdicción voluntaria para la AUTORIZACIÓN JUDICIAL PARA TRATAMIENTO DE FECUNDACIÓN de mi representada con el material reproductor de su cónyuge fallecido D [COMPLETAR], depositado en la clínica [COMPLETAR], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO.- Mi representada es cónyuge del fallecido D [COMPLETAR], solicitando por medio de la presente que se autorice judicialmente el tratamiento de fecundación mediante inseminación artificial con el material reproductor de su difunto cónyuge depositado en la clínica [COMPLETAR].

Mi representada contrajo matrimonio con D [COMPLETAR] en fecha [FECHA], con quien convivió hasta el momento de su defunción, no estando en situación de separación legal ni de hecho.

El cónyuge de mi representada falleció el día [FECHA].

(acompaño como documentos [COMPLETAR] certificados del Registro Civil de inscripción de matrimonio y de defunción del cónyuge de mi representada).

SEGUNDO.- La autorización que se solicita se refiere al material reproductor que es objeto del contrato de criopreservación de semen en la clínica [COMPLETAR], perfeccionado entre el difunto cónyuge de mi representada y el legal representante de la citada clínica., suscrito en fecha [FECHA], en el cual se dispuso que el citado cónyuge fallecido depositaba su material reproductor, con la finalidad de su conservación a largo plazo mediante técnicas de criopreservación, ante el diagnóstico que presentaba el cónyuge de mi representada por la enfermedad terminal que padecía.

En el citado contrato, se pactó que, en el supuesto del óbito del cedente del material reproductor, su cónyuge podría solicitar la utilización del semen para su fecundación, siempre que se diesen los requisitos establecidos en el artículo 9 de la Ley 14/2006, de 26 de mayo, sobre técnicas de reproducción humana asistida.

(acompaño como documento [COMPLETAR] contrato de criopreservación de semen de fecha [FECHA]).

TERCERO.- A la vista de la enfermedad terminal del marido de mi representada, en fecha [FECHA], en concordancia con la voluntad expresada en el contrato referido en el hecho anterior, éste otorgó escritura pública ante el notario de esta ciudad D [COMPLETAR], en el cual expresaba que autorizaba a su esposa para que accediera al material reproductor antes expresado a fin de someterse a tratamiento de fecundación, incluso con posterioridad a producirse su fallecimiento, tal como se acredita con el documento que se acompaña como número [NÚMERO].

Este consentimiento fue prestado por el marido, de forma libre y consciente, constante la situación de convivencia del matrimonio, y con la voluntad de que mi representada pudiera acceder al material reproductor cuando falleciera para someterse al proceso de reproducción asistida, tal como se acreditará por la información testifical que se ofrece en el otrosí de esta solicitud.

CUARTO.- La vigente Ley 14/2006 contempla la fecundación post mortem siempre que haya sido autorizada por el marido en testamento, escritura pública o en el documento al que hace referencia en el artículo 6.3, es decir, el de autorización a la esposa para que se someta a tratamiento, y el documento de instrucciones previas, siendo que el difundo marido de mi representada expresó su consentimiento de forma indubitada y consciente para el uso de su material genético después de su muerte, lo cual expresó asimismo en el contrato de crioconservación, por lo que procede que se autorice judicialmente la fecundación post mortem con el material reproductor del difunto Sr. [NOMBRE Y APELLIDOS], según la voluntad expresada en los citados documentos.

QUINTO.- A los efectos del art. 14.2 LJV, debo hacer constar que las entidades y personas que pueden estar interesadas en el expediente, son:

Clínica [COMPLETAR], con domicilio en [LOCALIDAD].

FUNDAMENTOS DE DERECHO

PRIMERO.- COMPETENCIA

. El art. 1 de la LJV establece que se consideran expedientes de jurisdicción voluntaria a todos aquellos que requieran la intervención de un órgano jurisdiccional para la tutela de derechos e intereses en materia de Derecho civil sin que exista controversia que deba sustanciarse en un proceso contencioso, siendo competentes objetiva y territorialmente los Tribunales de Instancia de esta ciudad.

SEGUNDO.- PROCEDIMIENTO

. El procedimiento a seguir en el presente supuesto es el de jurisdicción voluntaria, regulado en los arts. 14 y siguientes de la LJV.

TERCERO.- LEGITIMACIÓN

. Mi representada está legitimada en su condición de titular de un derecho e interés legítimo, tal como se establece en el art. 3 de la LJV.

CUARTO.- FUNDAMENTOS DE FONDO

. El art. 9.2 de la Ley 14/2006, de 26 de mayo, sobre técnicas de reproducción humana asistida, establece: “el marido podrá prestar su consentimiento, en el documento a que se hace referencia en el artículo 6.3, en escritura pública, en testamento o documento de instrucciones previas, para que su material reproductor pueda ser utilizado en los 12 meses siguientes a su fallecimiento para fecundar a su mujer. Tal generación producirá los efectos legales que se derivan de la filiación matrimonial. El consentimiento para la aplicación de las técnicas en dichas circunstancias podrá ser revocado en cualquier momento anterior a la realización de aquéllas. Se presume otorgado el consentimiento a que se refiere el párrafo anterior cuando el cónyuge supérstite hubiera estado sometido a un proceso de reproducción asistida ya iniciado para la transferencia de preembriones constituidos con anterioridad al fallecimiento del marido. La aplicación de ambos preceptos, de acuerdo al principio de protección de la persona con discapacidad y de la voluntad expresada por la misma”.

Por lo expuesto,

AL TRIBUNAL SUPLICO: Que tenga por presentado este escrito con los documentos que se acompañan, lo admita, y tenga por promovido expediente de jurisdicción voluntaria de autorización para el tratamiento de fecundación de mi representada y, practicadas las diligencias oportunas con intervención del Ministerio Fiscal, con citación de las personas interesadas expresadas en el hecho cuarto de esta solicitud, y previos los demás trámites con arreglo a Derecho, dicte resolución en la que se autorice judicialmente la utilización del material reproductor de su marido D [COMPLETAR] para la fecundación de mi representada, el cual se encuentra depositado en la clínica [COMPLETAR].

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL: tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

OTROSÍ SEGUNDO DIGO que acreditar la certeza de los hechos relatados, solicito que en la comparecencia sean oídos y propongo los siguientes testigos para acreditar la certeza de los hechos expresados:

- D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]

-

SUPLICO AL TRIBUNAL: tenga por propuestos a los testigos indicados, solicitando que sean citados por la Oficina Judicial para la práctica de la prueba en la comparecencia.

Es Justicia que insto en [COMPLETAR]

Firma de procurador y letrado.
