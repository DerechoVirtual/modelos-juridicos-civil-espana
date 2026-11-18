---
name: reconvencion-divorcio-separacion-contenciosa-835
description: "Redacta el escrito «Reconvención en el divorcio o la separación contenciosa» (formulario 835 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconvención en el divorcio o la separación contenciosa

> Formulario 0835 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] IMPORTE (7 veces)
- [ ] Nº (3 veces)
- [ ] FECHA (2 veces)
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…presentado que se tiene que declarar que»; «…arte en su negocio realizando labores de»; «…uge y por tanto los ingresos familiares;»; «… elimina el desequilibrio ocasionado por»; «… reconvención. En este caso al solicitar»; «…ración, art. 81 del CC. Por eso y porque»; «…que concurren en el presente caso porque»; «…celebrado en»; «…celebrado en»; «… elimina el desequilibrio ocasionado por»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 770.2 de la LEC
- art. 749.2 de la LEC
- art. 770 de la LEC
- arts. 85 y 86 del CC
- art. 81 del CC
- art. 91 del CC
- art. 97 del CC

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

### Formulario 0835 · Reconvención en el divorcio o la separación contenciosa

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

OTROSÍ DIGO: Que al amparo de lo establecido en el art. 770.2 de la LEC D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito debidamente en la contestación a la demanda, formulo DEMANDA RECONVENCIONAL frente a D./Dña. [NOMBRE Y APELLIDOS], cuyas circunstancias personales ya constan en autos con el fin de que:

(Opciones):

— se declare la disolución del matrimonio por divorcio, en vez de la separación conyugal que se propugna de contrario.

— se declare el derecho de mi representado a percibir una pensión compensatoria de [IMPORTE] euros mensuales.

Basamos esta pretensión en los siguientes:

HECHOS

Damos por reproducidos en este apartado todos los hechos narrados en la contestación de la demanda, en lo que se refieran a la pretensión que ahora desarrollamos, así como los documentos en que se basan las afirmaciones declaradas, interesando desde este momento que se consideren también prueba de esta reconvención.

(Opciones):

— Esta parte interesa que se declare la definitiva extinción del matrimonio por divorcio, el vez de la declaración de separación que se propugna de contrario porque consideramos más práctica esta medida.

— La parte actora no incluye entre las medidas que propone que regulen las relaciones entre los cónyuges en el futuro la relativa a la pensión compensatoria. Sin embargo entiende mi representado que se tiene que declarar que [COMPLETAR] (la separación o el divorcio) le produce un desequilibrio económico considerable porque D./Dña. [NOMBRE Y APELLIDOS] (carece de ingresos propios; se ha dedicado de forma preferente al cuidado de la familia desde hace [Nº] años, dejando de lado su promoción profesional; tiene unos ingresos notablemente inferiores a la otra parte; ayudaba a la otra parte en su negocio realizando labores de [COMPLETAR] por las que no percibía ingreso alguno, considerando que con su trabajo contribuía a disminuir los gastos del negocio del otro cónyuge y por tanto los ingresos familiares; [COMPLETAR])

Así las cosas entendemos que debe declararse el derecho de D./Dña. [NOMBRE Y APELLIDOS] a percibir: (Opciones):

1.º Una pensión compensatoria mensual de [IMPORTE] euros, que se ingresará por anticipado dentro de los primeros cinco días de cada mes en la cuenta que al efecto se designe y que se actualizará anualmente aplicando a la cantidad que en cada momento esté en vigor el IPC anual elaborado por el INE o índice que lo sustituya.

2.º Una pensión compensatoria mensual de [IMPORTE] euros por un tiempo no inferior a [Nº] años, que se ingresará por anticipado dentro de los primeros cinco días de cada mes en la cuenta que al efecto se designe y que se actualizará anualmente aplicando a la cantidad que en cada momento esté en vigor el IPC anual elaborado por el INE o índice que lo sustituya.

3.º Una prestación única por importe de [IMPORTE] euros que sustituirá la obligación de abonar una pensión periódica. Con esa cantidad entiende esta parte que se elimina el desequilibrio ocasionado por [COMPLETAR] (la separación o el divorcio).

 (explicar por qué se ha elegido la opción que se considere más apropiada a cada caso)

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 409, 769 y 770.2.ª de la LEC remiten al Tribunal que conozca de la pretensión principal para resolver también sobre las peticiones incluidas en la reconvención.

Tramitación

El art. 770.2.ª de la LEC dice que la reconvención se propone con la contestación a la demanda y de ella se dará traslado al actor para que conteste en diez días. El art. 409 del mismo texto legal afirma que las pretensiones que se deduzcan en la reconvención se sustanciarán y resolverán al propio tiempo y en la misma forma que las que sean objeto de demanda principal.

Legitimación

Esta legitimado para formular la reconvención contra el demandante el demandado, y en aplicación del art. 749.2 de la LEC deberá intervenir el Ministerio Fiscal cuando estén afectados por este pleito menores o personas con discapacidad. [NOTA DE REVISIÓN: El art. 749.2 LEC ya no habla de «incapacitados». Fuente: LEC 1/2000 (BOE-A-2000-323) art. 749.2, redacción Ley 8/2021 (BOE-A-2021-9233): «sea menor, persona con discapacidad o esté en situación de ausencia legal».]

Postulación

En atención a lo establecido en el art. 770 de la LEC en relación con el art. 750 del mismo texto legal, las partes deberán comparecer representadas por procurador y asistidas de letrado.

Fondo del asunto

PRIMERO.— El art. 770.2ª de la LEC limita los supuestos en los que cabe formular reconvención. En este caso al solicitar [COMPLETAR] (que se declare el divorcio en vez de la separación o que se adopte una medida definitiva no interesada por la actora y sobre la que el juez no deba pronunciarse de oficio), el demandado está facultado para interesarla.

SEGUNDO.— (Opciones):

1.º Los arts. 85 y 86 del CC regulan la disolución del matrimonio por divorcio. Para acordar esta medida se exigen los mismos requisitos que para la separación, art. 81 del CC. Por eso y porque [COMPLETAR] interesamos que se acuerde no la separación pretendida por la parte demandante sino directamente el divorcio.

2.º El art. 91 del CC dice que el Juez, a falta de acuerdo entre las partes, deberá acordar en las sentencias de nulidad, separación o divorcio, las medidas que regularán las relaciones de las partes.

El art. 97 del CC recoge los requisitos que deben darse para reclamar este derecho. Entendemos que concurren en el presente caso porque [COMPLETAR]

Las costas de la reconvención deberán imponerse a la otra parte en el caso de oponerse temerariamente a esta pretensión.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por formulada en tiempo y forma reconvención, la admita a trámite y acuerden su día, previos los trámites legales oportunos, declarar:

(Opciones):

— La disolución del matrimonio por divorcio de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] celebrado en [COMPLETAR] el día [FECHA], acordando como medidas que regirán sus relaciones en el futuro las que esta parte interesa en el suplico de la contestación a la demanda.

— (la separación o el divorcio) del matrimonio de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] celebrado en [COMPLETAR] el día [FECHA], acordando como medidas que regirán sus relaciones en el futuro las que esta parte interesa en el suplico de la contestación a la demanda, así como que se reconozca el derecho de D./Dña. [NOMBRE Y APELLIDOS] a percibir:

(Opciones):

1.º Una pensión compensatoria mensual de [IMPORTE] euros, que se ingresará por anticipado dentro de los primeros cinco días de cada mes en la cuenta que al efecto se designe y que se actualizará anualmente aplicando a la cantidad que en cada momento esté en vigor el IPC anual elaborado por el INE o índice que lo sustituya.

2.º Una pensión compensatoria mensual de [IMPORTE] euros por un tiempo no inferior a [Nº] años, que se ingresará por anticipado dentro de los primeros cinco días de cada mes en la cuenta que al efecto se designe y que se actualizará anualmente aplicando a la cantidad que en cada momento esté en vigor el IPC anual elaborado por el INE o índice que lo sustituya.

3.º Una prestación única por importe de [IMPORTE] euros que sustituirá la obligación de abonar una pensión periódica. Con esa cantidad entiende esta parte que se elimina el desequilibrio ocasionado por [COMPLETAR] (la separación o el divorcio).

Todo ello con expresa imposición de las costas de esta reconvención a la otra parte si se opusiera de forma temeraria a esta pretensión.

Es justicia que pido en mismo lugar y fecha.

========================================================================
