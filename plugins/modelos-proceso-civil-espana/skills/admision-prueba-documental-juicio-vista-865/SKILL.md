---
name: admision-prueba-documental-juicio-vista-865
description: "Redacta el escrito «Admisión de la prueba documental en el juicio o vista» (formulario 865 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Admisión de la prueba documental en el juicio o vista

> Formulario 0865 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] Nº (3 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, plaza n.º»; «…cédulas hipotecarias suscritas por D, en»

## Correcciones de la revisión (1)

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

### Formulario 0865 · Admisión de la prueba documental en el juicio o vista

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 13 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Autos n.º [NÚMERO]

MEDIOS DE PRUEBA que propone para su práctica D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en los autos referenciados:

DOCUMENTAL

1.º Que se unan definitivamente a autos los documentos (aportados por esta parte con —la demanda o la contestación a la demanda— o que se aportan por esta parte al contestar a la demanda).

2.º Que se unan a autos los documentos que se presentan en este momento por (ser de fecha posterior a nuestro escrito de alegaciones, ser de fecha anterior a la demanda, aunque esta parte no ha podido presentarlo hasta este momento por)

3.ºQue se libre exhorto al Tribunal de n.º [Nº] a fin de que remita copia debidamente testimoniada de la sentencia n.º [Nº] de fecha [FECHA] dictada en los autos n.º [Nº DE PROCEDIMIENTO]

4.º Que se libre mandamiento a la Notaría de D./Dña. [NOMBRE Y APELLIDOS], en a fin de que remita copia autentificada del testamento abierto otorgado por D./Dña. [NOMBRE Y APELLIDOS] ante el citado Notario en fecha [FECHA], con n.º [Nº] de protocolo

5.º Que remita oficio al Servicio de traumatología del hospital del INSALUD de para que remita copia del historial médico de D./Dña. [NOMBRE Y APELLIDOS]

6.º Que se consulte por el Tribunal a través del sistema de comunicación informático con (entidad administrativa) a fin de que se incorpore a autos la información sobre

7.º Que se requiera al representante legal de la empresa para que presente ante el Tribunal sus libros de contabilidad relativos a las operaciones de venta efectuadas en el mes de del año

8.º Que se requiera a (el actor o el demandado) para que exhiba el original que obra en su poder de las cédulas hipotecarias suscritas por D, en [COMPLETAR], y cuya copia simple (se presentó con nuestro escrito de demanda o de contestación o se presenta en este momento), siendo ésta la única que obra en nuestro poder.

(En su caso, si nos encontramos ante una demanda en materia de propiedad industrial o derechos intelectuales: acompañamos como principio de prueba: —muestra de ejemplares, mercancías o productos—).

9.º Que se requiera a D./Dña. [NOMBRE Y APELLIDOS] (tercero en el proceso), con domicilio en para que aporte la copia del contrato privado de compraventa que obra en su poder suscrito entre él y el demandado en fecha relativo a la compraventa de la vivienda sobre la que se está ejercitando el derecho de retracto. La práctica de esta prueba resulta a nuestro entender esencial por (motivos) y si estuviera dispuesto a exhibirlo voluntariamente y así lo solicitara, el Letrado de la Administración de Justicia se constituirá en su domicilio para testimoniarlo.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
