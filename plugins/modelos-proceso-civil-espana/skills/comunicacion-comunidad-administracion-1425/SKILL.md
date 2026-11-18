---
name: comunicacion-comunidad-administracion-1425
description: "Redacta el escrito «Comunicación de la comunidad a la Administración» (formulario 1425 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Comunicación de la comunidad a la Administración

> Formulario 1425 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 53 y 64 de la Ley 39/2015

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

### Formulario 1425 · Comunicación de la comunidad a la Administración

- Año del modelo: 2013
- Revisión 17-11-2026: 9 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente n.º [Nº DE PROCEDIMIENTO]

A

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI n.º [Nº], en su calidad de Presidente de la Comunidad de Propietarios de con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], comparece en el expediente sancionador reseñado y EXPONE:

Que mediante el presente escrito, según permite el artículo 53 y 64 de la Ley 39/2015, de Procedimiento Administrativo Común,y dentro del plazo legalmente conferido al efecto, formulo las siguientes

ALEGACIONES

Con fecha se ha dado traslado a esta Comunidad de la resolución por la que se acuerda iniciar expediente sancionador contra esta Comunidad por incumplimiento de la legalidad urbanística y en concreto por.

Igualmente se nos requiere para que en el plazo de meses procedamos a restaurar.

La responsabilidad por los presuntos desperfectos que se describen en la resolución de fecha es sólo achacable a D./Dña. [NOMBRE Y APELLIDOS], propietario de la finca de este inmueble, como así se acredita con los documentos que acompañamos con los n.os y que consisten en:

1.º Nota simple del Registro de la Propiedad donde consta esa titularidad.

2.º Certificación expedida por el Secretario de la Comunidad del acta de la Junta de Propietarios celebrada el día de en cuyo punto se acuerda llevar a cabo las obras de conservación del inmueble consistentes en.

3.º Certificación expedida por el Secretario de la Comunidad del acta de la Junta de Propietarios celebrada el día de en cuyo punto se acuerda requerir a D./Dña. [NOMBRE Y APELLIDOS] para que proceda a facilitar mediante el acceso a su propiedad la ejecución de la obra de conservación de la parte exterior de los miradores que se considera elemento común y que debía realizarse desde el interior.

4.º Copia del requerimiento que se envió a D./Dña. [NOMBRE Y APELLIDOS] con esta finalidad.

5.º Contrato con la empresa para que realice las obras acordadas en Junta de Propietarios y presupuesto de ejecución.

Es evidente que por esta Comunidad se han adoptado las decisiones y los medios necesarios para realizar las obras de conservación del inmueble y que sólo la actitud obstrucionista del propietario de n.º ha impedido que se llevaran a cabo. Así las cosas y en aplicación del artículo 10.2 de la Ley de Propiedad Horizontal que dice que «Los propietarios que se opongan o demoren injustificadamente la ejecución de las órdenes dictadas por la autoridad competente responderán individualmente de las sanciones que puedan imponerse en vía administrativa», interesamos que el presente expediente se dirija contra esta persona, acordando liberar de toda responsabilidad a la Comunidad de Propietarios que represento.

Por lo expuesto,

SOLICITO A: Que tenga por presentado este escrito con los documentos que acompaño y, en virtud de lo expuesto, se acuerde seguir el presente expediente sancionador y de restauración de la legalidad frente a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], procediéndose a su archivo respecto a esta Comunidad de Propietarios.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
