---
name: demanda-ordinaria-cobro-lo-indebido-389
description: "Redacta el escrito «Demanda ordinaria de cobro de lo indebido» (formulario 389 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria de cobro de lo indebido

> Formulario 0389 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] LOCALIDAD (5 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] COLEGIO
- [ ] IMPORTE (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] Nº
- [ ] FECHA (6 veces)
- [ ] NÚMERO (4 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de Procurador/aes de»; «…al»; «…al [COMPLETAR] para el vehículo»; «…mo la denuncia formulada como documentos»; «…de automóviles suscrita, por la Compañía»; «…, se realizó un pago de»; «…se encuentra en el depósito municipal de»; «…iante correspondencia escrita, en fechas»; «…cuantía del presente procedimiento es de»

## Elecciones que hay que hacer

- D./Doña / la mercantil
- NIF / CIF

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTROSI DIGO que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos proc…
- SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 85 de la LOPJ
- artículo 10 LEC
- artículo 7.1 LEC
- artículo 23 LEC
- artículo 31 LEC
- artículos 249.2 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 1895 CC
- artículo 1900 CC
- artículo 1901 CC
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

### Formulario 0389 · Demanda ordinaria de cobro de lo indebido

- Año del modelo: 2019
- Revisión 17-11-2026: 7 desplegables convertidos en elección en blanco; 2 párrafos opcionales señalados; 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio declarativo ordinario sobre reclamación de cantidad por cobre de lo indebido, conforme a lo establecido en los artículos 1.895 y siguientes del Código Civil.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A la Sección Civil del Tribunal de Instancia de [SEDE] que por turno de reparto corresponda de [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, Coleg. del Ilustre Colegio de Procurador/aes de [COMPLETAR], actuando en nombre y representación de [ELEGIR: D./Doña / la mercantil], con domicilio en [LOCALIDAD] y
NIF
CIF
  en virtud de escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO], y bajo la dirección letrada de D/Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparece y como mejor proceda en Derecho DICE

Que por medio del presente escrito vengo a formular DEMANDA JUICIO ORDINARIO SOBRE RECLAMACION DE CANTIDAD POR COBRO DE LO INDEBIDO por un importe de [IMPORTE], según lo establecido en los artículos 1895 y ss CC, frente a [ACTO O RESOLUCIÓN], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF].

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Todo ello en base a los siguientes:

HECHOS

PRIMERO.- D./Dña. [NOMBRE Y APELLIDOS] suscribió con la entidad ahora demandante, póliza de seguro de automóviles, núm. con periodo de vigencia desde el [FECHA] al [COMPLETAR] para el vehículo [COMPLETAR] de su titularidad. Se acompaña como documento acreditativa de tal extremo póliza de seguro como documento núm. [NÚMERO].

SEGUNDO.- Que en las condiciones particulares de dicha póliza se incluía la cobertura de robo del vehículo. Se acredita tal extremo mediante las condiciones particulares del seguro que se acompaña como documento núm. [NÚMERO].

TERCERO.- La ahora demandada, con fecha [FECHA] comunica siniestro a la compañía de seguros parte de siniestro de sustracción del vehículo asegurado, con cargo a la garantía de "robo de vehículo asegurado" de la póliza contratada acompañando la denuncia formulada. Se acredita tal extremo mediante parte dado a la compañía aseguradora así como la denuncia formulada como documentos [COMPLETAR].

CUARTO.- A consecuencia de dicho parte y por la cobertura incluida en las condiciones particulares de la póliza de seguro de automóviles suscrita, por la Compañía [COMPLETAR], se realizó un pago de [COMPLETAR] en concepto de indemnización por sustracción del vehículo en el número de cuenta indicado por la asegurada. Se acredita tal extremo mediante orden de transferencia al número de cuenta indicado como documento núm. [NÚMERO].

QUINTO.- Con fecha [FECHA] la compañía aseguradora tras varias investigaciones tiene conocimiento que el vehículo se encuentra en el depósito municipal de [COMPLETAR] desde la fecha [FECHA],día inmediatamente anterior a la fecha de comunicación de parte del siniestro, solicitando informe al Ayuntamiento de [LOCALIDAD] a fin de que indicara la fecha desde la cual el vehículo se encontraba en el depósito municipal, así como notificación remitida al titular del vehículo a efectos de proceder a su retirada.

SEXTO.- Desde que mi mandante ha tenido conocimiento del error producido en el abono realizado, se ha puesto en contacto con la demandada a fin de que restituyese la indemnización transferida, sin haber recibido respuesta alguna al respecto, ni haber procedido a la restitución de la misma. Se acredita tal extremo mediante burofax remitido a la asegurada como documento núm. [NÚMERO].

SÉPTIMO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

Primero.- Jurisdicción y competencia.

Corresponde al orden jurisdiccional civil conocer del asunto en base al art. 36 Ley de Enjuiciamiento Civil y artículos 9, 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ).

Corresponde la competencia objetiva y territorial al Tribunal al que nos dirigimos conforme a lo dispuesto en los artículos 45 y 52.1.1º de la LEC y en el artículo 85 de la LOPJ.

Segundo.- Capacidad y legitimación

a. Activa: Corresponde a [ELEGIR: D./Doña / la mercantil], con [ELEGIR: NIF / CIF], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC, en concreto, de solvens que por error ha realizado el abono de la indemnización, cantidad que no se debía.

b. Pasiva: Corresponde a la demandada, [ELEGIR: D./Doña / la mercantil], con [ELEGIR: NIF / CIF], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC, en concreto, de accipiens.

Ambas partes tienen capacidad para ser parte conforme dispone el artículo 6.1.1º LEC, respecto a la actora, y 6.1.1º o 6.1.3 LEC respecto a la demandada.

Igualmente tiene la actora capacidad procesal según lo dispuesto en el artículo 7.1 LEC.

Tercero.- Representación y defensa

Comparece la actora representada por Procurador/a, según lo dispuesto en el artículo 23 LEC y asistida de Letrado, conforme a lo contenido en el artículo 31 LEC.

Cuarto.- Cuantía

La cuantía del presente procedimiento es de [COMPLETAR].

Quinto.- Procedimiento

Conforme a lo dispuesto en los artículos 249.2 LEC, excediendo la cantidad reclamada de los quince mil euros, corresponde dar a la presente demanda la tramitación prevista parta el juicio ordinario, de los artículos 399 y ss LEC.

Sexto.- Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Séptimo.- Fundamentos jurídico materiales

Será de aplicación el artículo 1895 CC en relación al cobro de lo indebido, que establece que cuando se recibe alguna cosa que no había derecho a cobrar, y que por error ha sido indebidamente entregada, surge la obligación de restituirla. Concurren todos y cada uno de los requisitos exigidos jurisprudencialmente (STS 534/2010, de 30 de julio); que para la existencia del negocio jurídico que constituye el cobro o pago de lo indebido son tres:

• El pago efectivo realizado por el presunto deudor con la finalidad de extinguir la deuda, "animus solvendi", entendido como la entrega de cuerpo cierto in genere. El animus solvendi no es otra cosa que la voluntad del deudor de pagar.

Mi mandante realiza el pago de la indemnización con el único propósito de dar eficacia a la cobertura contratada por sustracción de vehículo en la póliza suscrita.

• La inexistencia de obligación entre el que paga y el que recibe, denominado indebitum, y, por consiguiente, la falta de causa en el pago, existiendo un indebitum ex persona, a pesar de existir un vínculo jurídico que se habría generado a partir del la contratación del seguro, no existe causa puesto que la causa que genera la cobertura incluida en las condiciones particulares, es inexistente. No se produce sustracción alguna del vehículo y por tanto no ha de ser cubierto.
• Error por parte del que hizo el pago, mi mandante, en la errónea creencia de estar obligado por la póliza suscrita abonando la indemnización correspondiente al valor del vehículo en la fecha en que se produce la posible sustracción.

En relación a la prueba, conforme dispone el artículo 1900 CC, corresponde al que hubiera hecho el pago acreditarlo, así como el error alegado. En este sentido, se ha acredita el pago realizado mediante las facturas presentadas y los movimientos bancarios de la cuenta titularidad de mi mandante. Y a pesar de acreditar el error pagado, en aplicación al artículo 1901 CC, se establece la presunción del error al haberse realizado un pago que no es debido, que no puede ser desvirtuado por la mera alegación de liberalidad o por otra causa justa.

Octavo.- Costas

Procede la condena en costas de la parte demandada por el principio cuasiobjetivo de vencimiento al amparo del artículo 394 LEC, al ver vistas, ésta, rechazadas todas sus pretensiones, sin que exista duda, de hecho o derecho, alguna.

Por lo expuesto

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con los documentos y copias que se acompañan, y a mí por comparecido y parte en la representación que ostento, se sirva admitirlo, tenga por formulada DEMANDA DE JUICIO ORDINARIO, SOBRE RECLAMACIÓN DE CANTIDAD POR COBRO DE LO INDEBIDO a frente a [ELEGIR: D./Doña / la mercantil], con domicilio en [LOCALIDAD] y
NIF
CIF
  y previos los trámites legales dicte en su día sentencia en la que, estimando la demanda, y en su virtud DECLARE:

• La obligación de la demandada al abono de la cantidad de [IMPORTE], coincidente con el importe de la indemnización, más los intereses legales de dicha cantidad, así como el abono de las costas procesales.

Por ser Justicia que pide en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

PRIMER OTROSI DIGO que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC., y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.

Firma del Abogado/a	Firma del Procurador/a
