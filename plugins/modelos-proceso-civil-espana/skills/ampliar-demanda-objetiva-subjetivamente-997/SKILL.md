---
name: ampliar-demanda-objetiva-subjetivamente-997
description: "Redacta el escrito «Ampliar la demanda, objetiva y subjetivamente» (formulario 997 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ampliar la demanda, objetiva y subjetivamente

> Formulario 0997 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] CALLE
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio ordinario»; «…igación asumida en contrato celebrado en»; «…patibles, pues ambas son personales y de»; «…n de cantidad, cumplimiento de contrato,»; «…taba cubierta por la Compañía de Seguros»; «…, según n.º [Nº] de póliza»; «…L: Que tenga por presentado este escrito»; «… acuerde dar traslado de esta ampliación»; «…venga a su derecho; o al nuevo demandado»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 401.2 de la LEC
- art. 71.2 de la LEC
- art. 72 de la LEC

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

### Formulario 0997 · Ampliar la demanda, objetiva y subjetivamente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio ordinario [COMPLETAR] / A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE [LOCALIDAD], PLAZA N.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:Que mediante el presente escrito y en aplicación del art. 401.2 de la LEC procedo a ampliar la demanda presentada por esta parte en fecha [FECHA] contra D./Dña. [NOMBRE Y APELLIDOS] en los siguientes términos:(Opciones):— Interesa a esta parte reclamar de forma acumulada a la pretensión ya fijada, el pago de [IMPORTE] euros al que deberá hacer frente el demandado como consecuencia del incumplimiento de su obligación asumida en contrato celebrado en [COMPLETAR] (lugar) de fecha [FECHA], y cuyo plazo de cumplimiento ha finalizado el día [FECHA], es decir en fecha posterior a la interposición de la demanda. Tal y como se puede apreciar en el documento que acompañamos, la relación objeto de este contrato, y la del contrato que se presentó eran similares y tenían carácter periódico. El demandado incumplió la primera y lo mismo ha pasado ahora con la segunda, tal como se acredita con el acta notarial que acompañamos como doc.n.º Existe unidad de objeto y sujetos y por tanto el art. 71.2 de la LEC permite acumular las acciones. Nos encontramos con dos acciones compatibles, pues ambas son personales y de [COMPLETAR] (reclamación de cantidad, cumplimiento de contrato, [COMPLETAR])— Esta parte ha tenido conocimiento después de presentar la demanda de que la actividad realizada por el demandado que ha causado los daños cuya reparación se pretende, estaba cubierta por la Compañía de Seguros [COMPLETAR], que tiene sede en esta ciudad en la C/ [CALLE], según n.º [Nº] de póliza [COMPLETAR] El art. 72 de la LEC permite acumular acciones que uno tenga contra varios sujetos. En este caso la responsabilidad directa y solidaria de la aseguradora deriva de los arts. 18 y 19 de la Ley de contrato de seguro. Así las cosas deberá darse traslado de la demanda y de esta ampliación a esta entidad a fin de que tenga conocimiento de la misma y actúe conforme le convenga en Derecho.

Deberá abrirse de nuevo plazo para contestar por 20 días cuando se dé traslado de esta ampliación a la otra parte.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito [COMPLETAR] (en su caso, con los documentos que acompaño) y copia de todo ello, lo admita y previos los trámites oportunos acuerde dar traslado de esta ampliación [COMPLETAR] (al demandado a fin que tenga conocimiento de la nueva acción ejercitada contra él y proceda según convenga a su derecho; o al nuevo demandado [COMPLETAR] a fin de que sea condenado de forma directa y solidaria junto con D./Dña. [NOMBRE Y APELLIDOS] a todas y cada una de las pretensiones pormenorizadas en el suplico de la demanda).

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
