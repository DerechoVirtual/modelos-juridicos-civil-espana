---
name: pago-aseguradora-perjudicado-danos-causados-tercero-235
description: "Redacta el escrito «Pago de la aseguradora del perjudicado por daños causados por un tercero» (formulario 235 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pago de la aseguradora del perjudicado por daños causados por un tercero

> Formulario 0235 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NIF
- [ ] DNI/NIE
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA (2 veces)
- [ ] FECHA
- [ ] Nº (2 veces)
- [ ] IMPORTE
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…representación de la Compañía de Seguros»; «…. 2º.-Que el día [FECHA] de»; «…2º.-Que el día [FECHA] de [COMPLETAR] de»; «…de [COMPLETAR] a las [Nº] horas en»; «…, asegurado en la Compañía de Seguros»; «…con nº [Nº] de póliza»; «…ulos a motor, han suscrito los Convenios»; «…culo asegurado en la Compañía de Seguros»; «… reparación se hace cargo la Aseguradora»; «…y a la Compañía de Seguros»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 8 del Real Decreto Legislativo 8/2004

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

### Formulario 0235 · Pago de la aseguradora del perjudicado por daños causados por un tercero

- Año del modelo: 2020
- Revisión 17-11-2026: 31 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Reunidos

De una parte: D./Dña. [NOMBRE Y APELLIDOS], que actúa en nombre y representación de la Compañía de Seguros [COMPLETAR], con domicilio social en [LOCALIDAD] y CIF nº [NIF].

De otra parte: D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI nº [DNI/NIE], que actúa en su propio nombre.

EXPONEN

1º.- Que D./Dña. [NOMBRE Y APELLIDOS] tiene suscrita póliza de seguro obligatorio del automóvil con esta Compañía de seguros para cubrir los riesgos del vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA].

2º.-Que el día [FECHA] de [COMPLETAR] de [COMPLETAR] a las [Nº] horas en [COMPLETAR], y cuando conducía el vehículo descrito en el apartado anterior, sufrió un accidente de circulación causado por el conductor D./Dña [NOMBRE Y APELLIDOS] que conducía el vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA], asegurado en la Compañía de Seguros [COMPLETAR] con nº [Nº] de póliza [COMPLETAR].

3º.- Que ambas Compañías de Seguros, en aplicación del artículo 8 del Real Decreto Legislativo 8/2004, de 29 de octubre, por el que se aprueba el texto refundido de la Ley sobre responsabilidad civil y seguro en la circulación de vehículos a motor, han suscrito los Convenios [COMPLETAR], en virtud de los cuales la Compañía que suscribe está facultada para satisfacer los daños causados por el vehículo asegurado en la Compañía de Seguros [COMPLETAR].

4º.- Que los comparecientes se reconocen capacidad suficiente para suscribir el presente documento de indemnización de daños materiales de acuerdo al siguiente contenido:

Cláusulas

Primera.- Esta Compañía de seguros va a abonar a la perjudicada la cantidad de [IMPORTE] euros por el mencionado siniestro.

Segunda.- Del presente pago o reparación se hace cargo la Aseguradora [COMPLETAR] en nombre y por cuenta de la Aseguradora del responsable del siniestro, subrogándose a todos los efectos en la posición de ésta en cuantos derechos y obligaciones le puedan corresponder.

Tercera.- Se hace constar expresamente que la aceptación y efectivo pago de la cantidad antedicha supone la renuncia de D./Dña. [NOMBRE Y APELLIDOS] a todas las acciones que respecto a D./Dña. [NOMBRE Y APELLIDOS] y a la Compañía de Seguros [COMPLETAR] pudieran corresponderle por el siniestro de referencia, salvo que se acreditara que la indemnización sea inferior a la que en derecho pueda corresponderle. En este sentido, se hace constar que el pago del importe que se ofrece no se condiciona a la renuncia por el perjudicado del ejercicio de futuras acciones en el caso de que la indemnización percibida fuera inferior a la que en derecho pueda corresponderle.

Y para que conste y surta los efectos oportunos suscriben el presente documento en el lugar y fecha arriba indicado.

Haga clic o pulse aquí para escribir texto.D./Dña. [NOMBRE Y APELLIDOS]

D./Dña. [NOMBRE Y APELLIDOS]
