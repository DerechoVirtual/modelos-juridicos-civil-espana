---
name: contrato-comunidad-instaladora-paneles-solares-gestion-56
description: "Redacta el escrito «Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención» (formulario 56 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención

> Formulario 0056 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] NIF (2 veces)
- [ ] FECHA
- [ ] IMPORTE (7 veces)
- [ ] Otros 32 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dente de la Comunidad de Propietarios de»; «…situada en»; «…trato, otorgada en Junta de Propietarios»; «…e como legal representante de la entidad»; «…., con sede social en»; «…. y NIF n.º [NIF], cuyo objeto social es»; «…a. .- Otras disposiciones de aplicación:»; «…or la citada instalación. Que la empresa»; «…l autoconsumo de energía eléctrica y por»; «…oras y convocatoria fueron publicadas en»; «… Cláusulas CLÁUSULAS Primera. La empresa»; «… cabo en la Comunidad de Propietarios de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 9 de la Ley 24/2013
- Real Decreto 337/2014
- Real Decreto 244/2019

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

### Formulario 0056 · Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención

- Año del modelo: 2023
- Revisión 17-11-2026: 47 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

COMPARECEN

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE], y

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE],

Exposición

EXPONEN

Que D./Dña. [NOMBRE Y APELLIDOS] comparece como Presidente de la Comunidad de Propietarios de [COMPLETAR] situada en [COMPLETAR]. con CIF n.º [NIF], según autorización para firmar el presente contrato, otorgada en Junta de Propietarios [COMPLETAR] de fecha [FECHA].

D./Dña. [NOMBRE Y APELLIDOS] actúa y contrata en nombre de esta Comunidad de Propietarios.

Que D./Dña. [NOMBRE Y APELLIDOS] comparece como legal representante de la entidad [COMPLETAR]., con sede social en [COMPLETAR]. y NIF n.º [NIF], cuyo objeto social es [COMPLETAR].

La entidad es empresa habilitada y cumple con los requisitos legalmente establecidos para instalar sistemas de autoconsumo de energía eléctrica en los términos legalmente establecidos (elegir y completar la normativa que proceda):

.- Real Decreto 337/2014, de 9 de mayo, por el que se aprueban el Reglamento sobre condiciones técnicas y garantías de seguridad en instalaciones eléctricas de alta tensión y sus Instrucciones Técnicas Complementarias ITCRAT 01 a 23.

.- ITC-RAT-21 del Reglamento de Instalaciones Eléctricas en Alta Tensión (RIAT).

.- RD 842/2002, de 2 de agosto, por el que se aprueba el Reglamento electrotécnico de baja tensión.

.- ITC-BT-03 del Reglamento de Instalaciones Eléctricas de Baja Tensión (RIBT)

- Ley 24/2013, de 26 de diciembre, del Sector Eléctrico.

.- RD 244/2019, de 5 de abril. Condiciones administrativas, técnicas y económicas del autoconsumo de energía eléctrica.

.- Otras disposiciones de aplicación: [COMPLETAR].

Que la Comunidad de Propietarios está interesada en la completa instalación de paneles solares y en solicitar y obtener las subvenciones que les pudieran corresponder por la citada instalación.

Que la empresa [COMPLETAR] está habilitada y cuenta tanto con los medios profesionales y técnicos para realizar la instalación como con las autorizaciones indicadas en el procedimiento administrativo establecido por Real Decreto 244/2019, por el que se regulan las condiciones administrativas, técnicas y económicas del autoconsumo de energía eléctrica y por [COMPLETAR].

Asimismo, la empresa cuenta con los medios y cumple los requisitos previstos para gestionar las subvenciones en materia de ahorro energético, eficiencia energética y energías renovables, cuyas bases reguladoras y convocatoria fueron publicadas en [COMPLETAR].

Que ambas partes se reconocen capacidad suficiente para suscribir el presente contrato para la instalación de sistemas de autoconsumo de energía eléctrica, en concreto, paneles solares, y la gestión y tramitación de las subvenciones aprobadas para el fomento de este tipo de instalaciones; contrato que se regirá por las siguientes

Cláusulas

CLÁUSULAS

Primera. La empresa [COMPLETAR] llevará a cabo en la Comunidad de Propietarios de [COMPLETAR] las siguientes actuaciones: [COMPLETAR], que afectarán del modo indicado a continuación a:

· Los elementos comunes siguientes: [COMPLETAR].

· Los elementos privativos siguientes: [COMPLETAR].

Segunda. En aplicación del Real Decreto 244/2019 por el que se regulan las condiciones administrativas, técnicas y económicas del autoconsumo de energía eléctrica, que regula las distintas modalidades previstas en el artículo 9 de la Ley 24/2013, de 26 de diciembre, del Sector Eléctrico, la instalación objeto de este contrato se ajustará a la modalidad de autoconsumo sin excedentes, [COMPLETAR].

Segunda. En aplicación del Real Decreto 244/2019 por el que se regulan las condiciones administrativas, técnicas y económicas del autoconsumo de energía eléctrica, que regula las distintas modalidades previstas en el artículo 9 de la Ley 24/2013, de 26 de diciembre, del Sector Eléctrico, la instalación objeto de este contrato se ajustará a la modalidad de autoconsumo sin excedentes, [COMPLETAR].

Segunda. En aplicación del Real Decreto 244/2019 por el que se regulan las condiciones administrativas, técnicas y económicas del autoconsumo de energía eléctrica, que regula las distintas modalidades previstas en el artículo 9 de la Ley 24/2013, de 26 de diciembre, del Sector Eléctrico, la instalación objeto de este contrato se ajustará a la modalidad de autoconsumo sin excedentes, [COMPLETAR].

Tercera El tiempo de la ejecución de la obra será de [COMPLETAR]. Por otro lado, [COMPLETAR].

Cuarta. El precio por la tramitación del procedimiento, la ejecución de la instalación de los paneles solares y su puesta en funcionamiento y la gestión de la subvención asociada a esa instalación se pacta en [IMPORTE] euros, que se desglosa de la siguiente manera:

· Tramitación administrativa: [IMPORTE] €. Dentro de la tramitacion se engloban las actuaciones siguientes: [COMPLETAR].

· Tramitación con la compañía distribuidora: [IMPORTE] €. La compañía es [COMPLETAR].

· Mano de obra: [IMPORTE] €.

· Material: [IMPORTE] €.

· Gestión y tramitacion de la subvención: [IMPORTE] €.

IVA: [IMPORTE] €.

El pago se realizará a favor de [COMPLETAR] de la siguiente manera: [COMPLETAR].

Quinta. Finalizadas las obras y realizadas las verificaciones e inspección inicial (si procede), la empresa instaladora deberá emitir:

· Certificado de Instalación, suscrito por un instalador en baja tensión que pertenezca a la empresa, según el procedimiento establecido por [COMPLETAR].

· Certificado final de obra. (En caso de que la instalación tenga una potencia superior a 10 kW y esté conectada en BT))..

Sexta. Para el caso de discrepancias en la interpretación de este contrato o conflictos en su ejecución las partes acuerdan someterse a [COMPLETAR].

Y para que conste y surta los efectos oportunos suscriben las partes el presente contrato en cada uno de los [COMPLETAR] folios de los que consta y en el lugar y fecha indicados a continuación.

En [COMPLETAR]., a [COMPLETAR] de [COMPLETAR].

Firmado: D./Dña. [NOMBRE Y APELLIDOS]

Por la Comunidad de Propietarios de [COMPLETAR]

Firmado: D./Dña. [NOMBRE Y APELLIDOS]

Por la empresa de [COMPLETAR]
