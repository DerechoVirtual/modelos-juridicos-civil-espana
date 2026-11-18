---
name: monitorio-cuotas-pendientes-gastos-requerimiento-1370
description: "Redacta el escrito «Monitorio por cuotas pendientes y gastos de requerimiento» (formulario 1370 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio por cuotas pendientes y gastos de requerimiento

> Formulario 1370 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE (7 veces)
- [ ] Nº
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a fecha ha impagado las mensualidades de»; «…rajudicial. En este sentido, se acudió a»; «… En este caso presentemos la petición en»; «…por ser»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Partes / Procurador / Presidente — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 813 de la LEC
- artículo 21.1 de la LPH
- artículo 21.6 de la LPH
- artículo 394.3 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículos 9.e) y 21.1 de la LPH
- artículo 21.3 de la LPH

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

### Formulario 1370 · Monitorio por cuotas pendientes y gastos de requerimiento

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 11 campos de relleno marcados en blanco; 9 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso monitorio

Petición inicial

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

[ELEGIR UNA OPCIÓN Y REDACTARLA: Partes / Procurador / Presidente — el texto de cada opción no venía en el formulario original]

Que mediante el presente escrito formulo petición inicial de procedimiento monitorio según permiten los artículos 21 de la Ley de Propiedad Horizontal (LPH) y 812.2.2.º de la Ley de Enjuiciamiento Civil (LEC) con objeto de que se requiera a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión, con domicilio en [LOCALIDAD], C/ y DNI n.º para que haga efectiva la cantidad de [IMPORTE] euros de principal que adeuda a la Comunidad en concepto de gastos comunes, más [IMPORTE] euros en concepto de gastos de requerimiento previo,. Basamos esta pretensión en los siguientes

HECHOS

(Para los Tribunales en los que se haya implantado la presentación de escritos a través del sistema telemático con firma electrónica-Lex Net y la Comunidad haya designado procurador para su representación).

Acompañamos como documento nº 1 índice numerado de los documentos que se presentan con esta petición inicial de procedimiento monitorio.

D./Dña. [NOMBRE Y APELLIDOS] es propietario de del edificio situado en la C/, según consta en la nota simple expedida por el Registro de la Propiedad n.º [Nº] que adjuntamos como documento n.º [Nº DE DOCUMENTO].

La cuota de participación que le corresponde es del %, según costa en el citado documento. En virtud de esta participación le corresponde contribuir a los gastos comunes con una cuota mensual de [IMPORTE] euros. Sin embargo, hasta la fecha ha impagado las mensualidades de [COMPLETAR], por lo que adeuda la cantidad de [IMPORTE] euros.

En fecha ha sido requerido, para que procediera a la liquidación de la deuda sin que hasta la fecha se haya hecho efectiva. Adjunto como documento n.º copia del citado requerimiento y como documento n.º factura de su importe, que asciende a [IMPORTE] euros.

En la Junta General Extraordinaria de la Comunidad de celebrada el día se acordó fijar la suma adeudada y reclamarla por vía judicial, autorizando al Presidente para que actuara en ese sentido ante los Tribunales en nombre de la Comunidad. Adjunto como documento n.º certificación del Secretario con el visto bueno del Presidente del acuerdo de la Junta aprobando la liquidación de la deuda de D./Dña. [NOMBRE Y APELLIDOS] con la Comunidad de Propietarios.

Como documento n.º acompaño acreditación de la notificación del acuerdo al deudor.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

En aplicación del artículo 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, corresponde al Tribunal de Instancia del domicilio del deudor o al lugar donde esté situada la finca. En este caso presentemos la petición en [COMPLETAR] por ser [COMPLETAR].

El artículo 249.8.º de la LEC excluye del ámbito del juicio ordinario las acciones de las Juntas de Propietarios que versen exclusivamente sobre reclamación de cantidad. El artículo 812.2.2.º del mismo texto legal permite utilizar el proceso monitorio para reclamar a los vecinos morosos los gastos comunes de Comunidades de Propietarios de inmuebles urbanos.

Los artículos 6.1.5.º y 7.6 de la LEC en relación con el artículo 21.1 de la LPH otorgan capacidad a las Comunidades de Propietarios para ser parte y a su Presidente o Administrador para actuar en su nombre.

No es preceptiva según establecen los artículos 23.2.1.º, 31.2.1.º y 814.2. de la LEC. Pero el artículo 21.6 de la LPH permite reclamar al comunero moroso los honorarios del Abogado y Procurador de que se sirva la Comunidad para reclamar las cantidades debidas, tanto si atiende al requerimiento de pago como si no comparece ante el Tribunal, y siempre con los límites del artículo 394.3 de la LEC.

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

PRIMERO.— Los artículos 9.e) y 21.1 de la LPH obligan a los comuneros a contribuir con arreglo a su cuota de participación a los gastos generales para el sostenimiento del inmueble y en caso de no hacerlo se les podrá reclamar judicialmente su pago.

SEGUNDO.— El artículo 21.3 de la LPH permite completar la cantidad reclamada con la derivada de los gastos de requerimiento previo de pago si se justifica su realización y su precio.

Con arreglo al artículo 21.6 de la LPH se impondrán al deudor tanto si atiende al requerimiento de pago como si no comparece ante el Tribunal.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copias de todo ello, lo admita y tenga por formulada petición inicial de procedimiento monitorio y en su virtud:

1.º Requiera el Letrado de la Administración de Justicia a D./Dña. [NOMBRE Y APELLIDOS] para que haga efectivo dentro del plazo legal el importe de las cuotas de Comunidad adeudadas que asciende a [IMPORTE] euros, más [IMPORTE] euros en concepto de requerimiento previo de pago, todo ello bajo apercibimiento de que, de no hacerlo, se dictará decreto dando por terminado el proceso y dando traslado a esta parte para instar ejecución por la cantidad adeudada como principal más costas e intereses de mora.

2.º O en caso de que formulara oposición en tiempo y forma se acuerde seguir la tramitación conforme a lo previso para el juicio verbal o se conceda a esta parte plazo para formular demanda de juicio ordinario.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

========================================================================
