---
name: servidumbre-paso-pacto-galicia-546
description: "Redacta el escrito «Servidumbre de paso por pacto (Galicia)» (formulario 546 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Servidumbre de paso por pacto (Galicia)

> Formulario 0546 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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
- [ ] AÑO
- [ ] DNI/NIE (2 veces)
- [ ] DOMICILIO (2 veces)
- [ ]  / incluir, en su caso, el régimen económico matrimonial
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DATO REGISTRAL (5 veces)
- [ ] título de adquisición (2 veces)
- [ ] en su caso, teniendo en cuenta la situación de interclusión –o enclavamiento- relativa de la finca identificada en el Expositivo I
- [ ] SUPERFICIE (2 veces)
- [ ] IMPORTE
- [ ] opcional
- [ ] Otros 26 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mi residencia, a de»; «…de [AÑO]. Ante mí»; «…licia, COMPARECEN De una parte: DON/DOÑA»; «…, vecino de»; «…, vecina de»; «…; estado civil»; «…. Exhiben sus DNI/NIF números»; «…y»; «…); siendo su vecindad civil la»; «…o de la finca siguiente: RÚSTICA.- Finca»; «…al tomo»; «…al tomo [COMPLETAR], libro»; …

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

### Formulario 0546 · Servidumbre de paso por pacto (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 3 campos de relleno marcados en blanco; 41 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, DATO REGISTRAL, DNI/NIE, DOMICILIO, IMPORTE, LOCALIDAD, LUGAR, NOMBRE Y APELLIDOS, SUPERFICIE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

NÚMERO

En [LUGAR], mi residencia, a de [COMPLETAR] de [AÑO].

Ante mí [COMPLETAR], Notario del Ilustre Colegio de Galicia,

COMPARECEN

De una parte:

DON/DOÑA [COMPLETAR], mayor de edad, titular del DNI número [DNI/NIE], vecino de [COMPLETAR], con domicilio en [DOMICILIO] y de estado civil [ / incluir, en su caso, el régimen económico matrimonial].

De otra parte:

DOÑA/DON, mayor de edad, titular del DNI número [DNI/NIE], vecina de [COMPLETAR], con domicilio en [DOMICILIO]; estado civil [COMPLETAR].

Exhiben sus DNI/NIF números [COMPLETAR] y [COMPLETAR] respectivamente.

INTERVIENEN, ambos en su propio nombre y derecho (o, en su caso, en representación de [NOMBRE Y APELLIDOS]); siendo su vecindad civil la [COMPLETAR].

Ambas partes se reconocen recíprocamente la capacidad de obrar y la legitimación suficiente para otorgar, con plena validez y eficacia, el presente negocio jurídico de CONSTITUCIÓN NEGOCIAL DE SERVIDUMBRE y

DICEN

Que Don/Doña [NOMBRE Y APELLIDOS] es propietario de la finca siguiente:

RÚSTICA.- Finca [COMPLETAR].

Inscrita en el Registro de la Propiedad de [LOCALIDAD] al tomo [COMPLETAR], libro [COMPLETAR] de [COMPLETAR], folio [COMPLETAR], finca [DATO REGISTRAL], inscripción [DATO REGISTRAL] ª.

REFERENCIA CATASTRAL: [COMPLETAR]

OPCIONES:

1ª.- Ha sido obtenida por el notario en forma telemática:

La que resulta de la certificación catastral descriptiva y gráfica; yo, el Notario, doy fe que, bajo mi responsabilidad, la he obtenido (por los procedimientos telemáticos habituales y de acuerdo con la Resolución de la DG del Catastro de 24 de noviembre de 2008) y ha sido solicitada a los efectos del presente otorgamiento; esta certificación queda unida a esta matriz.

2ª.- No consta la gráfica, pero se ha obtenido certificación en la que consta la referencia catastral:

La que resulta de la certificación catastralúnicamente descriptiva, que Yo, el Notario, Doy fe que, bajo mi responsabilidad, he obtenido (por los procedimientos telemáticos habituales y de acuerdo con la Resolución de la DG del Catastro de 24 de noviembre de 2008) y ha sido solicitada a efectos del presente otorgamiento, certificación que incorporo a esta matriz.

3a.- No se aporta referencia concreta (ninguna o sólo la de la finca matriz, aunque conste ésta) y no se ha obtenido por el notario en forma telemática.

a): No tiene todavía referencia catastral concreta. Hago la advertencia de la obligación de hacer, ante la Gerencia Territorial del Catastro y en el plazo de dos meses, la pertinente declaración de la alteración de titularidad que se formaliza en esta escritura y en especial de las responsabilidades que indica la Ley en caso de no presentación en plazo o ser las declaraciones falsas, incompletas o inexactas.

b): No me ha sido aportada la referencia catastral concreta, y tampoco la he obtenido yo, el Notario en forma telemática. Hago la advertencia de la obligación de hacer, ante la Gerencia Territorial del Catastro y en el plazo de dos meses, la pertinente declaración de la alteración de titularidad que se formaliza en esta escritura y en especial de las responsabilidades que indica la Ley en caso de no presentación en plazo o ser las declaraciones falsas, incompletas o inexactas.

Coincidencia de la descripción catastral y la realidad física:

Se ha manifestado por los otorgantes, previa mi expresa solicitud, la coincidencia entre la realidad física y la que consta en la certificación catastral indicada y manifestando su conformidad con la nueva descripción de la finca realizada conforme a los datos catastrales actuales.

(Si hay discrepancias entre la realidad de la finca y el Catastro que no sean subsanables en el acto del otorgamiento, se indicará este hecho y, además, que se ha realizado o iniciado su rectificación, aplicando el supuesto que proceda conforme a lo que dispone el art. 18, Ley de Catastro (con última redacción dada por la Ley de Reforma de la Ley Hipotecaria.)

TÍTULO: Le pertenece en virtud de [título de adquisición]

OPCIÓN: Esta finca se encuentra en situación de interclusión relativa, pues la salida que tiene a la vía pública con la que colinda, en parte, por su viento [COMPLETAR] sólo es practicable a pie o a caballo, pero sin que pueda accederse o transitarse con vehículos agrícolas de tracción mecánica.

Que Don/Doña [NOMBRE Y APELLIDOS] es propietario de la finca siguiente:

RÚSTICA.- Finca [COMPLETAR]

Inscrita en el Registro de la Propiedad de [LOCALIDAD] al tomo [COMPLETAR], libro [COMPLETAR] de [COMPLETAR], folio [COMPLETAR], finca [DATO REGISTRAL], inscripción [DATO REGISTRAL] ª.

REFERENCIA CATASTRAL

TÍTULO: Le pertenece en virtud de [título de adquisición]

CONSTITUCIÓN DE SERVIDUMBRE NEGOCIAL O VOLUNTARIA DE PASO

a).- Los comparecientes, según intervienen, constituyen servidumbre de paso [en su caso, teniendo en cuenta la situación de interclusión –o enclavamiento- relativa de la finca identificada en el Expositivo I] para personas y vehículos maquinaria de uso agrario, sobre la finca registral [DATO REGISTRAL] (predio sirviente) y a favor de la registral [COMPLETAR] (predio dominante), y de las siguientes características:

Duración: perpetua; sin perjuicio del juego de extinción de las causas que determinan esta consecuencia y, en particular, en el caso de que, como consecuencia de la apertura de un nuevo vial público de comunicación o de la compra o adquisición de la propiedad por el propietario del fundo dominante de algunas de las fincas colindantes, o de parte de ellas, a través de la cuales se pueda acceder a la vía pública, deje de estar en situación de interclusión.

Clase: Servidumbre para paso de personas, animales, vehículos y maquinaria de uso agrario.

Características: La servidumbre se concreta en un camino que arranca del linde [COMPLETAR] del predio sirviente, dirección [COMPLETAR], atraviesa éste con una longitud de [SUPERFICIE] metros y una anchura de [SUPERFICIE] metros hasta llegar al predio dominante, en el punto [COMPLETAR]. Esta anchura se reputa suficiente para el adecuado y ordenado aprovechamiento de la finca dominante, conforme a su naturaleza y tipo de producción actual, sin perjuicio de su posible adecuación conforme dispone la Ley de Derecho Civil de Galicia.

b).- En contraprestación a la constitución de la servidumbre, el propietario del fundo dominante abona al propietario del fundo sirviente la suma de [IMPORTE] € que abona en virtud de transferencia bancaria, de cuyo extracto se aporta copia a efectos de prueba, incorporándose a la matriz de la presente escritura pública.

IV.- Los gastos y costes derivados del otorgamiento de la presente escritura pública serán a cargo del propietario del fundo dominante; al igual que los aranceles registrales en el caso de que pretendiese su inscripción registral.

V.- En el caso de extinción de la servidumbre de paso que se constituye en virtud del presente negocio por desaparecer, sobrevenidamente, su situación de interclusión relativa, el propietario del fundo sirviente no [opcional] tendrá obligación de restituir al propietario del fundo dominante el precio percibido como consecuencia de su constitución, en tanto que compensará con él el perjuicio padecido durante el tiempo de duración de la servidumbre de paso que se constituye.

Los impuestos y arbitrios que se devenguen como consecuencia del pacto que se documenta, serán imputados de conformidad con las previsiones legales.

Leo esta escritura a los comparecientes, por su elección, previa advertencia y renuncia de la interesada a su derecho a leerlo por sí mismas y, enterados de su contenido, la aprueban y firman conmigo, el Notario, que doy fe de que el consentimiento ha sido libremente prestado, de que se adecua a la voluntad debidamente informada de los otorgantes y de haberse observado todas las formalidades legales anteriormente expresadas, de todo lo demás contenido en folios de clase Notarial, números [COMPLETAR], y de ser las

========================================================================
