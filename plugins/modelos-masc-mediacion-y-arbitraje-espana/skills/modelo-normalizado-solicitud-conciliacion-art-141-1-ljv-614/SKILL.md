---
name: modelo-normalizado-solicitud-conciliacion-art-141-1-ljv-614
description: "Redacta el escrito «Modelo normalizado de solicitud de conciliación (art. 141.1 LJV)» (formulario 614 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Modelo normalizado de solicitud de conciliación (art. 141.1 LJV)

> Formulario 0614 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NIF (2 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] TELÉFONO (3 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…con número de teléfono [TELÉFONO], fax»; «…ICITUD DE CONCILIACIÓN en reclamación de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, con número de teléfono [TELÉFONO], fax»; «…,»; «…Por: Con la presente solicitud»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- Por:…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 141.1 de la Ley 15/2015

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

### Formulario 0614 · Modelo normalizado de solicitud de conciliación (art. 141.1 LJV)

- Año del modelo: —
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (2); 2 bloques de alternativas señalados; 1 párrafos opcionales señalados; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de conciliación

Formulario normalizado para solicitud de conciliación previsto en el art. 141.1 de la Ley 15/2015, de 2 de julio, de Jurisdicción Voluntaria. Acuerdo del CGPJ publicado en BOE 28-1-2016.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS] con DNI y NIF/CIF número [NIF], domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO] y domicilio laboral en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR] con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO] (1).

FORMULO SOLICITUD DE CONCILIACIÓN en reclamación de [COMPLETAR] frente a [ACTO O RESOLUCIÓN]

-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS] con DNI y NIF/CIF [NIF], domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO], [COMPLETAR].

[OPCIONAL — incluir si procede]

Por:

Con la presente solicitud [COMPLETAR]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Aporto los documentos y/o dictámenes que se enumeran al final de este escrito. (2)

No aporto documentos y/o dictámenes

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Propongo la práctica de los siguientes medios de prueba:

1.
2.
3.
4.

(...)

No propongo prueba

En atención a lo expuesto,

PIDO AL TRIBUNAL:

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma

NOTAS DEL FORMULARIO

(1) Modelo aprobado por Acuerdo de 22 de diciembre de 2015, de la Comisión Permanente del Consejo General del Poder Judicial (BOE 28-1-2016).

El artículo 141.1 párrafo 2.º de la Ley 15/2015, de 2 de julio, de la jurisdicción voluntaria, dispone que el solicitante pueda formular su solicitud de conciliación cumplimentando unos impresos normalizados que, a tal efecto, se hallarán a su disposición en el órgano correspondiente.

(2) Documentación que se adjunta (en su caso):…

========================================================================
