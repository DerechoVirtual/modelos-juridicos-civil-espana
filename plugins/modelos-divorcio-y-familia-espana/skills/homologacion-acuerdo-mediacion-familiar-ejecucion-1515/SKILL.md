---
name: homologacion-acuerdo-mediacion-familiar-ejecucion-1515
description: "Redacta el escrito «Homologación de acuerdo de mediación familiar en ejecución de medidas definitivas» (formulario 1515 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Homologación de acuerdo de mediación familiar en ejecución de medidas definitivas

> Formulario 1515 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de [COMPLETAR] de»; «…ste proceso de divorcio en cuyo apartado»; «…de»; «…de [COMPLETAR] de»; «…sladado por su empresa a la localidad de»; «…ará a los hijos a la estación de tren de»; «…e los recogerá en la estación de tren de»; «…de la sesión constitutiva como documento»; «…en de visitas establecido en el apartado»; «…en de visitas establecido en el apartado»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

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

### Formulario 1515 · Homologación de acuerdo de mediación familiar en ejecución de medidas definitivas

- Año del modelo: 2014
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 17 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
DECIMOS
Suplico
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

Proceso de divorcio número [NÚMERO]

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación del ejecutante D. [NOMBRE Y APELLIDOS], y D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación del ejecutado D. [NOMBRE Y APELLIDOS], cuya representación tenemos acreditada en los autos arriba referenciados, comparecemos con la asistencia, respectivamente, de los Letrados D. y D. [NOMBRE Y APELLIDOS], y como mejor proceda en derecho

DECIMOS

Que en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se dictó sentencia firme en este proceso de divorcio en cuyo apartado [COMPLETAR] se fijaba un régimen de visitas de fines de semana alternos a favor del padre, quien debía recoger a los hijos en el domicilio de la madre y de éstos.

Que el pasado día [FECHA] de [COMPLETAR] de [COMPLETAR] el padre fue trasladado por su empresa a la localidad de [COMPLETAR], lo cual dificultaba gravemente el cumplimiento del régimen de visitas fijado en la sentencia.

Que las partes a las que representamos, ante esta vicisitud y en interés de los hijos, acordaron someterse a mediación para fijar un régimen de visitas compatible con esta nueva situación y han llegado a un acuerdo consistente en que las visitas se realicen un fin de semana cada mes, que corresponderá al segundo fin de semana, salvo que las obligaciones de los hijos lo impidan, en cuyo caso se realizarán el fin de semana siguiente, y, en orden a su cumplimiento, que la madre acompañará a los hijos a la estación de tren de [COMPLETAR] los viernes por la tarde y que el padre los recogerá en la estación de tren de [COMPLETAR], reintegrándose al domicilio familiar por el mismo procedimiento inverso el domingo por la tarde; todos los gastos del viaje serán sufragados por el padre (acompañamos a este escrito el referido acuerdo de mediación plasmado en el acta final extendida por el mediador familiar D. [NOMBRE Y APELLIDOS] y debidamente firmado por los litigantes como documento número [Nº DE DOCUMENTO], así como el acta de la sesión constitutiva como documento [COMPLETAR]).

Que habida cuenta de lo anterior, y no implicando el convenio suscrito una modificación sustancial de las medidas decretadas en la sentencia y estando realizado en interés de los menores, por medio del presente escrito solicitamos su homologación, a fin de que sustituya exclusivamente el régimen de visitas establecido en el apartado [COMPLETAR] de la sentencia dictada en este proceso.

Por lo expuesto, AL TRIBUNAL SUPLICO que tenga por presentado este escrito, acuerdo de mediación y documentos acompañados, solicitando dicte auto homologando el acuerdo de mediación en sustitución del régimen de visitas establecido en el apartado [COMPLETAR] de la sentencia dictada en este proceso.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogados y Procuradores

========================================================================
