---
name: contestacion-demanda-verbal-cantidad-cobro-lo-indebido-384
description: "Redacta el escrito «Contestación a la demanda verbal de cantidad por cobro de lo indebido» (formulario 384 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda verbal de cantidad por cobro de lo indebido

> Formulario 0384 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] LUGARD
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NÚMERO (2 veces)
- [ ] LUGAR (3 veces)
- [ ] POBLACIÓN
- [ ] Nº DE DOCUMENTO
- [ ] RESOLUCIÓN QUE EMPLAZA
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] INDICAR OBJETO DE ADQUISICIÓN (2 veces)
- [ ] Seleccionar una u otra opción
- [ ] Seleccionar una o varias opciones
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e la documentación como documentos nums.»; «…lecido la exigencia de tres requisitos:•»; «…sa que la voluntad del deudor de pagar.•»; «…go, existiendo un indebitum ex persona.•»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1089 CC
- artículo 1901 CC
- artículo 1156 CC
- artículo 394 LEC
- art. 231 de la LEC

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

### Formulario 0384 · Contestación a la demanda verbal de cantidad por cobro de lo indebido

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 1 bloques de alternativas señalados; 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación escrita a demanda de juicio verbal sobre reclamación de cantidad por cobro de lo indebido.

Formulario adaptado a la reforma procesal de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE [LOCALIDAD], PLAZA N.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [LUGARD]./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, Coleg. [NÚMERO] de colegiado del Ilustre Colegio de Procuradores de [LUGAR], actuando en nombre y representación de [NOMBRE Y APELLIDOS]/Razón social, con domicilio en [POBLACIÓN], calle, número y piso y NIFCIF [NÚMERO], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección letrada de D/D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de Abogados de [LUGAR], ante el Tribunal comparece y como mejor proceda en Derecho DICE

Que habiendo sido notificado y emplazado mediante [RESOLUCIÓN QUE EMPLAZA], por medio del presente escrito, vengo a formular CONTESTACIÓN A LA DEMANDA DE JUICIO VERBAL SOBRE RECLAMACIÓN DE CANTIDAD POR COBRO DE LO INDEBIDO presentada por D./D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./D./Dña. [NOMBRE Y APELLIDOS] en base a las siguientesALEGACIONESHECHOSPRELIMINAREsta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito

PRIMERO

Conforme con el correlativo de la demanda en relación al pago realizado por la actora con fecha [FECHA] y por importe de [IMPORTE].

SEGUNDO

Disconforme con el correlativo de la demanda. Si bien manifiesta la actora que el cobro realizado es indebido, con fecha [FECHA] se adquirió por la misma [INDICAR OBJETO DE ADQUISICIÓN], adquisición que quedaría formalizada desde el momento en que recibiese el pedido en el domicilio, junto con el documento relativo al derecho de desistimiento que debería remitir firmado y por correo certificado en el plazo de catorce días desde la recepción del mismo, de querer ejercer dicho derecho. Transcurrido dicho plazo, se entendería formalizado el contrato en todos sus extremos, procediendo la ahora demandada a cargar en la cuenta facilitada por la actora el precio total de la Colección. Se acompaña documento acreditativo de tal extremo el contrato firmado por la actora así como el acuse de recibo justificativo de la recepción de la documentación como documentos nums. [COMPLETAR].

TERCERO

Disconforme con el correlativo de la demanda. La actora alega error en el pago realizado cuando la cuenta bancaria es facilitada por el mismo, una vez que firma el contrato de adquisición recibido en el domicilio junto con el material adquirido. Contrato, que completa y remite mediante correo certificado a mi mandante. El pago realizado lo es con ánimo de extinguir la deuda que había adquirido.

CUARTO

Disconforme con el correlativo en relación a la inexistencia de causa justa. Transcurrido dicho plazo, se entendería formalizado el contrato en todos sus extremos, procediendo la ahora demandada a cargar en la cuenta facilitada por la actora el precio total de la adquisición.

QUINTO

Disconforme con el correlativo de la demanda. No puede hablar la actora de mala fe por parte de la demandada, existe un contrato por el cual se adquiere una colección legislativa, y una vez indicada la cuenta corriente donde se ha de efectuar el cargo, se presenta el recibo en la misma, sin que se haya ejercido el derecho de desistimiento alguno por parte de la actora, a pesar de haber sido informado del mismo.A los anteriores le son de aplicación los siguientesFUNDAMENTOS DE DERECHOPRIMEROConformes a los correlativos a la demanda sobre jurisdicción, competencia oponiéndose al resto de los alegados por no ser de aplicación o serlo "a sensu contrario"SEGUNDO

Conforme con el correlativo de la demanda sobre capacidad y legitimación.

TERCERO

Conforme con el correlativo sobre representación y defensa, así como procedimiento.-CUARTO

Oponiéndonos a los fundamentos jurídico-materiales alegados en relación al fondo del asunto por no ser de aplicación o ser de aplicación a sensu contrarioSe alega de contrario que será de aplicación el artículo 1895 en relación al cobro de lo indebido, que establece que cuando se recibe alguna cosa que no había derecho a cobrar, y que por error ha sido indebidamente entregada, surge la obligación de restituirla, Sin embargo, para poder hablar de la figura del cobro de lo indebido, la jurisprudencia (STS 534/2010, de 30 de julio, entre otras) ha establecido la exigencia de tres requisitos:• [COMPLETAR] El pago efectivo realizado por el presunto deudor con la finalidad de extinguir la deuda, "animus solvendi", entendido como la entrega de cuerpo cierto in genere. El animus solvendi no es otra cosa que la voluntad del deudor de pagar.• [COMPLETAR] La inexistencia de obligación entre el que paga y el que recibe, denominado indebitum, y, por consiguiente, la falta de causa en el pago, existiendo un indebitum ex persona.• [COMPLETAR] Error por parte del que hizo el pago.

Dicho esto, no concurren lo requisitos exigidos, cierto es que se realiza un pago efectivo mediante el cargo en la cuenta que no se ha negado. Sin embargo, existe una obligación contractual entre actora y demandada en virtud de un contrato por el cual se adquiere [INDICAR OBJETO DE ADQUISICIÓN], excluyéndose así el requisito de la inexistencia de obligación.

Tampoco existe error alguno por parte de quien realiza el pago, que ahora se reclama, el pago de las cantidades reclamadas está de sobra justificado por tener lugar en el seno de una relación contractual.

Por su parte, resulta de aplicación el artículo 1089 CC, por el cual se establece que las obligaciones nacen de la ley, de los contratos y cuasi contratos, y de los actos y omisiones ilícitos o en que intervenga cualquier género de culpa o negligencia, a su vez, el artículo 1901 CC dispone que las obligaciones nacidas de los contratos tienen fuerza de ley entre las partes contratantes y deben cumplirse a tenor de los mismos. Por último, el artículo 1156 CC dispone que las obligaciones se extinguen, entre otras causas, por el pago o cumplimento.

Aplicándolo al caso, la actora firmó un contrato, por el cual se comprometía a abonar el precio pactado, una vez recibido en su domicilio el objeto del mismo, por tanto, habiéndose recibido.

Por su parte, el artículo 71 del RD Leg 1/2007, de 16 de noviembre, por el que se aprueba el texto refundido de la Ley General para la Defensa de los Consumidores y Usuarios y otras leyes complementarias, establece el plazo mínimo para el ejercicio de desistimiento, habiendo sido informado del mismo, sin que en el plazo de catorce días se haya ejercido el mismo.

QUINTO CostasSe condenado el actor a las costas de la primera instancia por la temeridad y mala fe conforme el artículo 394 LEC.Por lo expuesto

SUPLICO AL TRIBUNAL,que me tenga por personado y comparecido en tiempo y forma en representación de [NOMBRE Y APELLIDOS]/Razón Social, y por CONTESTADA LA DEMANDA, y tras el curso legal, se dicte sentencia por la que se desestime la demanda interpuesta y condene a la actora al pago de las costas ocasionadas en la instancia.

Por ser Justicia que pide en [LUGAR], a [FECHA]. [Seleccionar una u otra opción]

[ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:]
— OTROSÍ DIGO: Que interesa a esta parte la celebración de vista, al existir controversia sobre los hechos y ser necesaria la práctica de prueba para la resolución de este proceso.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente, se sirva señalar la celebración de vista

OTROSÍ DIGO: Que esta parte no considera necesaria la celebración de vista.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente, se tenga por realizada a los efectos oportunos. [Seleccionar una o varias opciones]

SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC., y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.SUPLICOAL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.Firma del Abogado/a Firma del Procurador/a
