---
name: contrato-aprovechamiento-turno-inmuebles-turisticos-1166
description: "Redacta el escrito «Contrato de aprovechamiento por turno de inmuebles turísticos» (formulario 1166 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato de aprovechamiento por turno de inmuebles turísticos

> Formulario 1166 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] ESTADO CIVIL (2 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO (6 veces)
- [ ] CALLE
- [ ] Nº (3 veces)
- [ ] IMPORTE
- [ ] Otros 22 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, provisto de N.I.F.»; «…, provisto de N.I.F.»; «…en nombre y representación de mercantil»; «…sejero Delegado; Sociedad constituida en»; «…, e inscrita en el Registro Mercantil de»; «…, al libro»; «…ante el Notario de»; «…ente contrato, MANIFIESTAN Primero.- Que»; «…, de la ciudad de»; «…de»; «…de [COMPLETAR] al»; «…nmueble descrito tiene una superficie de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 28 de la Ley 4/2012
- art. 30.4 de la Ley 4/2012
- Real Decreto 390/2021

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

### Formulario 1166 · Contrato de aprovechamiento por turno de inmuebles turísticos

- Año del modelo: 2015
- Revisión 17-11-2026: 52 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE,

Don/Doña [NOMBRE Y APELLIDOS], estado civil [ESTADO CIVIL], mayor de edad, con domicilio en [LOCALIDAD], provisto de N.I.F. [COMPLETAR].

Y DE OTRA,

Don/Doña [NOMBRE Y APELLIDOS], estado civil [ESTADO CIVIL], mayor de edad, con domicilio en. [NÚMERO], provisto de N.I.F. [COMPLETAR].

ACTÚAN:

D./Dña. [NOMBRE Y APELLIDOS] en nombre y representación de mercantil [COMPLETAR] S.A. en su calidad de Consejero Delegado; Sociedad constituida en [COMPLETAR] mediante escritura autorizada por el Notario D./Dña. [NOMBRE Y APELLIDOS] el día [FECHA], e inscrita en el Registro Mercantil de [COMPLETAR], al libro [COMPLETAR]; en uso de las facultades concedidas a su favor por escritura pública otorgada el día [FECHA] ante el Notario de [COMPLETAR] D./Dña. [NOMBRE Y APELLIDOS]; fue designado para el cargo por delegación expresa del Consejo de Administración.

D./Dña. [NOMBRE Y APELLIDOS] en nombre propio.

Reconociéndose mutuamente capacidad suficiente para acordar el presente contrato,

MANIFIESTAN

Primero.- Que [COMPLETAR] S.A., es propietaria de la siguiente finca:

Apartamento señalado con el número [NÚMERO] del edificio sito en la Calle [CALLE], donde le corresponde el nº [NÚMERO], de la ciudad de [COMPLETAR]. Se halla inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al [COMPLETAR].

Segundo.- Que el inmueble descrito tiene una superficie de [COMPLETAR] metros cuadrados y consta de salón, 1 dormitorio, cocina y cuarto de baño.

Está completamente equipado con mobiliario, electrodomésticos e instalaciones necesarias para su disfrute en el turno concertado. Se acompaña como anexo 1, suscrito por ambas partes, descripción detallada del mobiliario y ajuar existente en el apartamento.

Tercero.- Que sobre dicho inmueble existe constituido un régimen de aprovechamiento por turno por escritura otorgada por el Notario de esta ciudad D./Dña. [NOMBRE Y APELLIDOS] en fecha [FECHA], número de protocolo [COMPLETAR].

Régimen que se halla debidamente inscrito en el Registro de la propiedad de [COMPLETAR], [COMPLETAR].

Cuarto.- Que [COMPLETAR] S.A., ha obtenido de las autoridades competentes las licencias necesarias para ejercer la actividad turística, las de apertura, las necesarias para la primera ocupación de los alojamientos, zonas comunes y servicios accesorios que sean necesarias para el destino y la correspondiente cédula de habitabilidad. Documentación que se encuentra a disposición del adquirente.

Quinto.- Que interesando a D./Dña. [NOMBRE Y APELLIDOS] la adquisición de un derecho real limitado de aprovechamiento sobre el inmueble descrito han concertado el presente contrato de aprovechamiento por turno de bienes inmuebles que quieren se sujete al cumplimiento de las siguientes:

ESTIPULACIONES

Primera.- Objeto

D./Dña. [NOMBRE Y APELLIDOS] transmite a D./Dña. [NOMBRE Y APELLIDOS], que adquiere, un derecho real de aprovechamiento por turno del apartamento descrito en el antecedente I de este contrato y que para mejor identificación se acompaña de un croquis debidamente firmado por los contratantes.

Dicho derecho real de aprovechamiento viene referido al turno n.º [NÚMERO] que va desde las [Nº] horas del [COMPLETAR] a las [Nº] horas del [COMPLETAR].

En ningún caso se transmite derecho de propiedad sobre el inmueble ni sobre parte de él.

La facultad de aprovechamiento no comprende derecho alguno a alterar la configuración ni el mobiliario del inmueble.

Junto con el alojamiento se facilita el siguiente ajuar y valor atribuido al mismo:

El presente contrato consta de un anexo consistente en inventario de bienes muebles y ajuar del alojamiento cuyo derecho de aprovechamiento se transmite

Segunda.- Régimen jurídico

El presente contrato se regirá con carácter general por las disposiciones de la Ley 4/2012, de 6 de julio, de contratos de aprovechamiento por turno de bienes de uso turístico, de adquisición de productos vacacionales de larga duración, de reventa y de intercambio.

Tercera.- Plazo

El presente derecho de aprovechamiento por turno tiene una duración de [Nº] años extinguiéndose el [COMPLETAR].

Cuarta.- Precio

El precio de la transmisión queda fijado en la cantidad de [IMPORTE] euros, que se abonarán en la siguiente forma: [COMPLETAR].

Quinta.- Servicios e instalaciones

Junto con el aprovechamiento objeto del presente contrato se adquiere el derecho al uso de un conjunto de servicios e instalaciones comunes que se describen a continuación:

El régimen de su uso y disfrute es el siguiente [COMPLETAR]

Sexta.- Formalización del contrato

La adquisición y transmisión de derechos de aprovechamiento por turno podrá inscribirse en el Registro de la Propiedad, siempre que el contrato se haya celebrado o formalizado mediante escritura pública y el registrador abra folio al turno cuyo derecho de aprovechamiento sea objeto de transmisión, quedando siempre a salvo lo dispuesto en la Ley Hipotecaria.

Séptima.- Seguros

La propiedad pone en conocimiento del adquirente que, conforme a lo establecido en el art. 28 de la Ley 4/2012, de 6 de julio, tiene suscrita y en vigor una póliza de seguro con la compañía [COMPLETAR] con el número [NÚMERO],que cubre la responsabilidad civil en que puedan incurrir los ocupantes de los alojamientos derivada de la utilización de los mismos, así como de seguro de incendios y otros daños generales del edificio o del conjunto de sus instalaciones y equipos.

Octava.- Se entrega al adquirente copia de la certificación de eficiencia energética en cumplimiento del Real Decreto 390/2021 y art. 30.4 de la Ley 4/2012.

Conformes con cuanto antecede, firman el presente contrato en un solo ejemplar original, en el lugar y fecha mencionados.

Firma de EL/LA PROPIETARIO/A:

	Firma de EL/LA ADQUIRIENTE
D./Dña. [NOMBRE Y APELLIDOS] 	D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
