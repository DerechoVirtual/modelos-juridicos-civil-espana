---
name: demanda-ejecutiva-ordinaria-sin-habilitacion-fondos-908
description: "Redacta el escrito «Demanda ejecutiva ordinaria sin habilitación de fondos» (formulario 908 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva ordinaria sin habilitación de fondos

> Formulario 0908 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] IMPORTE (4 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…ribunales, que interviene en concepto de»; «…en los autos de Juicio»; «… la provisión de fondos), domiciliado en»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 592 de la LEC
- art. 29 de la LEC
- art. 517 de la LEC
- art. 549 de la LEC
- art. 548 de la LEC
- art. 550.1 de la LEC
- art. 541 de la LEC

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

### Formulario 0908 · Demanda ejecutiva ordinaria sin habilitación de fondos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, que interviene en concepto de [COMPLETAR] (demandante/demandado) en la representación de D./Dña. [NOMBRE Y APELLIDOS] y bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS] en los autos de Juicio [COMPLETAR] n.º [NÚMERO], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito formulo demanda ejecutiva contra D./Dña. [NOMBRE Y APELLIDOS] (poderdante obligado a efectuar la provisión de fondos), domiciliado en [COMPLETAR], cuyas demás circunstancias personales constan en los presentes autos, de lo dispuesto en el decreto del Letrado de la Administración de Justicia de fecha [FECHA] dictado en estos autos, con objeto de que se dicte auto despachando ejecución de conformidad con el suplico de esta demanda que baso en los siguientes

HECHOS

Mediante decreto del Letrado de la Administración de Justicia de fecha [FECHA], notificado a mi principal D./Dña. [NOMBRE Y APELLIDOS] el día [FECHA], se resolvió fijar en la suma de [IMPORTE] euros la cantidad que éste debía hacerme efectiva en concepto de provisión de fondos con los que atender a la tramitación del proceso, suma que debía hacerme efectiva en el plazo de [Nº] días.

Dicha resolución es firme al no haber sido recurrida.

Ha transcurrido el plazo concedido a mi poderdante para que me hiciese efectiva la provisión de fondos señalada sin que aquél haya tenido a bien habilitar los fondos requeridos.

En todo caso han transcurrido, también, más de veinte días hábiles desde la notificación al ejecutado del decreto cuya ejecución se pide.

Son bienes del ejecutado susceptibles de embargo los siguientes: (detallar según el orden legal —art. 592 de la LEC—).

Los bienes detallados en el ordinal precedente no parecen suficientes para cubrir las sumas reclamadas, por lo que para la localización de bienes del ejecutado con los que hacer frente a su obligación de pago aparecen como necesarias las siguientes medidas de investigación judicial

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Art. 61 de la LEC, que determina la competencia funcional por conexión. En su virtud, “el Tribunal que tenga competencia para conocer de un pleito, la tendrá también para resolver sobre sus incidencias, para llevar a efecto las providencias y autos que dictare…..". Art. 545 de la LEC, que recoge el mismo principio en cuanto a la ejecución forzosa para las resoluciones dictadas por Letrados de la Administación de Justicia.

Legitimación

Corresponde la legitimación activa al Procurador firmante y la pasiva a su poder- dante. Art. 155 de la LEC: Aun cuando en el Juicio del que deriva la solicitud de provisión de fondos interven- go como apoderado del ejecutado, al dirigir la presente demanda ejecutiva en solicitud de ejecución por vía de apremio de la habilitación fijada judicialmente contra mi poderdante deberá darse traslado de la misma a través de su domicilio, referenciado en el encabezamiento de esta demanda.

Trámite y requisitos procesales

1.º Art. 517.9.º de la LEC: reconoce ejecutividad a las resoluciones procesales que lleven aparejada ejecución por disposición de ley. El art. 29 de la LEC establece que el requerimiento de pago de la suma que deba pagarse en concepto de provisión de fondos se hará por el Letrado de la Administración de Justicia bajo “apercibimiento de apremio”. El decreto en que baso la demanda ejecutiva es, en consecuencia, incardinable en el apartado 9.º del art. 517 de la LEC.

Sólo se despachará ejecución a petición de parte y en forma de demanda con los requisitos que se desarrollan en el art. 549 de la LEC.

2.º Art. 548 de la LEC: No se despachará ejecución dentro de los veinte días siguientes a la noti- ficación al ejecutado de la resolución cuya ejecución se pide. Aun cuando en el presente supuesto dicho obligado ha dispuesto ya del propio plazo fijado en el auto que sirve de base a esta demanda en solicitud de ejecución para el abono de dicha cantidad, en evitación de dificultades interpretativas la demanda se presenta transcurrido el plazo señalado en el art. 548 de la LEC.

3.º El art. 550.1 de la LEC exime de la obligación de presentar el título cuando la ejecución se funde en resolución que obre en los autos.

4.º Arts. 551 y ss. sobre trámite para el despacho de la ejecución y oposición a la misma.

5.º Arts. 571 y ss. sobre ejecución dineraria.

Fondo

Art. 29 de la LEC: Si no pagare el deudor el importe fijado en el decreto del Letrado de la Administración de Justicia en el plazo señalado procederá hacer efectivo el apercibimiento de apremio.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, se sirva admitirlo, teniendo por formulada demanda ejecutiva en solicitud de ejecución de lo dispuesto en el decreto de fecha [FECHA] mediante el que se acuerda fijar la cantidad de [IMPORTE] euros en concepto de provisión de fondos que D./Dña. [NOMBRE Y APELLIDOS] debía haberme entregado para atender al desarrollo del proceso, acordando lo siguiente:

1.º El embargo, sin necesidad de requerimiento personal previo, de bienes del ejecutado D./Dña. [NOMBRE Y APELLIDOS] para cubrir el principal de [IMPORTE] euros señalado como provisión de fondos que debía haber habilitado más otros [IMPORTE] euros que se consideran bastantes por ahora para cubrir las costas de esta ejecución,

2.º dictar, en su día y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante,

3.º hacer trance y remate de los bienes embargados y pagar con el importe obtenido al Procurador firmante el principal reclamado, intereses, gastos y costas causadas y que se causen hasta el completo pago, que deberán ser impuestos al ejecutado D./Dña. [NOMBRE Y APELLIDOS]

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Opcionalmente puede añadirse:

OTROSÍ DIGO: Que a los fines prevenidos en el art. 541 de la LEC y a los efectos previstos en la legislación hipotecaria,

NUEVAMENTE SUPLICO AL TRIBUNAL: Se sirva notificar la presente demanda al cónyuge del demandado, D./Dña. [NOMBRE Y APELLIDOS], en el mismo domicilio que el del ejecutado por ser justicia que reitero en igual lugar y fecha.)

========================================================================
