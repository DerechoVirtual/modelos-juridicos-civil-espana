---
name: resolucion-mutuo-acuerdo-contrato-prestacion-servicios-1161
description: "Redacta el escrito «Resolución por mutuo acuerdo del contrato de prestación de servicios» (formulario 1161 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución por mutuo acuerdo del contrato de prestación de servicios

> Formulario 1161 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR (2 veces)
- [ ] FECHA (3 veces)
- [ ] NOMBRE Y APELLIDOS (11 veces)
- [ ] NÚMERO (3 veces)
- [ ] LOCALIDAD
- [ ] NIF
- [ ] IMPORTE (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecino/a de»; «…, domiciliado/a en»; «…, mayor de edad, vecino/a de»; «…, domiciliado/a en»; «…epresentación de ESTUDIO DE ARQUITECTURA»; «…, Notario/a de»; «…, Notario/a de [COMPLETAR], el»; «…encargó a ESTUDIO DE ARQUITECTURA»; «…ropiedad sita en el término municipal de»; «…a el momento por ESTUDIO DE ARQUITECTURA»; «…más un»

## Elecciones que hay que hacer

- DNI / pasaporte

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

### Formulario 1161 · Resolución por mutuo acuerdo del contrato de prestación de servicios

- Año del modelo: 2015
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 2 desplegables convertidos en elección en blanco; 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

REUNIDOS

De una parte, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], domiciliado/a en [COMPLETAR] con [ELEGIR: DNI / pasaporte] n.º [NÚMERO]

De otra parte, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], domiciliado/a en [COMPLETAR] con [ELEGIR: DNI / pasaporte] n.º [NÚMERO]

INTERVIENEN

D./Dña. [NOMBRE Y APELLIDOS] en su propio nombre y derecho.

D./Dña. [NOMBRE Y APELLIDOS] en representación de ESTUDIO DE ARQUITECTURA [COMPLETAR], SOCIEDAD LIMITADA PROFESIONAL, con domicilio en [LOCALIDAD] y CIF n.º [NIF]; en uso del poder otorgado ante D./Dña. [NOMBRE Y APELLIDOS], Notario/a de [COMPLETAR], el [COMPLETAR], bajo el número [NÚMERO] de los de su protocolo.

Ambas partes, en las respectivas calidades con que actúan se reconocen mutua y recíprocamente plena capacidad legal para cuanto pasan a manifestar y convenir y de sus libres y espontáneas voluntades,

MANIFIESTAN

I.- Que mediante contrato de arrendamiento de servicios profesionales suscrito por las partes con fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] encargó a ESTUDIO DE ARQUITECTURA [COMPLETAR] determinados trabajos en relación a la construcción de una vivienda unifamiliar en una finca de su propiedad sita en el término municipal de [COMPLETAR] Se acompaña copia del citado contrato como anexo al presente documento.

II.- Que D./Dña. [NOMBRE Y APELLIDOS] no tiene, en el momento actual, la capacidad económica que tenía en el momento de la firma del contrato, y no puede, en los términos pactados, continuar con la ejecución de las obras de edificación de la citada vivienda, y al efecto

ACUERDAN

Dar por resuelto y extinguido el referido contrato de arrendamiento de servicios profesionales en los términos fijados en los siguientes,

PACTOS

PRIMERO.- Ambas partes, de común acuerdo, resuelven y dejan sin ningún valor ni efecto la relación de servicios que les vinculaba, entendiéndose totalmente liquidada la relación contractual habida entre las partes.

SEGUNDO.- D./Dña. [NOMBRE Y APELLIDOS] recibe en este acto de D./Dña. [NOMBRE Y APELLIDOS], la cantidad de [IMPORTE] euros, importe a que asciende el importe de los trabajos realizados hasta el momento por ESTUDIO DE ARQUITECTURA [COMPLETAR] más un [COMPLETAR] % de los honorarios que le quedaban por percibir por aquellas fases encargadas que ya no podrán llevar a cabo como consecuencia de la resolución, por importe de [IMPORTE] euros, en concepto de indemnización por daños y perjuicios voluntariamente convenida.

TERCERO.- Con la firma de este documento, y la entrega de las antedichas cantidades, las partes quedan totalmente desligados del contrato de arrendamiento de servicios que en este acuerdo se reseña, sin que tengan derecho a reclamarse cantidad alguna por ningún concepto, como consecuencia del contrato que se resuelve, renunciando mutua y expresamente al ejercicio de acciones legales que pudieran derivarse del contrato referido, haciéndose asimismo ambas partes recíproca devolución de toda la documentación obrante, sirviendo el presente, para ambos efectos, de suficiente recibo.

En [LUGAR], a [FECHA].

Firma de EL/LA ARRENDADOR/A:

	Firma de EL/LA ARRENDATARIO/A
D./D.ª [NOMBRE Y APELLIDOS]	D./D.ª [NOMBRE Y APELLIDOS]

========================================================================
