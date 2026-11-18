---
name: oposicion-concesion-justicia-gratuita-882
description: "Redacta el escrito «Oposición a la concesión de justicia gratuita» (formulario 882 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la concesión de justicia gratuita

> Formulario 0882 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] NÚMERO (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA»; «…io de justicia gratuita), mayor de edad,»; «…(ciudad),»; «…(solicitante)»; «…nte escrito, con los que se acredita que»; «…ia jurídica gratuita en el procedimiento»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 17 de la Ley 1/1996

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

### Formulario 0882 · Oposición a la concesión de justicia gratuita

- Año del modelo: 2013
- Revisión 17-11-2026: 15 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

A LA COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS] (oponente a la concesión del beneficio de justicia gratuita), mayor de edad, [COMPLETAR] (estado civil), con domicilio en [LOCALIDAD] (ciudad), [COMPLETAR] (calle) y DNI n.º [DNI/NIE], ante la Comisión comparece en el expediente de asistencia jurídica gratuita n.º [NÚMERO] y como mejor proceda en derecho EXPONE:

Que mediante el presente escrito y en aplicación de los arts. 17 de la Ley 1/1996, de 10 de enero, de Asistencia Jurídica Gratuita y 16.3 de su Reglamento de desarrollo, procedo a OPONERME a la concesión de este derecho al solicitante D./Dña. [NOMBRE Y APELLIDOS], apoyando mi pretensión en las siguientes:

ALEGACIONES

No es cierto que D./Dña. [NOMBRE Y APELLIDOS] (solicitante) [COMPLETAR] (citar hechos o circunstancias que se rebaten), tal como se acredita con los documentos n.º [NÚMERO] que adjunto al presente escrito, con los que se acredita que [COMPLETAR] (hechos o circunstancias que se afirman).

De lo expuesto se infiere claramente que los ingresos del demandante superan la cuantía del doble del indicador público de la renta a efectos múltiples y que por tanto se le deberá denegar este derecho.

Por lo expuesto,

SOLICITO A LA COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA: Que tenga por presentado este escrito con los documentos que acompaño, lo admita y, previos los trámites legales oportunos y en virtud de las alegaciones practicadas, acuerde denegar a D./Dña. [NOMBRE Y APELLIDOS] el derecho a la asistencia jurídica gratuita en el procedimiento [COMPLETAR] tramitado ante el Tribunal n.º [Nº]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
