---
name: reconocimiento-espana-sentencia-rusa-convenio-espana-628
description: "Redacta el escrito «Reconocimiento en España de sentencia rusa (Convenio España-URSS de 1990)» (formulario 628 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconocimiento en España de sentencia rusa (Convenio España-URSS de 1990)

> Formulario 0628 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LUGAR (4 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO (5 veces)
- [ ] FECHA (4 veces)
- [ ] PEDRO (3 veces)
- [ ] CALLE
- [ ] NÚMEROFUNDAMENTO
- [ ] En su caso (2 veces)
- [ ] CATALINA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ales, en representación de Doña Catalina»; «…rma del Abogado/a Firma del Procurador/a»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- - [En su caso] Una certificación del Letrado de la Administración de Justicia del tribunal haciendo constar qu…
- - [En su caso] Una copia certificada conforme de la citación hecha a la parte condenada en rebeldía (documento…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 36 LEC
- art. 85.5 LOPJ
- art. 52.1 de la Ley 29/2015
- art. 2 de la Ley 29/2015

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

### Formulario 0628 · Reconocimiento en España de sentencia rusa (Convenio España-URSS de 1990)

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 2 llamadas a nota sin texto retiradas; 2 párrafos opcionales señalados; 6 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de reconocimiento en España de sentencia dictada en Rusia según el Convenio España-URSS de 1990Formulario adaptado a la reforma procesal de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE [LUGAR]D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en representación de Doña Catalina [COMPLETAR], según acredito mediante la escritura de poder que acompaño, y con la intervención del Letrado que suscribe, colegiado n.º [NÚMERO] del Ilustre Colegio de Abogados de [LUGAR], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:Que por medio del presente escrito formulo SOLICITUD DE RECONOCIMIENTO DE LA SENTENCIA de fecha [FECHA], pronunciada por el Tribunal de asuntos civiles del Tribunal Municipal de Moscú (Federación Rusa), para que pueda dicha sentencia extranjera ser cumplida y en su caso ejecutada en España, con arreglo a lo establecido por el Convenio entre el Reino de España y la Unión de Repúblicas Socialistas Soviéticas sobre asistencia judicial en materia civil, firmado en Madrid el 26 de octubre de 1.990, citándose al demandado Don [PEDRO], domiciliado en la ciudad de [LUGAR], calle [CALLE], número [NÚMEROFUNDAMENTO] la solicitud en los siguientes hechos y consideraciones jurídicas:HECHOSPRIMERO.- En fecha [FECHA], el Tribunal de asuntos civiles del Tribunal Municipal de Moscú (Federación Rusa), dictó sentencia por la que se establecían las medidas relativas a la guarda y custodia y de patria potestad de los hijos menores habidos en el matrimonio con Don [PEDRO]

SEGUNDO.- La sentencia adquirió firmeza en fecha [FECHA] habiéndose dictado como consecuencia de una acción civil ejercitada por mi representada contra Don [PEDRO], incluida dentro del ámbito de aplicación del Convenio entre el Reino de España y la Unión de Repúblicas Socialistas Soviéticas sobre asistencia judicial en materia civil, firmado en Madrid el 26 de octubre de 1.990, cumpliéndose todos los requisitos que establece el mismo para que se pueda dar a efecto su ejecución.A estos hechos le son aplicables los siguientes:FUNDAMENTOS DE DERECHOI.- COMPETENCIAEs de aplicación lo dispuesto en el art. 36 LEC, en cuanto determina la extensión y límites de la jurisdicción de los tribunales civiles españoles, y el art. 85.5 LOPJ, que atribuye a los Tribunales de Instancia el conocimiento de las solicitudes de reconocimiento y ejecución de sentencias extranjeras, salvo que por tratado o norma internacional se disponga la competencia de otro tribunal.

En el presente caso, es directamente aplicable el art. 24.3 del Convenio entre España y la antigua URSS, hoy Federación Rusa, de 26 de Octubre de 1.990 (en adelante, el Convenio), aplicable a Rusia en virtud de la figura de Derecho Internacional Público de la sucesión de Estados (ATS de 18 de abril de 2000, Rec. 178/2000), que señala en España a las Secciones Civiles de los Tribunales de Instancia como competentes objetivamente, por razón de la materia, para conocer de las solicitudes de reconocimiento y homologación de las sentencias civiles allí dictadas.

Es territorialmente competente el Tribunal del domicilio del demandado, por aplicación de lo dispuesto en el art. 52.1 de la Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil (en lo sucesivo LCJIMC), que establece que la competencia para conocer de las solicitudes de exequátur corresponde a los Tribunales de Instancia del domicilio de la parte frente a la que se solicita el reconocimiento o ejecución, o de la persona a quien se refieren los efectos de la resolución judicial extranjera.II.- PROCEDIMIENTOSerán aplicables los arts. 52 y siguientes LCJIMC.III.- CAPACIDAD Y LEGITIMACIÓNMi mandante Doña Catalina es española, goza del pleno ejercicio de sus derechos civiles y ostenta interés legítimo para deducir el derecho ante el Estado español (art. 54.1 LCJIMC).

La demanda se dirige frente a Don Pedro por ser la otra parte contra la que recayó la resolución que se pretende reconocer y ejecutar (art. 54.3 LCJIMC).IV.- POSTULACIÓN Y DEFENSAConforme exige el art. 54.1 LCJIMC se formula esta demanda a través de Procurador de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el Tribunal.V.- FUNDAMENTO LEGAL DE LA PETICIÓNEs aplicable al presente caso el Convenio España-URSS de 1.990, cuyo art. 24 establece en su apartado 5 que "Al permitir la ejecución de la resolución el Tribunal no la revisará en cuanto al fondo, sino que se limitará a determinar que se han cumplido las condiciones previstas en los artículos 18,19, 20 y 23".En este caso, la resolución rusa cumple todos los requisitos exigidos por el referido tratado, es decir:1.- La resolución es ejecutoria conforme a la ley rusa.2.- Las partes han sido legalmente citadas, según las normas rusas.3.- Emana de un órgano jurisdiccional competente según los arts. 19 y 20 del Convenio, no siendo asunto atribuido a la competencia exclusiva de los órganos jurisdiccionales españoles.4.- La ejecución de la resolución no afecta a la soberanía, seguridad o principios básicos de la legislación española.5.- Tampoco ha sido dictada en España sentencia ejecutoria entre las mismas partes y sobre los mismos hechos. Del mismo modo tampoco se encuentra pendiente en España ningún proceso entre las mismas partes y por el mismo objeto.VI.- INTERVENCIÓN DEL MINISTERIO FISCALResulta preceptiva la intervención del Ministerio Fiscal, según dispone el art. 54.8 LCJIMC, a cuyo efecto se le dará traslado de todas las actuaciones.VII.- DOCUMENTOS PRECEPTIVOS QUE SE APORTANEn cumplimiento de lo dispuesto en el art. 23 del Convenio, se aporta a la presente solicitud la siguiente documentación:-Una copia de la resolución con todas las condiciones necesarias para su autenticidad (documento núm. [NÚMERO]).

[OPCIONAL — incluir si procede]

- [En su caso] Una certificación del Letrado de la Administración de Justicia del tribunal haciendo constar que la resolución es ejecutoria (documento núm. [NÚMERO]).)

[OPCIONAL — incluir si procede]

- [En su caso] Una copia certificada conforme de la citación hecha a la parte condenada en rebeldía (documento núm. [NÚMERO]).- Las traducciones legalizadas de los documentos anteriores así como la de la solicitud (documentos núm. [NÚMERO]).

Por lo expuesto,

SUPLICO AL TRIBUNALque, teniendo por presentado este escrito con los documentos que lo acompañan y sus copias, por el Letrado de la Administración de Justicia se sirva admitirlo; tenerme por parte en la representación que ostento de Doña [CATALINA], y previo traslado a la parte contraria y al Ministerio Fiscal por el término legal, se sirva dictar Auto por el que se otorgue el reconocimiento en España a la sentencia extranjera referida.

Es justicia que pido en [LUGAR], a [FECHA].Firma del Abogado/a Firma del Procurador/a [COMPLETAR] Téngase en cuenta que, conforme indica su Preámbulo y expresamente dispone el art. 2 de la Ley 29/2015, de 30 de julio, de Cooperación jurídica internacional en materia civil, el régimen de exequátur regulado en su Título V se aplica siempre con carácter subsidiario respecto a normas de la Unión Europea y tratados internacionales en los que España sea parte, y las normas especiales del Derecho interno, por lo que, en caso de resoluciones dictadas por países no miembros de la UE con los que España mantenga algún tratado, deberá estarse a éste.

========================================================================
