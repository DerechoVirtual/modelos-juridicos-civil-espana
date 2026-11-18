---
name: fiducia-cum-amico-entre-particulares-contrato-191
description: "Redacta el escrito «Fiducia cum amico entre particulares: contrato» (formulario 191 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Fiducia cum amico entre particulares: contrato

> Formulario 0191 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] PROVINCIA (3 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] NÚMERO
- [ ] FECHA
- [ ] Nº
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la ciudad/localidad de»; «…, provincia de [PROVINCIA], a»; «…, a [COMPLETAR] de»; «…, a [COMPLETAR] de [COMPLETAR] del año»; «…, mayor de edad, vecino/a de»; «…, mayor de edad, vecino/a de»; «…es la siguiente: Tiene una superficie de»; «…Linda: al Norte»; «…Linda: al Norte [COMPLETAR], al Sur»; «…, al Sur [COMPLETAR], al Este»; «…, al Este [COMPLETAR], al Oeste»; «…scrita en el Registro de la Propiedad de»; …

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

### Formulario 0191 · Fiducia cum amico entre particulares: contrato

- Año del modelo: 2021
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad/localidad de [COMPLETAR], provincia de [PROVINCIA], a [COMPLETAR] de [COMPLETAR] del año [COMPLETAR]

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en [LOCALIDAD], provincia de [PROVINCIA], provisto/a del N.I.F. número

Y de otra parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR] con domicilio en [LOCALIDAD], provincia de [PROVINCIA] provisto/a del N.I.F.

MANIFIESTAN

Que intervienen en su propio nombre y se reconocen mutua y plena capacidad legal de obrar y de obligarse para este acto, otorgando de forma libre y espontánea y a su tenor el presente CONTRATO DE FIDUCIA, asumiendo la responsabilidad que corresponda en función de la veracidad de sus manifestaciones, y, de mutuo acuerdo,

EXPONEN

Que D/Dª [NOMBRE Y APELLIDOS], (en adelante, EL FIDUCIANTE) es propietario de la finca rústica sita en [LOCALIDAD] y cuya descripción es la siguiente:

Tiene una superficie de [COMPLETAR] Linda: al Norte [COMPLETAR], al Sur [COMPLETAR], al Este [COMPLETAR], al Oeste [COMPLETAR]

Se halla inscrita en el Registro de la Propiedad de [COMPLETAR], al Tomo [COMPLETAR] Libro [COMPLETAR], Folio [COMPLETAR], página [COMPLETAR], finca núm [NÚMERO]

Le pertenece a título de dominio en virtud de la compra que de la misma efectuó a D [COMPLETAR] en fecha [FECHA], según es de ver en la inscripción núm. [Nº] de la finca.

La finca se halla libre de arrendamientos y cargas. Al corriente del pago de impuestos, tasas y contribuciones de todo tipo.

Régimen Urbanístico [COMPLETAR]

Identificación catastral [COMPLETAR]

II.- Que en la referida finca existe un negocio ganadero con las instalaciones, bienes y cabezas de ganado que se recogen en el Inventario que se acompaña como Anexo I, el cual se incorpora como integrante del presente contrato.

III. Que es interés del FIDUCIANTE que se lleve a cabo la dirección, control, administración y explotación del citado negocio por el FIDUCIARIO durante los próximos años, hasta tanto el mismo FIDUCIANTE, o, en su caso, sus herederos, estén en disposición de explotar el negocio, lo cual interesa asimismo al FIDUCIARIO.

IV. Que estando ambas partes interesadas en que sea el FIDUCIARIO quien ostente durante todo este tiempo la titularidad de la explotación en fideicomiso frente a terceros a todos los efectos, convienen la celebración del presente contrato de fiducia para la transmisión del negocio, con sujeción a las siguientes

CLÁUSULAS

PRIMERA.- TRANSMISIÓN DEL NEGOCIO GANADERO

El FIDUCIANTE transmite en fideicomiso al FIDUCIARIO la finca y titularidad del negocio ganadero descrito en los expositivos I y II con sus instalaciones, bienes y cabezas recogidas en el Anexo I, obligándose a otorgar cuantos documentos públicos y administrativos sean necesarios para la transmisión de la titularidad negocio al FIDUCIARIO.

SEGUNDA.- EXPLOTACIÓN DEL NEGOCIO

El negocio ganadero arriba expresado se explotará bajo el nombre del FIDUCIARIO en fideicomiso para el FIDUCIANTE.

El FIDUCIARIO explotará personal y directamente el negocio, sin perjuicio de recurrir a la contratación de terceras personas cuando sea necesario.

El FIDUCIARIO consultará previamente al FIDUCIANTE las cuestiones derivadas de la explotación del negocio en el caso de que pretenda modificar las condiciones de la explotación o construir nuevas instalaciones.

TERCERA.- CONDICIONES ECONÓMICAS DE LA EXPLOTACIÓN

Todos los gastos, impuestos y demás obligaciones de la explotación serán pagados por el FIDUCIARIO.

El beneficio neto de la explotación después de impuestos será dividido en partes iguales, al 50% entre el FIDUCIANTE y el FIDUCIARIO.

La liquidación de los beneficios se realizará a la finalización de cada año natural.

CUARTA.- DURACIÓN MÍNIMA DE LA EXPLOTACIÓN

Ambas partes convienen un periodo de duración mínimo de la explotación por el FIDUCIARIO de diez años.

Una vez transcurrido el periodo mínimo de duración, el FIDUCIARIO estará obligado a reintegrar el negocio al FIDUCIANTE, en las condiciones que se recogen en la siguiente estipulación.

QUINTA.- OBLIGACIÓN DE REINTEGRO DEL NEGOCIO

El negocio será reintegrado al FIDUCIANTE, o en su caso, a sus herederos, una vez transcurrido el periodo mínimo de duración y a solicitud del FIDUCIANTE, quien deberá observar un plazo de preaviso mínimo de seis meses.

Transcurrido el plazo de preaviso, el FIDUCIARIO se obliga a otorgar los documentos públicos y administrativos necesarios para el reintegro inmediato de la propiedad de la finca, instalaciones, bienes y demás elementos que constituyen el negocio, y poner en posesión de los mismos al FIDUCIANTE o a sus herederos, sin reclamar ningún tipo de compensación o resarcimiento.

SEXTA.- OBLIGACIONES DE LAS PARTES

Las partes se obligan al cumplimiento del contrato conforme a sus cláusulas y a los fines pactados, y en especial:

-El FIDUCIARIO se obliga a conservar la finca, instalaciones y demás bienes transmitidos en fideicomiso en perfecto estado hasta tanto sean reintegrados al FIDUCIANTE o a sus herederos.

-El FIDUCIANTE se obliga a mantener en la posesión del negocio al FIDUCIARIO durante todo el periodo del fideicomiso, absteniéndose de realizar cualquier acto de perturbación en la explotación del negocio.

SÉPTIMA.- PROHIBICIÓN DE DISPONER

El FIDUCIARIO se compromete a no enajenar, gravar, arrendar o imponer cualquier otra carga a la finca, instalaciones y demás bienes transmitidos en fideicomiso.

OCTAVA.- .- RESOLUCIÓN DEL CONTRATO

El contrato se resolverá por las causas previstas legalmente, estipulándose expresamente, como causas de resolución a instancias del FIDUCIANTE, el impago por el FIDUCIARIO de las obligaciones económicas pactadas en el presente contrato, así como el incumplimiento por el FIDUCIARIO de los deberes de conservación y de la prohibición de disponer pactada en el presente contrato.

A instancias del FIDUCIARIO, el contrato se resolverá en el caso de que el FIDUCIANTE no transmita el negocio en el plazo de seis meses desde la firma de este contrato.

NOVENA.- GASTOS E IMPUESTOS DEL CONTRATO

Los gastos notariales, registrales, administrativos y de cualquier otro orden, así como los impuestos derivados de la transmisión en fideicomiso serán satisfechos por mitad por FIDUCIANTE y FIDUCIARIO.

Los gastos notariales, registrales, administrativos y de cualquier otro orden, así como los impuestos y tributos derivados del cumplimiento de la obligación de reintegro, serán de cargo del FIDUCIANTE.

DÉCIMA.- NOTIFICACIONES

Toda notificación que se efectúe entre las partes se hará por escrito y será entregada personalmente o de cualquier otra forma que certifique la recepción por la parte notificada en los respectivos domicilios indicados en el encabezamiento de este Contrato.

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

Y en prueba de conformidad de cuanto antecede, las partes firman y rubrican el presente contrato al que se incorpora el Anexo I expresado como parte integrante de su contenido, a un solo efecto y por duplicado ejemplar, en todas sus hojas, en el lugar y fecha del encabezamiento.

EL FIDUCIANTE EL FIDUCIARIO

Fdo.: Don/Doña [NOMBRE Y APELLIDOS] Fdo.: Don/Doña [NOMBRE Y APELLIDOS]
