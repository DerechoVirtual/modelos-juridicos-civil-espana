---
name: escritura-usufructo-vidual-universal-reciproco-galicia-536
description: "Redacta el escrito «Escritura de usufructo vidual universal recíproco (Galicia)» (formulario 536 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de usufructo vidual universal recíproco (Galicia)

> Formulario 0536 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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

- [ ] AÑO (4 veces)
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] FECHA (4 veces)
- [ ] LOCALIDAD (6 veces)
- [ ] Nº (11 veces)
- [ ] DATO REGISTRAL (9 veces)
- [ ] IMPORTE (5 veces)
- [ ] DÍA
- [ ] en su caso
- [ ] SUPERFICIE
- [ ] es previsión es potestativa
- [ ] Otros 50 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…NÚMERO En A Coruña, mi residencia, a de»; «…de [AÑO]. Ante mí»; «…presente escritura pública. Que DON/DOÑA»; «…se identifican seguidamente: 1º.- Planta»; «…stina a usos comerciales o industriales,»; «…. Ocupa la superficie útil aproximada de»; «… fachada principal del inmueble: frente,»; «…; derecha entrando,»; «…alada en el citado plano con los números»; «…. Cuota:»; «…sponde el número de referencia catastral»; «…EUROS Y»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5 de la Ley Orgánica 15/1999
- Ley 2/2006
- Ley 8/1989

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

### Formulario 0536 · Escritura de usufructo vidual universal recíproco (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 6 campos de relleno marcados en blanco; 89 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, DATO REGISTRAL, DÍA, FECHA, IMPORTE, LOCALIDAD, NOMBRE Y APELLIDOS, Nº, SUPERFICIE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

NÚMERO

En A Coruña, mi residencia, a de [COMPLETAR] de [AÑO].

Ante mí [COMPLETAR], Notario del Ilustre Colegio de Galicia,

COMPARECEN

INTERVIENEN, ambos en su propio nombre y derecho.

DECLARAN: Que, en el momento de otorgamiento de la presente escritura pública, ambos comparecientes tienen la vecindad civil gallega.

IDENTIFICO a los comparecientes por sus referidos documentos; tienen, a mi juicio, la capacidad de obrar y la legitimación necesarias para otorgar la presente escritura de PACTO SUCESORIO DE CONSTITUCIÓN DE USUFRUCTO VIDUAL UNIVERSAL RECÍPROCO, y a este efecto,

EXPONEN

Que DON/DOÑA [NOMBRE Y APELLIDOS] y DON/DOÑA [NOMBRE Y APELLIDOS] contrajeron matrimonio en fecha [FECHA], conforme me acreditan en virtud del certificado emitido por el Registro Civil de [LOCALIDAD] / en su caso, son pareja de hecho inscrita en el Registro de Parejas de Hecho de Galicia, conforme me acreditan en virtud de certificado emitido por el responsable del mismo en fecha [FECHA], cuya vigencia me aseguran y cuya copia, a efectos de prueba, dejo unida a la matriz de las presente escritura pública.

Que DON/DOÑA [COMPLETAR] es dueño, con carácter privativo, de los dos bienes inmuebles y de las participaciones sociales que se identifican seguidamente:

1º.- Planta [COMPLETAR], de la casa número [Nº], sita en la calle Prolongación de la de Barcelona. Está situada bajo la rasante de la calle de su situación y se destina a usos comerciales o industriales, [COMPLETAR]. Ocupa la superficie útil aproximada de [COMPLETAR], siéndole inherente un derecho conjunto de copropiedad con las demás plantas del edificio sobre los elementos comunes necesarios para su adecuado uso y disfrute. Linda, tomando referencia la fachada principal del inmueble: frente, [COMPLETAR]; derecha entrando, [COMPLETAR], y en parte la referida rampa de acceso; izquierda, el solar número [Nº]; y espalda, finca de Don [NOMBRE Y APELLIDOS], señalada en el citado plano con los números [COMPLETAR].

Cuota: [COMPLETAR] centésimas.

Inscripción: Registro de la Propiedad número [Nº] en el Libro [DATO REGISTRAL], Folio [DATO REGISTRAL], finca número [Nº], inscripción [DATO REGISTRAL].

Datos Catastrales: Le corresponde el número de referencia catastral [COMPLETAR].

Cargas y arrendamientos: Libres de cargas y sin arrendar.

Valor.- Este piso se valora en la suma de [IMPORTE] EUROS Y [COMPLETAR] CÉNTIMOS ( €).

2º.- TÉRMINO MUNICIPAL DE [COMPLETAR].- Local destinado a plaza de garaje y trastero, en la plaza de sótano de un edificio radicante en la parcela [COMPLETAR], de [COMPLETAR], municipio de [LOCALIDAD], de dieciocho metros y noventa decímetros cuadrados de superficie. Linda, viendo el local desde su frente: Frente-Norte, [COMPLETAR]; derecha entrando-Oeste, plaza de garaje número [Nº]; izquierda-Este, plaza de garaje número [Nº]; y fondo-Sur, muro que separa del subsuelo de la parcela [COMPLETAR].

Es la plaza de garaje número [Nº] de la Escalera [COMPLETAR], Bloque [COMPLETAR].

Cuota de participación en los elementos comunes del inmueble: [COMPLETAR] centésimas.

Referencia catastral.- Catastrada bajo la referencia catastral [COMPLETAR], según resulta de certificación catastral descriptiva y gráfica, que yo, el Notario, doy fe de haber solicitado a efectos del presente otorgamiento y obtenido por los procedimientos telemáticos seguros habilitados (de conformidad con la resolución de 24 de noviembre de 2008, de la Dirección General del Catastro), que incorporo a esta matriz.

Inscripción.- Registro de la Propiedad de [LOCALIDAD], Libro [DATO REGISTRAL] de [COMPLETAR], folio [COMPLETAR], finca número [Nº].

Título.- Le corresponde en virtud de compraventa otorgada por los cónyuges Don [NOMBRE Y APELLIDOS] y Dñª [COMPLETAR], formalizada en escritura pública autorizada por el Notario del Ilustre Colegio de Galicia Don [NOMBRE Y APELLIDOS] en fecha [FECHA] de [COMPLETAR] de [AÑO], bajo el número de su protocolo [DATO REGISTRAL].

Cargas y gravámenes.- La finca se encuentra libre de cargas y gravámenes, así como de inquilinos y ocupantes y con todos los derechos a la misma que son inherentes al derecho de propiedad.

Valor.- Esta plaza de garaje se valora en la suma de [IMPORTE] EUROS Y CINCUENTA Y [COMPLETAR] CÉNTIMOS ( €).

3º.- [COMPLETAR] participaciones sociales de la sociedad mercantil «, S.L.» («, S.L.»), identificadas con los números [COMPLETAR] a [DÍA], ambos incluidos, con un valor nominal cada una de ellas de [IMPORTE] €. La mencionada sociedad, con domicilio social en [COMPLETAR]; fue constituida, por tiempo indefinido, mediante escritura pública y se haya inscrita en el Registro Mercantil de [LOCALIDAD], en el Tomo [DATO REGISTRAL] del Archivo, Sección General, Folio [DATO REGISTRAL], Hoja núm. [Nº] y con C.I.F. B-[COMPLETAR].

DON/DOÑA [COMPLETAR] manifiesta asimismo que le pertenecen las acciones antes relacionadas en el concepto indicado, aportando certificado expedido en fecha XX de [COMPLETAR] de [AÑO] por la entidad depositaria de las acciones objeto del pacto de apartación que se formaliza en esta escritura pública, que me exhibe y que se incorpora a la matriz de esta escritura pública a efectos de prueba; al tiempo que manifiesta que no existe limitación estatutaria alguna a la libre transmisiblidad de las referidas participaciones sociales en virtud de negocio jurídico con eficacia mortis causa.

Valor: La totalidad de las participaciones sociales objeto de transmisión se valoran en la suma de [IMPORTE] €, de conformidad con el informe de valoración de la referida sociedad mercantil realizado por un experto independiente, cuya copia se incorpora a la matriz de la presente escritura pública.

Que DON/DOÑA [COMPLETAR] es dueña, con carácter privativo, de los bienes inmuebles y de la cartera de valores que seguidamente se identifican:

1º.- [COMPLETAR]

Que DOÑA/DON [COMPLETAR] y DON/DOÑA [NOMBRE Y APELLIDOS], son dueños en régimen económico matrimonial de gananciales [en su caso] del siguiente bien inmueble:

TÉRMINO MUNICIPAL DE [COMPLETAR].- Local comercial, en la planta baja de un edificio radicante en la parcela [COMPLETAR], de [COMPLETAR], municipio de [LOCALIDAD], de [SUPERFICIE] metros y [COMPLETAR] decímetros cuadrados de superficie. Linda, viendo el local desde su frente: Frente-Norte, [COMPLETAR]; derecha entrando-Oeste, local comercial [COMPLETAR]; izquierda-Este, edificio núm. [Nº] de la misma Calle; y fondo-Sur, muro que separa del subsuelo de la parcela [COMPLETAR].

Cuota de participación en los elementos comunes del inmueble: [COMPLETAR] centésimas.

Referencia catastral.- Catastrado bajo la referencia catastral [COMPLETAR], según resulta de certificación catastral descriptiva y gráfica, que yo, el Notario, doy fe de haber solicitado a efectos del presente otorgamiento y obtenido por los procedimientos telemáticos seguros habilitados (de conformidad con la resolución de 24 de noviembre de 2008, de la Dirección General del Catastro), que incorporo a esta matriz.

Inscripción.- Registro de la Propiedad de [LOCALIDAD], Libro [DATO REGISTRAL] de [COMPLETAR], folio [COMPLETAR], finca número [Nº].

Título.- Le corresponde en virtud de compraventa otorgada por los cónyuges Don [NOMBRE Y APELLIDOS] y Dñª [COMPLETAR], formalizada en escritura pública autorizada por el Notario del Ilustre Colegio de Galicia Don [NOMBRE Y APELLIDOS] en fecha [FECHA] de [COMPLETAR] de [AÑO], bajo el número de su protocolo [DATO REGISTRAL].

Cargas y gravámenes.- La finca se encuentra libre de cargas y gravámenes, así como de inquilinos y ocupantes y con todos los derechos a la misma que son inherentes al derecho de propiedad.

Valor.- Este local comercial se valora en la suma de [IMPORTE] EUROS Y CINCUENTA Y [COMPLETAR] CÉNTIMOS ( €).

Expuesto lo que antecede, al amparo de lo dispuesto en los artículos 228 y concordantes de la Ley 2/2006, de Derecho civil de Galicia y por medio de la presente escritura,

OTORGAN

Pactan la atribución recíproca del usufructo vitalicio sobre el derecho que a cada uno de ellos corresponde en los dos bienes objeto de esta escritura y sobre cuantos otros fuesen de su recíproca propiedad en el momento de causarse la herencia de cada uno de ellos, con todo lo que en ellos se hallare y con cuantas accesiones, mejoras y derechos les correspondiesen en ese momento. Este pacto se formaliza al amparo del artículo 228 de la Ley de Derecho Civil de Galicia y se hace con carácter irrevocable [es previsión es potestativa].

Disponen expresamente la vigencia y el mantenimiento del usufructo vidual universal y vitalicio para el caso de que el viudo contrajese nuevas nupcias o conviviese maritalmente con otra persona.

Relevan al cónyuge supérstite que reciba el usufructo universal que se instituye recíprocamente de cualquier obligación de formación de inventario de los bienes usufructuados y de prestar fianza.

El usufructuario tendrá la facultad de enajenar cuantos bienes muebles, incluidas participaciones y acciones sociales, que queden en la herencia con la finalidad de pagar las deudas hereditarias.

Todos los gastos derivados de esta escritura pública serán de cargo de los otorgantes.

Los impuestos y arbitrios que se devenguen como consecuencia del pacto que se documenta, serán imputados de conformidad con las previsiones legales.

Solicitan de la Oficina Liquidadora la aplicación de las reducciones personales, deducciones y exenciones contempladas en el Decreto Legislativo 1/2011, de 28 de julio, por el que se aprueba el texto refundido de las disposiciones legales de la Comunidad Autónoma de Galicia en materia de tributos cedidos por el Estado.

PRESENTACIÓN TELEMÁTICA.- De conformidad con el artículo 249 del Reglamento Notarial, remito copia autorizada electrónica del presente instrumento, para su constancia al Registro de Actos de Última Voluntad.

Hago las reservas y advertencias legales y, a efectos fiscales, las relati­vas a las obligacio­nes y respon­sabilidades que incumben a las partes en su aspecto material, formal y sancio­nador, y a las consecuen­cias de toda índole que se deriva­rían de la inexacti­tud de sus declara­ciones. Advier­to, en especial de las obliga­ción relativa al plazo de presentación de esta escritura a liquidación de los Impuestos sobre Sucesiones y Donaciones y sobre la afec­ción de los bienes al pago del primero de dichos Impuestos y de las respon­sabili­da­des en caso de no presentación, así como de los efectos de la Ley 8/1989.

Hechas las reservas legales oportunas, en especial las relativas al artículo 5 de la Ley Orgánica 15/1999, de protección de datos de carácter personal.

Leo esta escritura a los comparecientes, por su elección, previa advertencia y renuncia de la interesada a su derecho a leerlo por sí mismas y, enterados de su contenido, la aprueban y firman conmigo, el Notario, que doy fe de que el consentimiento ha sido libremente prestado, de que se adecua a la voluntad debidamente informada de los otorgantes y de haberse observado todas las formalidades legales anteriormente expresadas, de todo lo demás contenido en folios de clase Notarial, números [COMPLETAR], y de ser las

========================================================================
