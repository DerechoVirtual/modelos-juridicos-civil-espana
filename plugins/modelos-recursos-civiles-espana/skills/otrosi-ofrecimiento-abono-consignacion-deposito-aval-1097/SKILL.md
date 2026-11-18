---
name: otrosi-ofrecimiento-abono-consignacion-deposito-aval-1097
description: "Redacta el escrito «Otrosí: ofrecimiento de abono, consignación, depósito o aval para preparar recursos» (formulario 1097 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí: ofrecimiento de abono, consignación, depósito o aval para preparar recursos

> Formulario 1097 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- Cita el art. 449.3 LEC anterior (mencionaba el recurso extraordinario por infracción procesal y decía «al prepararlos»). Corregido en procesal.json.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

El formulario no tiene campos marcados: revisa el texto por si hay datos implícitos.

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 449.6 de la LEC
- art. 449 de la LEC
- art. 148.2 de la LAU

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

### Formulario 1097 · Otrosí: ofrecimiento de abono, consignación, depósito o aval para preparar recursos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE
- Avisos de la revisión: Cita el art. 449.3 LEC anterior (mencionaba el recurso extraordinario por infracción procesal y decía «al prepararlos»). Corregido en procesal.json.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

OTROSÍ DIGO: Que a los efectos previstos en el art. 449.6 de la LEC, esta parte manifiesta su voluntad de abonar, consignar, depositar o avalar las cantidades correspondientes al importe de la condena más los intereses y recargos exigibles, que no se acredita en este momento porque

NUEVAMENTE SUPLICO AL TRIBUNAL: Tenga por hecha la anterior manifestación, a los efectos legales pertinentes.

Es justicia que reitero en mismo lugar y fecha.

NORMATIVA APLICABLE

Art. 449.6 de la LEC.

NOTAS ACLARATORIAS

En los supuestos en los que deba prevenirse cualquier posible déficit de acreditación documental del pago, consignación, depósito o aval se puede añadir un otrosí ofreciendo pagar, consignar, depositar o avalar las sumas que se establecen en cada uno de los supuestos del art. 449 de la LEC.

Debe tenerse en cuenta —como recuerda numerosa jurisprudencia menor, entre la que se puede destacar la sentencia de la de la Audiencia Provincial Asturias (Sección 5.ª) de 16 de mayo de 2006, rec. 192/2006— que en este supuesto entra en juego el mecanismo de subsanación de los actos procesales. Su base legal radica en los artículos 449.6, en relación con el 231 de la LEC, que instituyen un principio general de subsanación, que contempla el art. 449 de la LEC cuando el recurrente "hubiese manifestado su voluntad de abonar, consignar, depositar o avalar las cantidades correspondientes, pero no acreditara documentalmente, a satisfacción del tribunal, el cumplimiento de tales requisitos".

Es preciso distinguir, a efectos de la posibilidad de subsanación, dos supuestos netamente diferentes:

a) La falta de acreditación de la realización de depósito, cuando éste se ha efectuado en tiempo y forma, es un claro supuesto de subsanación amparado legalmente.
b) Por el contrario, la falta material de realización del depósito es un defecto que, según el criterio de diferentes Audiencias, no resulta subsanable.

El LAJ cuidará de que pueda ser subsanado el defecto cuando el recurrente hubiera manifestado su voluntad de abonar, consignar, depositar o avalar las cantidades correspondientes, pero no lo acreditara documentalmente.

La Audiencia Provincial de Baleares (Sección 4.ª), en sentencia de 21 de marzo de 2006, rec. 287/2005 (ponente: GELABERT FERRAGUT, Juana M.ª) estableció: "... de conformidad con lo dispuesto en el art. 449.3 no debía haberse admitido el recurso de apelación, pues la subsanación a que se refiere el apartado 6 del mencionado artículo en relación con el art. 231, lo es a los solos efectos de acreditar documentalmente con posterioridad el cumplimiento del requisito de la consignación, pero siempre que la misma se haya efectuado dentro del plazo establecido por la LEC para tener por solicitado la preparación del recurso de apelación; no cuando la repetida consignación se realiza después de transcurrido dicho plazo. Es decir, el cumplimiento del requisito ha de realizarse dentro del plazo inmediato a la notificación de la sentencia, establecido en cada caso por la LEC 1/2000 para la preparación del recurso de cuya interposición se trate, pues la dicción literal del art. 449.6 de la LEC permite corregir sólo el defecto de acreditación pero no autoriza a cumplir ‘extemporáneamente’ el defecto material del pago o la consignación...".

Para la Audiencia Provincial de Valencia (Sección 8.ª), sentencia de 26 de junio de 2006, rec. 317/2006; ponente: SÁNCHEZ ALCARAZ, Eugenio: "El obstáculo que inicialmente se advierte cara al éxito del recurso de apelación formulado es el derivado de la inobservancia de lo dispuesto en el artículo 449.3 de la Ley de Enjuiciamiento Civil. Este precepto establece que en los procesos en que se pretenda la condena a indemnizar los daños y perjuicios derivados de la circulación de vehículos de motor no se admitirán al condenado a pagar la indemnización, los recursos de apelación o casación si, al interponerlos, [NOTA DE REVISIÓN: El art. 449.3 LEC ya no menciona el recurso extraordinario por infracción procesal. Fuente: LEC art. 449.3 (redacc. RDL 6/2023, BOE-A-2023-25758).] no acredita haber constituido depósito del importe de la condena más los intereses y recargos exigibles en el establecimiento destinado al efecto. Esta exigencia no ha sido observada correctamente por los hoy apelantes y aunque el artículo 449.6 del texto legal citado expresa que en los casos de los apartados anteriores, antes de rechazar o declarar desiertos los recursos, se estará a lo dispuesto en el artículo 231 de esta Ley, cuando el recurrente hubiese manifestado su voluntad de abonar, consignar, depositar o avalar las cantidades correspondientes, pero no acreditara documentalmente, a satisfacción del tribunal, el cumplimiento de tales requisitos, lo cierto es que ni en el escrito de preparación (fols. 224 y 225), ni en el de interposición (fols. 245 al 248 y 254 al 258), efectuaron manifestación alguna al respecto".

La Audiencia Provincial de Madrid (Sección 12.ª) mediante auto de 28 de septiembre de 2005, rec. 272/2005 (ponente: HERRERO DE EGAÑA Y OCTAVIO DE TOLEDO, Fernando) también interpreta que la acreditación del pago es requisito formal cuya inobservancia es susceptible de subsanación: "... la STC de 14 de septiembre de 1992, rec. 1726/1989, que por lo que se refiere a la necesidad de acreditar el pago o consignación de las rentas vencidas para la válida interposición y sustanciación de los recursos planteados en los procesos arrendaticios, según exigen tanto la LAU (art. 148.2) como la LEC (art. 1566), este Tribunal, en las citadas resoluciones, ha considerado justificadas dichas exigencias legales por su objeto consistente en evitar que el arrendatario se valga del pleito para dejar de satisfacer la renta durante la tramitación del mismo (STC 104/1984), pero también ha manifestado que debe prevalecer una interpretación finalista o teleológica de dichas normas que tenga presente el sentido de las formas en el proceso y no convierta en obstáculo insalvable el incumplimiento involuntario y no malicioso de requisitos formales, siempre y cuando tales omisiones no impidan la marcha del proceso ni afecten a la finalidad perseguida por el legislador, que es la de asegurar los intereses del arrendador que ha obtenido una sentencia favorable, evitando que el proceso arrendaticio —y el derecho del arrendatario a acceder al sistema de recursos legalmente establecido— sea instrumentalizado como una maniobra dilatoria en claro perjuicio de la contraparte (SSTC 46/1989, 31/1992 y 51/1992). Una interpretación teleológica y finalista de tales normas en el sentido antes apuntado obliga a distinguir entre el hecho del pago o consignación previa al recurso y su acreditación (SSTC 46/1989, 49/1989, 62/1989, 121/1990, 31/1992 y 51/1992). En efecto, la prueba de que ese pago o consignación se ha realizado constituye un simple requisito formal, cuyos eventuales defectos son susceptibles de subsanación". Pero esta resolución se cuida de diferenciar la falta de acreditación de la falta de cumplimiento, estableciendo que: "Pero tal no es el caso respecto del hecho mismo del pago o consignación de las rentas vencidas, que viene a cumplir una finalidad cautelar y de legítima salvaguardia de los intereses del arrendador, configurándose, por tanto, según lo previsto en el art. 148.2 de la LAU y como tiene manifestado este Tribunal en las sentencias citadas, como un requisito esencial para el acceso al recurso".

========================================================================
