---
name: impugnacion-oposicion-ejecucion-familia-motivos-fondo-158
description: "Redacta el escrito «Impugnación de la oposición a la ejecución en familia por motivos de fondo» (formulario 158 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de la oposición a la ejecución en familia por motivos de fondo

> Formulario 0158 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…la madre los impares. Siendo año par, en»; «…lección le correspondía, por tanto, a D.»; «…io, en el burofáx impuesto en Correos el»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] de [COMPLETAR] al»; «…de [COMPLETAR] al [COMPLETAR] de»; «…). Y siendo ello así, es claro que D.»; «…sión del derecho de visita a favor de D.»; «…n de la sentencia de divorcio. TERCERO.-»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 93 del Código Civil
- art. 560 LEC

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

### Formulario 0158 · Impugnación de la oposición a la ejecución en familia por motivos de fondo

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de parte de impugnación a la oposición a ejecución en materia de familia -derecho de visitas- formulada de contrario por motivos de fondo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], según tengo acreditado en los autos de ejecución registrados con el número [NÚMERO], siguiendo instrucciones de mi mandante y como mejor proceda en derecho DIGO:

Que por medio del presente escrito y dentro del plazo de cinco días concedido por/ la diligencia de ordenación/el auto de fecha [FECHA], IMPUGNO LA OPOSICIÓN a la ejecución despachada por auto de fecha [FECHA], formulada por el ejecutado D./Dña. [NOMBRE Y APELLIDOS], señalando los siguientes:

HECHOS

PRIMERO.- El relato fáctico contenido en el correlativo del escrito de oposición resulta desajustado a la realidad, por cuanto a continuación se expone.

La sentencia de divorcio, de fecha [FECHA], señaló en favor del cónyuge no custodio -D. [NOMBRE Y APELLIDOS] - un régimen de visitas en el que se le atribuía la mitad de los periodos vacacionales, con previsión de que la elección le correspondería a él los años pares y a la madre los impares.

Siendo año par, en [COMPLETAR] la elección le correspondía, por tanto, a D. [COMPLETAR], constando fehacientemente como articuló su opción, de conformidad con el título constituido por la sentencia de divorcio, en el burofáx impuesto en Correos el [COMPLETAR], con elección del 2º periodo de vacaciones -día [FECHA] de [COMPLETAR] de [COMPLETAR] al [COMPLETAR] de [COMPLETAR] de - (documento nº [Nº DE DOCUMENTO]).

Y siendo ello así, es claro que D. [COMPLETAR], ejerció correctamente su derecho de elección, razón por la que debe resolverse que la ejecución siga adelante.

SEGUNDO.- No se comparten las argumentaciones del ejecutado en el correlativo e insistimos en los supuestos de hecho y de derecho de nuestra demanda ejecutiva porque en este proceso de ejecución no procede entrar en la materia propia de la extinción/suspensión del derecho de visita a favor de D. [COMPLETAR], pues la concurrencia o no de los presupuestos del párrafo segundo del artículo 93 del Código Civil, ha de ser planteado en el pertinente proceso de modificación de medidas definitivas y no en el cauce de esta ejecución de la sentencia de divorcio.

TERCERO.- [COMPLETAR]

FUNDAMENTOS DE DERECHO

I.- Conformes a los correlativos sobre jurisdicción y competencia.

II.- Conforme con el correlativo sobre capacidad y legitimación, a los meros efectos formales.

III.- Conforme con el correlativo sobre representación y defensa, así como procedimiento.

Se formula este escrito de impugnación dentro del plazo legal de cinco días desde el traslado previsto en el art. 560 LEC.

IV.- Oponiéndonos a los fundamentos jurídico materiales alegados en relación al fondo del asunto por no ser de aplicación o ser de aplicación a sensu contrario

V.- Las costas de la tramitación de la oposición a la ejecución deberán ser impuestas al ejecutado, conforme a lo dispuesto en el art. 561.1 en relación con el 394 LEC.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL:

que tenga por presentado el presente escrito de impugnación a la oposición a la ejecución por motivos de fondo efectuada en nombre y representación de mi patrocinado, para que, conforme a los preceptos legales aplicables, se desestime totalmente la oposición formulada declarando procedente que la ejecución siga adelante, con imposición al ejecutado de las costas de la ejecución.

OTROSÍ DIGO: Que interesa al derecho de esta parte la celebración de vista, por lo que se solicita del Tribunal que se señale un día para su celebración dentro de los diez días siguientes a la conclusión del trámite de impugnación a la oposición.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
