---
name: rechazo-cargo-perito-designado-justa-causa-685
description: "Redacta el escrito «Rechazo del cargo por el perito designado con justa causa» (formulario 685 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Rechazo del cargo por el perito designado con justa causa

> Formulario 0685 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…. 138.3 LJV. En este sentido, el próximo»; «…tengo cita en el Hospital de»; «…, para someterme a una operación de»; «… recuperarme de la enfermedad crónica de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 138.3 de la Ley 15/2015
- art. 38 de la Ley 50/1980
- art. 138.3 LJV
- art. 138 LJV

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

### Formulario 0685 · Rechazo del cargo por el perito designado con justa causa

- Año del modelo: 2015
- Revisión 17-11-2026: 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del perito designado declinando su nombramiento por coincidir con la realización de pruebas médicas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio profesional en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y de conformidad con el art. 138.3 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), comparezco para alegar justa causa y no aceptar el nombramiento como perito. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) El pasado [FECHA] se me notificó decreto del Letrado de la Administración de Justicia del órgano al cual tengo el honor de dirigirme, en el que se comunicaba mi nombramiento como tercer perito conforme a lo dispuesto en el art. 38 de la Ley 50/1980, de 8 de octubre, de Contrato de Seguro (en lo sucesivo, LCS), en el marco del expediente de jurisdicción voluntaria tramitado con nº [NÚMERO] / [COMPLETAR].

2.ª) Que en la referida comunicación se me requería para que en el plazo legal de dos días previsto en el art. 342.1 de la Ley de Enjuiciamiento Civil, compareciera en el Tribunal, y manifestara si acepto el cargo.

3.ª) Que por medio del presente escrito, y dentro del plazo indicado, comparezco y manifiesto mi voluntad de no aceptar el cargo, alegando justa causa, tal y como dispone el art. 138.3 LJV. En este sentido, el próximo [COMPLETAR] tengo cita en el Hospital de [COMPLETAR], para someterme a una operación de [COMPLETAR], prescrita médicamente para recuperarme de la enfermedad crónica de [COMPLETAR] que padezco desde hace tres años. El cirujano que realizará la operación,
Dr. D. [NOMBRE Y APELLIDOS]
Dra. Dña.
[NOMBRE Y APELLIDOS], ha indicado un periodo mínimo de recuperación de cinco semanas, incompatible con el plazo de 30 días previsto en el apartado cuarto del citado precepto legal. Acompaño a este escrito certificado médico expedido por el mencionado facultativo, en el cual se recogen todos los extremos expuestos.

4.ª) En consecuencia, y en virtud de dicha justa causa, manifiesto mi voluntad de no aceptar el cargo, solicitando que, conforme al art. 342.2 de la Ley de Enjuiciamiento Civil, el Letrado de la Administración de Justicia considere aquella suficiente, sustituyéndome por el perito siguiente en la lista correspondiente.

Por todo lo expuesto, al amparo del art. 138 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito se me tenga por no aceptado en el nombramiento de tercer perito, y se considere suficiente la justa causa alegada para ello, sustituyéndome por el siguiente perito tasador de seguros de la lista correspondiente.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del perito

========================================================================
