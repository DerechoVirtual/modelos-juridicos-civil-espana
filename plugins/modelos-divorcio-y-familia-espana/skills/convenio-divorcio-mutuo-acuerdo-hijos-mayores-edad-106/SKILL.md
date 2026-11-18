---
name: convenio-divorcio-mutuo-acuerdo-hijos-mayores-edad-106
description: "Redacta el escrito «Convenio de divorcio de mutuo acuerdo con hijos mayores de edad» (formulario 106 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio de divorcio de mutuo acuerdo con hijos mayores de edad

> Formulario 0106 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] PROFESIÓN (2 veces)
- [ ] CALLE (7 veces)
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] IMPORTE (11 veces)
- [ ] NÚMERO
- [ ] Nº (3 veces)
- [ ] PROVINCIA
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] Otros 34 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la ciudad de»; «…a»; «…. Reunidos De una parte, Doña»; «…, vecino de la localidad de»; «…. Y de otra parte, Don»; «…, vecino de la localidad de»; «…dos en virtud de matrimonio celebrado en»; «…en forma»; «…, tomo»; «…, tomo [COMPLETAR], folio»; «…ven dos hijos/as, ambos mayores de edad:»; «…, nacido/a el día [FECHA]; y»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 81, 82, 83, 86 y 90 del Código Civil
- art. 1392 del CC

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

### Formulario 0106 · Convenio de divorcio de mutuo acuerdo con hijos mayores de edad

- Año del modelo: 2022
- Revisión 17-11-2026: 67 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (DNI/NIE, IMPORTE, Nº)
- Avisos de la revisión: Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad de [COMPLETAR] a [COMPLETAR].

Reunidos

De una parte,

Doña [COMPLETAR], mayor de edad, casada, de profesión [PROFESIÓN], vecino de la localidad de [COMPLETAR], con domicilio en calle [CALLE], provista de DNI núm. [DNI/NIE].

Y de otra parte,

Don [COMPLETAR], mayor de edad, casada, de profesión [PROFESIÓN], vecino de la localidad de [COMPLETAR], con domicilio en calle [CALLE], provista de DNI núm. [DNI/NIE]

Actúan ambos en nombre e interés propio, y se reconocen mutua y recíprocamente capacidad legal bastante para otorgar el presente convenio regulador, a cuyo efecto libre y espontáneamente,

Manifiestan

I.– Que están casados en virtud de matrimonio celebrado en [COMPLETAR] en forma [COMPLETAR] el día [FECHA], que se encuentra inscrito en el Registro civil de [LOCALIDAD], tomo [COMPLETAR], folio [COMPLETAR].

II.– Que de este matrimonio han nacido y viven dos hijos/as, ambos mayores de edad: [COMPLETAR], nacido/a el día [FECHA]; y [COMPLETAR], nacida/o el día [FECHA].

III.– Que ambos cónyuges son de vecindad civil común y el régimen económico del matrimonio es el de gananciales.

IV.– El domicilio familiar está sito en la localidad de [COMPLETAR], calle [CALLE].

V.– Siendo voluntad de ambas partes proceder al divorcio de mutuo acuerdo, suscriben el presente convenio, de conformidad a lo dispuesto en el artículo 81, 82, 83, 86 y 90 del Código Civil, a fin de que sea aprobado judicialmente (o notarialmente). Y a tal efecto, convienen los siguientes

Pactos

Primero.– De la disolución por divorcio.

Ambos cónyuges, acuerdan con carácter definitivo la disolución por divorcio de su matrimonio, y declaran que nada tienen que decirse ni reclamarse por razón del propio divorcio y de sus causas, salvo lo que en el presente documento se determina.

Segundo.– Medidas respecto de los hijos mayores de edad

Los hijos comunes del matrimonio D/Dª [NOMBRE Y APELLIDOS] y D/Dª [NOMBRE Y APELLIDOS], son mayores de edad, por lo que tienen capacidad para gobernarse por sí mismos en los aspectos personales, si bien es necesario pactar lo procedente respecto de sus alimentos, educación y manutención al estar en la actualidad cursando estudios de grado universitario y carecer de ingresos propios, dependiendo económicamente de sus progenitores.

Ambos progenitores pactan las siguientes medidas en relación a sus alimentos, manutención, convivencia y educación de sus hijos comunes:

1) Los hijos comunes seguirán conviviendo en el domicilio familiar con el/la padre/madre hasta que finalicen sus estudios universitarios y se independicen económicamente. El periodo de uso y disfrute del domicilio familiar en estas condiciones finalizará cuando hagan vida independiente los dos hijos, con un límite temporal máximo de diez años a contar desde la fecha de este convenio.
2) El padre/madre contribuirá a los gastos de alimentación, cuidado y educación de sus hijos/as mediante el pago de una pensión alimenticia que se fija en la cantidad de [IMPORTE] EUROS MENSUALES (- €/mes). Dicha pensión se abonará, dentro de los cinco primeros días de cada mes, en la cuenta bancaria núm [NÚMERO]., que el/la padre/madre tiene abierta conjuntamente con sus hijos/as en la entidad financiera [COMPLETAR], oficina núm. [Nº].

Dicha pensión se actualizará automáticamente cada doce meses, incrementándose o disminuyéndose según el IPC que publique el Instituto Nacional de Estadística u otro organismo oficial que pudiera sustituirle.

3) Los gastos extraordinarios que se puedan originar mientras subsista la contribución de alimentos para los hijos deben ser sufragados por mitad entre ambos progenitores. Se entenderán como gastos extraordinarios aquellos que derivados del estado de salud de los hijos no sean cubiertos por la Seguridad Social, también aquellos derivados de los estudios que en un futuro lleven a término los hijos/as comunes como matrículas para cursar masters u otras actividades formativas complementarias a los estudios universitarios que actualmente están cursando.

Estas medidas han sido aceptadas expresamente por los hijos, quienes autorizarán con su firma este pacto, manifestando su voluntad de comparecer ante el letrado de la Administración de Justicia (o notario) a prestar su consentimiento.

Tercero.– Atribución de la vivienda y ajuar familiar

El uso y disfrute temporal de la vivienda familiar sito en la localidad de [COMPLETAR], provincia de [PROVINCIA], calle [CALLE] con su ajuar, queda atribuido al padre/ madre, que residirá en el mismo junto con los/as hijos/as comunes del matrimonio, en los términos pactados en la cláusula segunda de este convenio.

El otro cónyuge fija su domicilio en la ciudad de [COMPLETAR], calle [CALLE], donde piensa trasladarse a residir, habiendo retirado ya de la vivienda familiar sus enseres y objetos personales.

La atribución del uso y disfrute de la vivienda familiar finalizará cuando ambos hijos comunes hagan vida independiente, con el límite máximo de diez años desde la firma de este convenio.

Una vez finalice el periodo de atribución pactado se procederá a la división del inmueble, de acuerdo a las condiciones que se recogen en el pacto QUINTO sobre la liquidación del régimen económico-matrimonial (o, en su caso, sobre la división de los bienes comunes).

Cuarto.– Pensión compensatoria.

Se establece como pensión compensatoria en favor del/la esposo/a la cantidad de [IMPORTE] EUROS MENSUALES (- euros/mes), con una duración temporal de cinco años.

La pensión se fija para resarcir el desequilibrio económico que produce la disolución del matrimonio en el cónyuge favorecido, pactando ambas partes que quedará extinguida en todo caso cuando el cónyuge contraiga matrimonio, o conviva en relación análoga de afectividad con otra persona, o se desempeñe actividad retribuida con un salario superior a los 1.500 euros brutos.

La pensión se deberá ingresar en los cinco días primeros de cada meses en la cuenta titularidad del cónyuge favorecido núm. [Nº], de la entidad financiera [COMPLETAR].

Dicha pensión se actualizará automáticamente cada doce meses, incrementándose o disminuyéndose según el IPC que publique el Instituto Nacional de Estadística u otro organismo oficial que pudiera sustituirle.

Quinto.– De la disolución y liquidación de la sociedad de gananciales.

El régimen económico del matrimonio es el de sociedad de gananciales, acordando ambas partes la disolución del mismo, de conformidad a lo dispuesto en el art. 1392 del CC y preceptos concordantes, así como su liquidación conforme a las siguientes estipulaciones:

I. Inventario de la sociedad de gananciales

Ambas partes de mutuo acuerdo manifiestan que la sociedad se compone el siguiente inventario de bienes:

I.A) ACTIVO DE LA SOCIEDAD

1. VIVIENDA sita en la localidad de [COMPLETAR], calle [CALLE], de una superficie de [COMPLETAR] metros cuadrados, y que es la finca registral núm. [Nº], inscrita en el Registro de la Propiedad de al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR].

La citada vivienda tiene la condición de VIVIENDA FAMILIAR y está valorada en el importe de [IMPORTE] euros, tal y como resulta de la valoración efectuada por la sociedad de tasación inmobiliaria

2. LOCAL sito en la localidad de [COMPLETAR], calle [CALLE], de una superficie de [COMPLETAR] metros cuadrados, y que es la finca registral núm. inscrita en el Registro de la Propiedad de al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR]. El citado local está valorado en el importe de [IMPORTE] euros, tal y como resulta de la valoración efectuada por la sociedad de tasación inmobiliaria

3. VEHÍCULO marca [MARCA/MODELO], modelo [MARCA/MODELO], número de bastidor [COMPLETAR], con matrícula [MATRÍCULA], de color [COMPLETAR], valorado según certificado emitido por el concesionario oficial de la marca en la localidad de [COMPLETAR], en el importe de [IMPORTE] euros.

4. DEPÓSITOS BANCARIOS en las entidades [COMPLETAR], números [COMPLETAR] por importe de [IMPORTE].

I. B) PASIVO DE LA SOCIEDAD

1. HIPOTECA por importe de [IMPORTE] euros y vencimiento, concedida por la entidad financiera [COMPLETAR], que grava la vivienda descrita en el apartado 1 del activo, y de la que, a fecha de hoy, y tal como consta en el certificado emitido por la citada entidad financiera que se acompaña como documento núm. 5, queda todavía por pagar la suma de [IMPORTE] euros.

2. PRÉSTAMO concedido por la financiera por importe de [IMPORTE] euros y vencimiento, que grava el vehículo mencionado en el apartado 3 del activo, y del que todavía resta por pagar la cantidad de [IMPORTE] euros.

II. Liquidación de la sociedad de gananciales

Ambas partes estipulan liquidar la sociedad de gananciales realizando las siguientes adjudicaciones y asunción de pasivo de cada cónyuge, difiriendo la liquidación de la vivienda familiar al momento en que finalice el uso pactado en las cláusulas segunda y tercera de este convenio, la cual se realizará en los términos que asimismo se pactan seguidamente.

Los lotes que se adjudican son los siguientes:

LOTE NÚMERO 1, adjudicado al cónyuge D/Dª [NOMBRE Y APELLIDOS], compuesto de los siguientes bienes, derechos y obligaciones:

Valor total del mismo: [COMPLETAR].

LOTE NÚMERO 2, adjudicado al cónyuge D/Dª [NOMBRE Y APELLIDOS], compuesto de los siguientes bienes, derechos y obligaciones:

Valor total del mismo:

Ambas partes manifiestan estar conformes en la valoración, quedando un remanente de [IMPORTE] euros a favor de D/Dª [NOMBRE Y APELLIDOS] que el otro cónyuge D/Dª [NOMBRE Y APELLIDOS] se obliga a satisfacer tan pronto se dicte la sentencia de divorcio, en compensación de la diferencia en el valor de los lotes adjudicados. obligándose ambas partes a formalizar cuantos documentos públicos, administrativos o privados sean necesarios para llevar a cabo la liquidación.

III. Liquidación de la vivienda familiar

Ambos cónyuges mantendrán la propiedad indivisa de la vivienda familiar descrita en el apartado 1 del activo durante el periodo de atribución del domicilio al padre/madre e hijos/as y hasta su extinción, con una cuota del 50% del inmueble y haciéndose cargo del pago de la hipoteca y gastos de comunidad por mitad.

Una vez finalizado el periodo de uso del domicilio familiar, ambas partes procederán a la división del inmueble, mediante su venta en la forma que convengan de mutuo acuerdo o por medio de agencia inmobiliaria, pactando expresamente que el cónyuge interesado tendrá derecho preferente a la adquisición de la vivienda familiar respecto de terceros compradores en las mismas condiciones.

Una vez realizada la venta, el precio obtenido será repartido por mitad.

Ambos cónyuges se comprometen a otorgar los documentos públicos y privados necesarios para la liquidación del inmueble.

Sexto.– Indivisibilidad de las disposiciones del presente convenio.

Todas las disposiciones del presente convenio constituyen un conjunto negocial indivisible, por lo que ambos cónyuges se comprometen a observarlo fielmente, obligándose a no interferir ni perturbar el libre y satisfactorio desarrollo de sus respectivas vidas privadas ni las posibles actividades personales o profesionales que ambos pudieran desarrollar.

Séptimo.– De las cuestiones formales.

Los cónyuges se obligan a otorgar los documentos públicos y firmar la documentación que sea necesaria para el fiel cumplimiento de lo pactado en este contrato, así como a efectuar las comparecencias ante Oficinas Públicas y Privadas a las que sean requeridos para dicho fin.

El presente convenio resuelve todas las diferencias existentes entre los cónyuges e implica transacción de todas las cuestiones planteadas entre los mismos, por lo que ambos se comprometen a solicitar su divorcio de mutuo acuerdo, constituyendo el presente documento como PROPUESTA DEL CONVENIO REGULADOR de todos sus efectos.

Los cónyuges manifiestan su voluntad de acudir a la autoridad competente para obtener su divorcio, acompañando a la demanda de divorcio de mutuo acuerdo el convenio aquí estipulado.

Y en prueba de conformidad, los comparecientes se ratifican en el contenido de todos y cada uno de los pactos que integran el presente documento, los cuales han sido redactados según sus propias instrucciones, firmándolo por triplicado y a un solo efecto en el lugar y fecha arriba indicados, quedando uno de ellos en poder de cada uno de los esposos, y el tercero en poder de esta representación a efectos de a presentarlo con la demanda de divorcio de mutuo acuerdo.

Asimismo, en prueba de conformidad sobre la estipulación segunda, los hijos mayores de edad firman el presente convenio, a los efectos de expresar su consentimiento sobre las medidas que les afectan establecidas en el pacto segundo del convenio.
