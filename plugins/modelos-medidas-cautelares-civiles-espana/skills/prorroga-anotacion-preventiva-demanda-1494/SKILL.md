---
name: prorroga-anotacion-preventiva-demanda-1494
description: "Redacta el escrito «Prórroga de anotación preventiva de demanda» (formulario 1494 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Prórroga de anotación preventiva de demanda

> Formulario 1494 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] FECHA (5 veces)
- [ ] NÚMERO (4 veces)
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, según tengo acreditado en autos»; «…de»; «…de [COMPLETAR] al Tomo»; «…e [COMPLETAR] al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…ncuentra en el siguiente estado procesal»; «…UMENTOS: a) Con relación al primer hecho»; «…) En relación al segundo y tercer hechos»; «…de»; «…de [COMPLETAR] al Tomo»; «…e [COMPLETAR] al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»

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

### Formulario 1494 · Prórroga de anotación preventiva de demanda

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
ALEGACIONES
SUPLICO AL TRIBUNAL
Firmas

Escrito solicitando prórroga de anotación preventiva de demanda conforme al artículo 86 de la Ley Hipotecaria.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN] con domicilio en [LOCALIDAD], calle [CALLE], según tengo acreditado en autos [COMPLETAR], comparezco ante el Tribunal y como mejor proceda en Derecho DIGO:

Que por la presente, y siguiendo las expresas instrucciones de mi representado, formulo petición de prórroga de anotación preventiva de demanda acordada por resolución de fecha [FECHA] Y ello sobre la base de las siguientes:

ALEGACIONES

PRIMERO

Que en fecha [FECHA] se acordó por ese Tribunal la medida cautelar de anotación preventiva de demanda sobre la finca registral n.º [NÚMERO] inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], titulada a nombre de D./Dña. [NOMBRE Y APELLIDOS], la cual fue inscrita en dicho Registro en fecha [FECHA] según quedó acreditado en autos mediante el correspondiente duplicado debidamente cumplimentado.

SEGUNDO

Que el próximo día [FECHA] caducará dicha anotación preventiva al transcurrir el plazo legal indicado en el artículo 86 de la Ley Hipotecaria; no obstante lo cual, dispone el citado precepto que "a instancia de los interesados o por mandato de las autoridades que las decretaron, podrán prorrogarse por un plazo de cuatro años más, siempre que el mandamiento ordenando la prórroga sea presentado antes de que caduque el asiento".

TERCERO

Que el presente procedimiento se encuentra en el siguiente estado procesal [COMPLETAR], no habiendo decaído las razones que llevaron en su día a la adopción de la citada medida cautelar.

Como fundamento de las anteriores manifestaciones se adjuntan a la presente solicitud los siguientes DOCUMENTOS:

a) Con relación al primer hecho [COMPLETAR]
b) En relación al segundo y tercer hechos [COMPLETAR]

En virtud de lo expuesto:

SUPLICO AL TRIBUNAL

Que teniendo por presentada esta solicitud junto con sus documentos y copias de todo ello, se sirva admitirla y tener por formulada petición de prórroga de la medida cautelar de anotación preventiva de demanda sobre la finca registral n.º [NÚMERO] inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], propiedad del demandado D./Dña. [NOMBRE Y APELLIDOS], librándose los oportunos mandamientos por duplicado a dicho Registro.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
