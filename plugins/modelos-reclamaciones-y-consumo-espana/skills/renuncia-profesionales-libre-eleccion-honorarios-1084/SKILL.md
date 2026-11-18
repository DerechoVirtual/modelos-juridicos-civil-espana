---
name: renuncia-profesionales-libre-eleccion-honorarios-1084
description: "Redacta el escrito «Renuncia de profesionales de libre elección a honorarios o derechos» (formulario 1084 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Renuncia de profesionales de libre elección a honorarios o derechos

> Formulario 1084 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] COLEGIO (2 veces)
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº (2 veces)
- [ ] ÓRGANO
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de colegiado»; «…de colegiado»; «…llo, solicito la designación directa del»; «…(Letrado, Procurador) que suscribe, para»; «…en el juicio de»; «…s, renuncio expresamente ante el Colegio»; «…(ABOGADOS, PROCURADORES) DE»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 27 de la Ley 1/1996

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

### Formulario 1084 · Renuncia de profesionales de libre elección a honorarios o derechos

- Año del modelo: 2013
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Opciones:

AL ILTRE. COLEGIO DE ABOGADOS DE [COLEGIO] AL ILTRE. COLEGIO DE PROCURADORES DE [COLEGIO]

D./Dña. [NOMBRE Y APELLIDOS], (Letrado en ejercicio del Iltre. Colegio al que me dirijo, con n.º [Nº] de colegiado [COMPLETAR], o Procurador de los Tribunales, con n.º [Nº] de colegiado [COMPLETAR]), ante ese Iltre. Colegio comparece y EXPONE:

Que en aplicación de los arts. 27 de la Ley 1/1996, de 10 de enero, de Asistencia Jurídica Gratuita y 36.1 de su Reglamento de desarrollo, solicito la designación directa del [COMPLETAR] (Letrado, Procurador) que suscribe, para [COMPLETAR] (asistir o representar) a D./Dña. [NOMBRE Y APELLIDOS] en el juicio de [COMPLETAR], seguido ante [ÓRGANO] contra D./Dña. [NOMBRE Y APELLIDOS]

A estos efectos se acompaña este escrito a la solicitud del reconocimiento del derecho a la asistencia jurídica gratuita de D./Dña. [NOMBRE Y APELLIDOS]

Al ser libremente elegidos, renuncio expresamente ante el Colegio [COMPLETAR] de (Abogados, Procurado- res) y ante D./Dña. [NOMBRE Y APELLIDOS] (cliente) a percibir de éste los honorarios y derechos que pudieran corresponderme y que él debería abonar, siempre que se le reconozca el derecho instado.

Por lo expuesto,

SOLICITO AL ILTRE. COLEGIO DE [LOCALIDAD] (ABOGADOS, PROCURADORES) DE [COMPLETAR]:

Que tenga por presentado este escrito que acompaña a la solicitud de reconocimiento de derecho a la asistencia jurídica gratuita de D./Dña. [NOMBRE Y APELLIDOS] y por hechas las manifestaciones de renuncia a percibir de D./Dña. [NOMBRE Y APELLIDOS] (solicitante de la justicia gratuita) los honorarios y derechos que éste hubiera de venir obligado a hacer efectivos a este profesional si se le reconoce el derecho a la asistencia jurídica gratuita, acordando la designación directa de D./Dña. [NOMBRE Y APELLIDOS] como (Abogado, Procurador).

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
