---
name: rendicion-cuentas-tutor-curador-ante-tribunal-117
description: "Redacta el escrito «Rendición de cuentas del tutor o curador ante el Tribunal» (formulario 117 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Rendición de cuentas del tutor o curador ante el Tribunal

> Formulario 0117 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (5 veces)
- [ ] AÑO (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…fin, se adjuntan como documentos números»; «…nº [NÚMERO] de»; «…. -»; «…de»; «…de [COMPLETAR], al Tomo»; «… [COMPLETAR], al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…nº [NÚMERO] de -»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 43.3 LJV
- art. 51 LJV

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

### Formulario 0117 · Rendición de cuentas del tutor o curador ante el Tribunal

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del tutor o curador presentando al Tribunal rendición de cuentas por su administración tras el cese en su cargo. Aunque en el modelo se comparece por medio de procurador, conforme al art. 43.3 LJV, no es preceptiva la postulación técnica.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], tutor/curador designado en resolución de fecha [FECHA], según tengo acreditado en los autos de expediente de jurisdicción voluntaria n.º [Nº]/[AÑO] seguidos en este Tribunal, ante el mismo comparezco y como mejor en derecho proceda DIGO:

Que en cumplimiento de lo establecido en el art. 232 (en caso de tutela) /292 (en caso de curatela) CCiv y en el plazo establecido al efecto, habiendo cesado mi mandante en el ejercicio de su cargo como tutor/curador de D./Dña. [NOMBRE Y APELLIDOS] por los motivos que constan en los citados autos, por medio del presente escrito, conforme a los trámites establecidos en el art. 51 LJV, vengo a presentar RENDICIÓN DE LA CUENTA GENERAL JUSTIFICADA DE LA ADMINISTRACIÓN DEL PATRIMONIO del que fuera mi pupilo.

A tal fin, se adjuntan como documentos números [COMPLETAR], detallando a continuación el estado de los ingresos y gastos acumulados durante el ejercicio del cargo, teniendo en cuenta el inventario de bienes inicial que consta en autos y que reproducimos con en este escrito con el fin de facilitar la interpretación de la rendición de cuentas:

I. INVENTARIO INICIAL

a) Dinero en efectivo:

b) Efectos públicos y valores mobiliarios:

c) Alhajas:

d) Semovientes:

e) Frutos:

- Renta arrendaticia mensual por importe de [IMPORTE] euros correspondiente al alquiler del piso sito en calle [CALLE] nº [NÚMERO] de [COMPLETAR] que satisface el inquilino Sr./a. según contrato de arrendamiento de fecha [FECHA].
- [COMPLETAR]

f) Muebles:

g) Inmuebles:

- Finca registral nº [NÚMERO] inscrita al Registro de la Propiedad nº [NÚMERO] de [COMPLETAR], al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], que se corresponde con el piso sito en la calle [CALLE] nº [NÚMERO] de
- [COMPLETAR]

h) Derechos y acciones:

i) Otros bienes:

II. VARIACIONES RESPECTO AL INVENTARIO INICIAL

Bien/Valor afectado	Operación	Fecha	Importe

TOTAL			L

III. INGRESOS

Descripción	Fecha	Importe anual
Alimentación
Educación
Gastos médicos
TOTAL

IV. DESTINO DE LOS INGRESOS OBTENIDOS

Descripción	Fecha	Importe anual
Reinversiones
Gastos de mantenimiento de inversiones

V. GASTOS CORRIENTES POR CUENTA DEL PUPILO

Descripción	Fecha	Importe anual
Pensiones
Rentas del capital mobiliario
Rentas del capital inmobiliario
Otros
TOTAL

Diferencia ingresos-gastos:

Como resulta de los justificantes aportados, resulta una cantidad remanente a favor de D./D.ª [NOMBRE Y APELLIDOS] de [IMPORTE] euros, que en fecha [FECHA] ha sido ingresada en su libreta de ahorros y que constituye la última anotación de ésta.

En su virtud,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito y los documentos acompañados y copia de todo ello, se sirva admitirlos y, previos los trámites legales, dicte resolución aprobando la RENDICIÓN DE CUENTAS POR CESE DE FUNCIONES DEL TUTOR/CURADOR SOBRE LA ADMINISTRACIÓN Y GESTIÓN DE LOS BIENES DE D./Dña. [NOMBRE Y APELLIDOS], tal y como consta en el expediente de jurisdicción voluntaria referenciado, correspondiente al periodo comprendido desde la asunción del cargo de tutor/curador el día [FECHA] hasta el cese en el mismo, el día [FECHA]

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Procurador
