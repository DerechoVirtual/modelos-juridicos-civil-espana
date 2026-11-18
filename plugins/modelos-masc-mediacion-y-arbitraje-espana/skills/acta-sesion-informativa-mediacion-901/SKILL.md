---
name: acta-sesion-informativa-mediacion-901
description: "Redacta el escrito «Acta de la sesión informativa en la mediación» (formulario 901 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de la sesión informativa en la mediación

> Formulario 0901 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (3 veces)
- [ ] DNI/NIE (2 veces)
- [ ] NIF
- [ ] FECHA (2 veces)
- [ ] IMPORTE
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mediador de»; «…, mediador de [COMPLETAR] con sede en»; «…cta de sesión infor- mativa de mediación»; «…ero o el segundo en nombre de la entidad»; «…r que: - El objeto de la controversia es»; «…te de la mediación correrá por cuenta de»; «…brar sesión constitutiva de la mediación»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0901 · Acta de la sesión informativa en la mediación

- Año del modelo: 2013
- Revisión 17-11-2026: 23 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

D./Dña. [NOMBRE Y APELLIDOS], mediador de [COMPLETAR] con sede en [COMPLETAR] (en su caso), inscrito en el Registro de Mediadores e Instituciones de Mediación con el n.º [NÚMERO] emite la siguiente acta de sesión infor- mativa de mediación [COMPLETAR] (civil o mercantil) celebrada entre D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] y D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] (en su caso, el primero o el segundo en nombre de la entidad [COMPLETAR], con domicilio en [LOCALIDAD] y CIF [NIF]), haciendo constar lo siguiente:

1.º Por ambos comparecientes se presentó en fecha [FECHA] solicitud de mediación en la que se hacía constar que:

- El objeto de la controversia es [COMPLETAR] (descripción del problema)

- Su valoración económica asciende a [IMPORTE] euros.

- El coste de la mediación correrá por cuenta de [COMPLETAR] (las partes en igual proporción, D./Dña. [NOMBRE Y APELLIDOS], ...)

2.º Se citó a esta sesión informativa a la que han acudido ambas partes.

3.º En la sesión se les ha informado debidamente sobre los siguientes extremos:

- posibles causas que puedan afectar a su imparcialidad,

- de su profesión, formación y experiencia,

- de las características de la mediación, su coste, la organización del procedimiento,

- de las consecuencias jurídicas del acuerdo que se pudiera alcanzar,

- del plazo para firmar el acta de la sesión constitutiva.

Los comparecientes declaran haber comprendido toda la información recibida y manifiestan la intención de iniciar las sesiones de mediación.

4.º Acordado por los comparecientes intentar resolver su controversia mediante mediación deciden celebrar sesión constitutiva de la mediación [COMPLETAR] (en este mismo acto o para las que se les deja citados para el día [FECHA])

Y para que conste y surta efectos entre los comparecientes firmo yo el mediador D./Dña. [NOMBRE Y APELLIDOS], junto con los comparecientes, en el lugar y fecha del encabezamiento.

Firmas

========================================================================
