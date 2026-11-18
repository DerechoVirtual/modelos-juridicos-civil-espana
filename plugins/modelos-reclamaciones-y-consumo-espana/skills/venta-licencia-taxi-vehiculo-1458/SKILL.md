---
name: venta-licencia-taxi-vehiculo-1458
description: "Redacta el escrito «Venta de licencia de taxi y vehículo» (formulario 1458 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Venta de licencia de taxi y vehículo

> Formulario 1458 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº DE RESOLUCIÓN (3 veces)
- [ ] LOCALIDAD (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] MARCA/MODELO (2 veces)
- [ ] FECHA
- [ ] IMPORTE
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecino de»; «…, mayor de edad, vecino de»; «…, en vigor y con fecha de salida de»; «…de»; «…de [COMPLETAR] de»; «…de»

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

### Formulario 1458 · Venta de licencia de taxi y vehículo

- Año del modelo: 2014
- Revisión 17-11-2026: 25 campos de relleno marcados en blanco; 11 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Reunidos
Exponendo
CLÁUSULAS
Conformidad

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS.-

DE UNA PARTE Y EN CALIDAD DE VENDEDOR, D. [NOMBRE Y APELLIDOS], mayor de edad, vecino de [COMPLETAR] con domicilio en la calle [CALLE], provisto del Documento Nacional de Identidad nº [NÚMERO], actuando en su propio nombre y derecho.

Y DE OTRA PARTE, Y EN CALIDAD DE COMPRADOR, D. [NOMBRE Y APELLIDOS], mayor de edad, vecino de [COMPLETAR] con domicilio en la calle [CALLE], provisto del Documento Nacional de Identidad nº [NÚMERO], actuando en su propio nombre y derecho.

Se reconocen ambas partes plena capacidad legal y legitimidad para otorgar el presente contrato, y en su virtud

EXPONEN.-

Que D. [NOMBRE Y APELLIDOS], es titular de una licencia municipal de auto-taxi nº [Nº DE RESOLUCIÓN] expedida por el Ayuntamiento de [LOCALIDAD]. Que dicha licencia se encuentra libre de cargas y gravámenes que puedan imposibilitar y dificultar su transferencia.

Que D. [NOMBRE Y APELLIDOS], ha obtenido la correspondiente autorización de transferencia de la licencia municipal de auto-taxi nº [Nº DE RESOLUCIÓN] por parte de la Subdirección de Circulación y Transportes del Ayuntamiento de [LOCALIDAD], en vigor y con fecha de salida de [COMPLETAR] de [COMPLETAR] de [COMPLETAR] en expediente nº [Nº DE PROCEDIMIENTO]

Que ambas partes han convenido la transmisión de cuantos derechos corresponden a D. [NOMBRE Y APELLIDOS], sobre la licencia reseñada a favor de D. [NOMBRE Y APELLIDOS], llevando a efecto lo convenido de acuerdo a las siguientes

CLÁUSULAS

Objeto

Que D. [NOMBRE Y APELLIDOS], transmite a D. [NOMBRE Y APELLIDOS], que acepta, la licencia de auto-taxi referida anteriormente con cuantos derechos son inherentes a la misma, libre de cargas, gravámenes, cesiones de uso, arrendamientos y al corriente en el pago de cánones y tributos de toda clase.

Que conjuntamente a la transmisión de la licencia se procede a la entrega de todos los elementos necesarios para la prestación del servicio de auto-taxi (emisora, módulo, taxímetro con impresora y terminal de gestión de flotas), todos ellos en perfecto estado de conservación y funcionamiento.

Que además de la licencia de taxi, D. [NOMBRE Y APELLIDOS], vende a D. [NOMBRE Y APELLIDOS], el vehículo de marca [MARCA/MODELO] modelo [MARCA/MODELO] con bastidor número [NÚMERO] y matrícula número [NÚMERO]

Información

Que la parte compradora manifiesta que ha sido informada del estado del referido vehículo, en su conjunto y de sus elementos mecánicos y componentes fundamentales, de su antigüedad y kilometraje. Asimismo se hace constar que el comprador ha examinado a través de un tercero el automóvil, y que el vehículo objeto de la presente compra-venta se encuentra revisado reglamentariamente por la ITV en fecha [FECHA] de [COMPLETAR] de

Reserva de derechos

Durante la gestión y obtención de la correspondiente autorización para el nuevo titular, de los derechos de explotación de la señalada licencia de auto-taxi, el vendedor D. se reserva el derecho a seguir explotando la actividad de dicha licencia.

Precio

Que ambas partes acuerdan un precio por la cesión de la licencia y la venta del vehículo antes señalado por un importe total de [IMPORTE] euros, cuya forma de pago se hará por cheque el mismo día de la renuncia definitiva de la licencia auto-taxi número [Nº DE RESOLUCIÓN] en el Ayuntamiento de [LOCALIDAD].

Resolución

El presente contrato quedará resuelto de pleno derecho si por cualquier circunstancia el Ayuntamiento de [LOCALIDAD] no autorizara la transferencia de la licencia o denegara el otorgamiento del carné municipal de taxi al comprador.

Sumisión a tribunales

Los contratantes, con renuncia expresa a su propio fuero, se someten expresamente a los Tribunales de [LOCALIDAD] para cuantas incidencias diera lugar la interpretación y cumplimiento de este contrato.

Y en prueba de conformidad con todo lo anteriormente expuesto, ambas partes manifiestan su conformidad con el presente contrato, que otorgan y firman en dos ejemplares igualmente originales, en el lugar y fecha arriba.

========================================================================
