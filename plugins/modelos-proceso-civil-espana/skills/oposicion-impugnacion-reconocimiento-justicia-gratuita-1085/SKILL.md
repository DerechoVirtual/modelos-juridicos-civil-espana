---
name: oposicion-impugnacion-reconocimiento-justicia-gratuita-1085
description: "Redacta el escrito «Oposición a la impugnación del reconocimiento de justicia gratuita» (formulario 1085 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la impugnación del reconocimiento de justicia gratuita

> Formulario 1085 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE
- [ ] MATRÍCULA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…mite para la percepción del derecho, así»; «…euros, es titular de un vehículo»; «…y su trabajo como»; «… litigar en defensa de intereses propios»; «… para el reconocimiento del derecho, así»; «…), ni que el vehículo»; «… litigar en defensa de intereses propios»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 20 de la Ley 1/1996

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

### Formulario 1085 · Oposición a la impugnación del reconocimiento de justicia gratuita

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], cuyas circunstancias personales ya constan en autos de impugnación de resolución de reconocimiento del derecho a la asistencia jurídica gratuita n.º [NÚMERO], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y, amparándome en el art. 20 de la Ley 1/1996, de Asistencia Jurídica Gratuita, formulo oposición a la impugnación planteada de contrario, basándome en las siguientes

ALEGACIONES

Opciones:

I. Si el que impugnó es el demandante de la asistencia jurídica gratuita y se opone el contrario en el proceso principal:

PRIMERA.— Debe mantenerse la resolución recurrida que deniega el derecho a la asistencia jurídica gratuita a D./Dña. [NOMBRE Y APELLIDOS], ya que se fundamenta correctamente en la propia documentación por él aportada a los autos. De ésta se deduce que la unidad familiar supera los ingresos establecidos como límite para la percepción del derecho, así [COMPLETAR] (se computan todos ellos). A efectos probatorios dejamos acotados los archivos de la Delegación de Hacienda y del INEM.

SEGUNDA.— En todo caso y en aplicación del art. 4.º de la Ley 1/1996, de Asistencia Jurídica Gratuita hay que tener en cuenta que de los signos externos del modo de vida de D./Dña. [NOMBRE Y APELLIDOS] se deduce que éste necesariamente ha de tener unos ingresos que superen la cifra que afirmó, pues es propietario de una vivienda en una zona céntrica, de un valor aproximado de [IMPORTE] euros, es titular de un vehículo [COMPLETAR] y su trabajo como [COMPLETAR] le proporciona, además de los ingresos fijos, dietas de

TERCERA.— Respecto al requisito necesario del art. 3.º de la citada Ley sobre la necesidad de litigar en defensa de intereses propios [COMPLETAR] (alegaciones que contradigan la afirmación del contrario).

II. Si el que impugnó es el contrario en el proceso principal y se opone el demandante de la asistencia jurídica gratuita:

PRIMERA.— Debe mantenerse la resolución recurrida que me concede el derecho a la asistencia jurídica gratuita, ya que se fundamenta correctamente en la propia documentación aportada a los autos y de la que se deduce que la unidad familiar tiene unos ingresos que por todos los conceptos no superan el doble del indicador público de la renta a efectos múltiples, cifra límite para el reconocimiento del derecho, así [COMPLETAR] (se computan todos ellos).

SEGUNDA.— El art. 4.º de la Ley 1/1996 de Asistencia Jurídica Gratuita excluye este derecho, tal como se afirma de contrario, cuando de los signos externos del modo de vida del solicitante se deduce que éste necesariamente ha de tener unos ingresos que superen la cifra indicada, pero no es cierto que la vivienda que habito sea de mi propiedad sino que ésta ha sido cedida temporalmente por un familiar (doc. n.º [NÚMERO]), ni que el vehículo [COMPLETAR] sea de excesivo valor pues hay que tener en cuenta que por su matrícula [MATRÍCULA], tiene un valor venal de

TERCERA.— Respecto al requisito necesario del art. 3.º de la citada Ley sobre la necesidad de litigar en defensa de intereses propios [COMPLETAR] (alegaciones que confirmen lo expuesto).

Común:

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, lo admita y tenga por hechas las manifestaciones anteriores en el sentido de oponerme a la impugnación de la resolución n.º [NÚMERO] del expediente n.º [NÚMERO] dictada por la Comisión de Asistencia Jurídica Gratuita.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
