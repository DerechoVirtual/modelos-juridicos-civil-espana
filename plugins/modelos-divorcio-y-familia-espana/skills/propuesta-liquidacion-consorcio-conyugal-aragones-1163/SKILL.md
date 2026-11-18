---
name: propuesta-liquidacion-consorcio-conyugal-aragones-1163
description: "Redacta el escrito «Propuesta de liquidación del consorcio conyugal aragonés» (formulario 1163 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Propuesta de liquidación del consorcio conyugal aragonés

> Formulario 1163 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº
- [ ] IMPORTE (11 veces)
- [ ] NÚMERO (6 veces)
- [ ] FECHA
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en escritura otorgada en»; «… en escritura otorgada en [COMPLETAR] el»; «…parecientes. Registro de la Propiedad de»; «…,»; «…RÚSTICA. Campo de regadío, en término de»; «…, en escritura otorgada en»; «… en escritura otorgada en [COMPLETAR] el»; «…Registro de la Propiedad de»; «…Registro de la Propiedad de [COMPLETAR],»; «…- Cuenta de valores n.º [NÚMERO] con»; «…de la entidad»; «…de la entidad [COMPLETAR], sucursal»; …

## Párrafos opcionales (6)

Inclúyelos solo si encajan en los hechos:

- -…
- -…
- - Muebles y enseres del domicilio conyugal valorados en [IMPORTE] euros.…
- - Cuenta de valores n.º [NÚMERO] con [COMPLETAR] con acciones y fondos.…
- - Cuenta Corriente n.º [NÚMERO] de la entidad [COMPLETAR], sucursal [COMPLETAR], sita en la calle [CALLE] de […
- - Vehículo marca [MARCA/MODELO] modelo [MARCA/MODELO], matrícula [MATRÍCULA], valorado en [IMPORTE] euros.…

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

### Formulario 1163 · Propuesta de liquidación del consorcio conyugal aragonés

- Año del modelo: 2015
- Revisión 17-11-2026: 4 llamadas a nota sin texto retiradas; 6 párrafos opcionales señalados; 43 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

LIQUIDACIÓN DEL PATRIMONIO CONYUGAL

El matrimonio se encontraba sujeto al régimen consorcial aragonés habiéndose producido la disolución de la sociedad ganancial en virtud de la sentencia de separación si bien no se ha producido la liquidación y adjudicación de los bienes de la misma a los cónyuges, por lo que proceden a efectuar en este documento las operaciones de inventario, liquidación y adjudicación conforme a las siguientes reglas:

A) INVENTARIO

I.- ACTIVO de la sociedad consorcial.

[OPCIONAL — incluir si procede]

-
+
Añadir más párrafos iguales

URBANA. Vivienda sita en [LOCALIDAD], calle [CALLE] que se describe así:

Pertenece al matrimonio en pleno dominio por compra a D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], en escritura otorgada en [COMPLETAR] el [COMPLETAR], ante su Notario/a D./Dña. [NOMBRE Y APELLIDOS], Protocolo núm. [Nº]

Sin cargas en cuanto a la hipoteca a favor de la Entidad Bancaria que figura inscrita, que está totalmente pagada y pendiente de escritura de cancelación que los cónyuges se comprometen a otorgar.

Los gastos que ello conlleve serán sufragados por mitad e iguales partes por los comparecientes.

Registro de la Propiedad de [COMPLETAR], [COMPLETAR].

Referencia catastral:

Valor: [IMPORTE] euros.

[OPCIONAL — incluir si procede]

-
+
Añadir más párrafos iguales

RÚSTICA. Campo de regadío, en término de [COMPLETAR].

Pertenece al matrimonio en pleno dominio por compra a D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], en escritura otorgada en [COMPLETAR] el [COMPLETAR], ante su Notario/a D./Dña. [NOMBRE Y APELLIDOS]

Registro de la Propiedad de [COMPLETAR], [COMPLETAR].

Valor: [IMPORTE] euros.

[OPCIONAL — incluir si procede]

- Muebles y enseres del domicilio conyugal valorados en [IMPORTE] euros.

[OPCIONAL — incluir si procede]

- Cuenta de valores n.º [NÚMERO] con [COMPLETAR] con acciones y fondos.

Valor a fecha de [IMPORTE]: euros.

[OPCIONAL — incluir si procede]

- Cuenta Corriente n.º [NÚMERO] de la entidad [COMPLETAR], sucursal [COMPLETAR], sita en la calle [CALLE] de [COMPLETAR], cuyo importe a fecha [FECHA] es de [IMPORTE] euros.

[OPCIONAL — incluir si procede]

- Vehículo marca [MARCA/MODELO] modelo [MARCA/MODELO], matrícula [MATRÍCULA], valorado en [IMPORTE] euros.

II.- PASIVO de la sociedad consorcial.

Sin partidas que consignar.

VALOR DEL PATRIMONIO CONYUGAL: [IMPORTE] euros.

B) LIQUIDACIÓN

Corresponde a cada uno de los cónyuges por su participación en el haber conyugal la cantidad de [IMPORTE] euros.

C) ADJUDICACIONES

Don [COMPLETAR] se adjudica con carácter privativo los bienes siguientes:

La mitad indivisa de la vivienda descrita en el n.º [NÚMERO] de los bienes del activo así como la totalidad de los bienes relacionados con los números [COMPLETAR], y la mitad del fondo señalado con el n.º [NÚMERO].

El Sr. se adjudica las fincas rústicas del consorcio para evitar el desmerecimiento que la partición produciría en dichos bienes, debiendo compensar a la Sra. del exceso que se adjudica como más abajo se dirá.

TOTAL ADJUDICADO: [IMPORTE] euros.

Doña [COMPLETAR] se adjudica la mitad indivisa de la vivienda descrita en el n.º [NÚMERO] de los bienes del activo, la totalidad de los señalados con los números [COMPLETAR] y [COMPLETAR], el importe total de la cuenta corriente descrita en el n.º 8 del activo y la mitad del fondo señalado con el n.º [NÚMERO].

TOTAL ADJUDICADO: [IMPORTE] euros.

La Sra. deberá recibir del Sr. la cantidad de [IMPORTE] euros que le faltan por el valor de su 50% en los bienes del consorcio.

Los comparecientes renuncian mutua y recíprocamente a cualquier reclamación posterior sobre la liquidación practicada así como al derecho expectante de viudedad o a cualquier otro derecho que pudiera corresponderles por ministerio de la ley sobre los bienes del otro.

Cualquier otro bien o deuda no incluido en este documento pertenecerá o será a cargo de aquel de los comparecientes que figura como titular del mismo.

Firma

Firma

D. 	Dña. [NOMBRE Y APELLIDOS]

========================================================================
