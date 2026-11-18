---
name: comunicar-nuevo-domicilio-deudor-pedir-requerimiento-260
description: "Redacta el escrito «Comunicar nuevo domicilio del deudor y pedir requerimiento de pago por auxilio judicial» (formulario 260 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Comunicar nuevo domicilio del deudor y pedir requerimiento de pago por auxilio judicial

> Formulario 0260 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NÚMERO
- [ ] FECHA
- [ ] SEDE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 815 LEC
- arts. 172.3 y 174.1 LEC

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

### Formulario 0260 · Comunicar nuevo domicilio del deudor y pedir requerimiento de pago por auxilio judicial

- Año del modelo: 2020
- Revisión 17-11-2026: 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito comunicando al Letrado de la Administración de Justicia nuevo domicilio del deudor y solicitando la práctica del requerimiento de pago vía auxilio judicial tras resultado negativo de la diligencia de requerimiento de pago efectuada en el domicilio del deudor consignado en el escrito de petición inicial del proceso monitorio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según consta acreditado en los autos de juicio monitorio que se sigue en este Tribunal con el nº [NÚMERO] a instancias de esta parte y contra D./Dña. [NOMBRE Y APELLIDOS], ante el mismo comparezco y como mejor proceda en derecho, DIGO:

Que habiendo sido notificado a mi mandante, con fecha [FECHA], diligencia del Letrado de la Administración de Justicia poniendo en conocimiento de esta parte el resultado negativo de la diligencia de requerimiento de pago efectuada en el domicilio del deudor consignado en el escrito de petición inicial de los presentes autos, instando a esta representación a manifestar lo que a su derecho conviniere, por medio del presente escrito, y dentro del plazo concedido al efecto, formulo las siguientes:

ALEGACIONES

PRIMERA.- Que una vez practicadas las averiguaciones oportunas, esta parte ha conocido que, con posterioridad a la presentación de la petición inicial del procedimiento monitorio, el deudor ha cambiado de domicilio, siendo su actual dirección la siguiente:

Se facilita, así mismo, su número de teléfono, fax, y correo electrónico:

SEGUNDA.- Que dado que el mencionado domicilio se encuentra fuera de la circunscripción de este Tribunal, interesa a esta parte que el requerimiento de pago al que se refiere el art. 815 LEC se verifique mediante auxilio judicial, de conformidad con lo dispuesto en los arts. 165 y ss. LEC, librándose exhorto a la Oficina Judicial del Tribunal de Instancia de [SEDE] para que se lleve a cabo dicho requerimiento.

A estos efectos, se designa a D./Dña. [NOMBRE Y APELLIDOS] como Procurador/a habilitado/a para actuar ante dicha Oficina Judicial, con el fin de que le sean notificadas las resoluciones dictadas para el cumplimiento del exhorto de acuerdo con lo dispuesto en los arts. 172.3 y 174.1 LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL,

tenga por presentado este escrito, con sus copias, y teniendo por causadas las anteriores manifestaciones en la representación que ostento, se sirva admitirlo, y en mérito a lo manifestado, se considere evacuado el trámite conferido, acordando conforme se interesa, y en su consecuencia se dicte resolución por la que se dé a los autos el curso legalmente previsto

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

Firma de Procurador
