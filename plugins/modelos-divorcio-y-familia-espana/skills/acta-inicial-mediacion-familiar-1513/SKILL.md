---
name: acta-inicial-mediacion-familiar-1513
description: "Redacta el escrito «Acta inicial de mediación familiar» (formulario 1513 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta inicial de mediación familiar

> Formulario 1513 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LUGAR (2 veces)
- [ ] DÍA (2 veces)
- [ ] MES (2 veces)
- [ ] AÑO (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mediador de la institución»; «…, con el numero,»; «…terno filiales, habiendo sido informados»; «…de guarda y visitas de los hijos comunes»; «…y»; «…y [COMPLETAR], de»; «…ar desde la firma del presente documento»; «…vienen que la mediación se desarrolle en»

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

### Formulario 1513 · Acta inicial de mediación familiar

- Año del modelo: 2014
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Fecha y mediador
MANIFIESTA
Términos
Firmas

ACTA INICIAL DE LA MEDIACIÓN

En [LUGAR], a [DÍA] de [MES] de [AÑO].

D. [NOMBRE Y APELLIDOS], mediador de la institución [COMPLETAR], con el numero, [COMPLETAR]

MANIFIESTA

Que la citada comparecencia lo ha sido a efectos de ser informados de la mediación familiar que pueden iniciar para resolver las controversias derivadas del cese de la convivencia conyugal, tanto en el aspecto económico como en las relaciones paterno filiales, habiendo sido informados [COMPLETAR] sobre sus derechos y deberes, principios rectores de la mediación, de las características del procedimiento, de su duración y de los honorarios profesionales.

Que, a la vista de la información recibida, manifiestan que tienen la intención de resolver el conflicto por vía extrajudicial y aceptan desarrollar la mediación para la resolución del conflicto planteado en el proceso antes expresado dentro de los siguientes

Términos

Designación de mediador

Ambas partes de común acuerdo designan como mediador a quien suscribe D. [NOMBRE Y APELLIDOS], cuyas circunstancias constan en el encabezamiento.

Objeto del conflicto que se somete a mediación

Que el conflicto que se somete a mediación es el derivado del cese de la convivencia conyugal de ambas partes a fin de regular lo procedente sobre los efectos personales y patrimoniales derivados de la disolución de su matrimonio que tienen intención de instar judicialmente y en especial:

- Ejercicio de la patria potestad y régimen de guarda y visitas de los hijos comunes [COMPLETAR] y [COMPLETAR], de [COMPLETAR] y [Nº] años de edad respectivamente.

- Pensión económica que debe satisfacerse en su caso en concepto de alimentos y educación de los hijos comunes.

- Atribución del domicilio familiar.

- Aspectos patrimoniales derivados de la disolución del matrimonio y de la liquidación del régimen de gananciales.

Programa de actuaciones y duración máxima del procedimiento

El programa de actuaciones comprenderá las sesiones de mediación que pudieran ser necesarias (individuales y/o conjuntas) a criterio del mediador, en atención al principio de flexibilidad y al principio de igualdad.

Las partes acuerdan que el plazo de duración máxima del procedimiento de mediación será de [Nº] meses a contar desde la firma del presente documento [COMPLETAR]

Coste de la mediación

El coste de la mediación se dividirá por igual entre las partes firmantes, y se abonará a la finalización del procedimiento.

El coste de la mediación incluirá los honorarios del mediador a razón de [IMPORTE] euros por sesión, con una cifra máxima de [IMPORTE] euros.

Aceptación y asunción de obligaciones

Las partes declaran haber sido informadas acerca de las características básicas de la mediación, Y manifiestan su voluntad de participar en la mediación y asumir las obligaciones que de ella se deriven, observando el deber de confidencialidad en relación a cualquier documento o manifestación que se realice en el procedimiento, salvo el acuerdo total o parcial que pudiera alcanzarse, y tanto las partes, como el mediador se comprometen a aceptar y cumplir estos principios básicos.

Lugar de celebración y lengua del procedimiento

Que ambas partes convienen que la mediación se desarrolle en [COMPLETAR] y que el idioma en el que se sustanciará el procedimiento será el castellano.

Y para que así conste, se extiende esta acta con un ejemplar para cada una de las partes, a uno solo efecto, al lugar y fecha indicados.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
