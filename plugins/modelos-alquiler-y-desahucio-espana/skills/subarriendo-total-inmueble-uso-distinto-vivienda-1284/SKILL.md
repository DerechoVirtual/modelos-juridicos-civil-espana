---
name: subarriendo-total-inmueble-uso-distinto-vivienda-1284
description: "Redacta el escrito «Subarriendo total de inmueble (uso distinto de vivienda)» (formulario 1284 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Subarriendo total de inmueble (uso distinto de vivienda)

> Formulario 1284 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA
- [ ] IMPORTE
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, n.º [NÚMERO], de»; «…, según contrato otorgado en»; «…rito en el Registro de la Propiedad como»; «…El presente contrato será efectivo desde»; «…, y tendrá una duración de»; «…euros en concepto de renta, IVA»; «…o de los cinco primeros días de cada mes»; «… electricidad, gas, recibos de comunidad»; «… del local y dedicarlo a la actividad de»; «…eterse expresamente a la Jurisdicción de»; «…tario el presente contrato que consta de»

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

### Formulario 1284 · Subarriendo total de inmueble (uso distinto de vivienda)

- Año del modelo: 2013
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

MANIFIESTAN

Que D./Dña. [NOMBRE Y APELLIDOS] es arrendatario del local sito en la C/ [CALLE], n.º [NÚMERO], de [COMPLETAR], según contrato otorgado en [COMPLETAR], en fecha [FECHA], actualmente en vigor.

Que el propietario y arrendador del inmueble es D./Dña. [NOMBRE Y APELLIDOS], y el local consta descrito en el Registro de la Propiedad como [COMPLETAR]

Que es deseo de D./Dña. [NOMBRE Y APELLIDOS] subarrendar de forma total dicho local, motivo por el cual se otorga este contrato de subarriendo.

Que ambas partes se reconocen mutuamente la capacidad necesaria para otorgar el presente contrato de subarriendo que pactan libremente con arreglo a las siguientes

CLÁUSULAS

D./Dña. [NOMBRE Y APELLIDOS] ocupará en virtud de este contrato la totalidad de la superficie del local.

El presente contrato será efectivo desde [COMPLETAR], y tendrá una duración de [COMPLETAR].

Vencida la duración pactada, el subarriendo se prorrogará por un año si ninguna de las dos partes anunciara a la otra con 30 días de antelación la intención de dejar sin efecto la relación. Esta prórroga estará subordinada y determinada por la relación de arrendamiento principal.

D./Dña. [NOMBRE Y APELLIDOS] abonará mensualmente a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] euros en concepto de renta, IVA [COMPLETAR]. Esta cantidad se hará efectiva por anticipado y dentro de los cinco primeros días de cada mes [COMPLETAR].

La renta se actualizará anualmente aplicándole el IPC elaborado por el INE o índice que lo sustituya.

Respecto a los gastos por servicios comunes tales como agua, electricidad, gas, recibos de comunidad [COMPLETAR].

El subarrendatario se compromete a no cambiar el destino del local y dedicarlo a la actividad de [COMPLETAR]. Cualquier modificación dará lugar a la resolución de este contrato.

Igualmente se obliga a no realizar obra alguna sin consentimiento del propietario y del inquilino.

El subarrendador se compromete al pago de la renta al arrendador y a no realizar actividades que puedan perturbar la actividad del subarrendatario en el local.

El subarrendatario declara desde este momento conocer y aceptar las cláusulas del contrato principal de arrendamiento. Se une copia simple de ese contrato como anexo número 1.

También declara conocer y aceptar el estado general del inmueble.

El subarrendador se obliga a poner en conocimiento del arrendador este negocio antes de que transcurra un mes desde la firma de este convenio, mediante notificación fehaciente del contrato, uniéndose en ese momento este documento como anexo número 2 a este contrato, junto con el justificante de la entrega o notificación al arrendador.

Para todos los conflictos que puedan surgir en la interpretación, aplicación, efectos e incumplimiento de este contrato por las partes, acuerdan los contratantes someterse expresamente a la Jurisdicción de [COMPLETAR] con renuncia a cualquier otro fuero que pudiera corresponderles.

Y para que conste y surta los efectos oportunos firman subarrendador y subarrendatario el presente contrato que consta de [COMPLETAR] folios, y que se suscribe en cada hoja de los tres ejemplares idénticos que se otorgan mutuamente entre ellos y para el arrendador, en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
