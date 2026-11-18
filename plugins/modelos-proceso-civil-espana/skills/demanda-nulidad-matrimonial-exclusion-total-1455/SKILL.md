---
name: demanda-nulidad-matrimonial-exclusion-total-1455
description: "Redacta el escrito «Demanda de nulidad matrimonial por exclusión total» (formulario 1455 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de nulidad matrimonial por exclusión total

> Formulario 1455 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] NOMBRE DEL SOLICITANTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, católico, vecino de»; «…esia Católica, con domicilio conocido en»; «…y Dª»; «…y Dª [COMPLETAR], contando»; «…nio canónico en la Iglesia Parroquial de»; «…, de la localidad de»; «…, el día [FECHA] de»; «…, el día [FECHA] de [COMPLETAR] de»; «…n conyugal de Mutuo Acuerdo en el mes de»; «…de»; «…rtuna Sentencia de Separación recaída el»; «…de»; …

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

### Formulario 1455 · Demanda de nulidad matrimonial por exclusión total

- Año del modelo: 2014
- Revisión 17-11-2026: 36 campos de relleno marcados en blanco; 2 menciones a juzgados actualizadas (LO 1/2025); 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Rvdo. Tribunal Eclesiástico
Procurador, representación y asistencia Letrada
Interposición de demanda de nulidad
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Otrosí
Lugar y fecha
Firmas

AL REVERENDO. TRIBUNAL ECLESIÁSTICO DEL ARZOBISPADO DE [LOCALIDAD]

D. [NOMBRE Y APELLIDOS], Procurador de Tribunales y de D. [NOMBRE Y APELLIDOS], mayor de edad, católico, vecino de [COMPLETAR], calle [CALLE], nº [NÚMERO]; C.P., según resulta del Acta de mandato procuratorio y comisión a letrado que se acompaña, ante el Rvdo. Tribunal comparezco y DIGO:

Que en la representación y defensa que ostento y siguiendo instrucciones de mi mandante, interpongo demanda de NULIDAD DEL MATRIMONIO contraído por mi mandante con Dña. [NOMBRE Y APELLIDOS], mayor de edad, bautizada en la Iglesia Católica, con domicilio conocido en [COMPLETAR] calle [CALLE], nº [NÚMERO], C.P., la que se basa y fundamenta en los siguientes:

HECHOS

D. [NOMBRE Y APELLIDOS] y Dª [COMPLETAR], contando [COMPLETAR] y [Nº] años de edad respectivamente, contrajeron formalmente matrimonio canónico en la Iglesia Parroquial de [COMPLETAR], de la localidad de [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR].

Se adjunta a la presente demanda Partida de matrimonio con número [NÚMERO] de documentos.

De su unión matrimonial no ha nacido ningún hijo, no habiendo quedado la esposa embarazada en momento alguno durante la misma.

Los esposos, en el orden civil, formularon demanda de separación conyugal de Mutuo Acuerdo en el mes de [COMPLETAR] de [COMPLETAR], de la que conoció el Tribunal de Instancia (Sección Civil, plaza n.º [NÚMERO]) de [LOCALIDAD], la que, tras su oportuna tramitación, dio lugar a la oportuna Sentencia de Separación recaída el [COMPLETAR] de [COMPLETAR] de [COMPLETAR].

Posteriormente se tramitó ante la jurisdicción civil y mismo Tribunal de Instancia (Sección Civil) de [NOMBRE DEL SOLICITANTE], el procedimiento de divorcio recayendo sentencia en fecha [FECHA] de [COMPLETAR] de [COMPLETAR].

Se acompañan copias de las referidas sentencias, bajo número de documentos [COMPLETAR] y [COMPLETAR].

D. conoció a Dª [COMPLETAR] en [COMPLETAR], de donde ella es originaria, en el verano del año [COMPLETAR] y durante sus vacaciones estivales, y quedó prendado de sus encantos. Tanto fue así que, tras su regreso mantuvieron la relación telefónica y telemática, decidiendo D. regresar en las siguientes vacaciones de Navidad. Fue en ese segundo viaje cuando decidió pedir matrimonio a Dª [COMPLETAR], quien aceptó de buen grado la propuesta.

Ya de regreso en España, de forma inmediata, D. se puso a tramitar la documentación necesaria de modo que pudiese celebrarse la boda con la mayor celeridad posible.

Una vez celebrado el matrimonio, D. constata que la relación cariñosa que anteriormente le dispensaba Dª [COMPLETAR] se muda en una relación mucho más distante y fría. Observa el esposo con nitidez que la vida matrimonial nada tiene que ver con la vida de noviazgo que habían mantenido.

Al poco tiempo D. descubre una serie de correspondencia mantenida por su esposa con su familia extensa de la que se desprende, sin género de duda, que la única intención de ella al momento de contraer era la obtención de la nacionalidad.

Ante la referida revelación la esposa reconoce a su marido la verdadera motivación matrimonial y le solicita el tiempo suficiente que le permita regularizar su situación legal.

El esposo hoy se decide a formular esta demanda en el convencimiento de que su matrimonio nunca ha existido como tal.

FUNDAMENTOS DE DERECHO

El canon 1.673 del Corpus Iuris Canonici, en relación con el artículo 10 de la Instrucción Pontificia Dignitas Connubii y disposiciones concordantes, según el cual es competente el Tribunal al que se dirige la demanda para poder entender de la presente causa por mantener ambos cónyuges el domicilio en territorio de esta diócesis.

El canon 1.674-1 del CIC, en relación con el artículo 92.1 de la Instrucción Pontificia Dignitas Connubii- que establece la legitimación de cualquiera de los cónyuges para acusar de nulidad su matrimonio.

Deberá tramitarse la presente causa conforme a cuanto ha sido establecido para el Juicio contencioso ordinario, al amparo de lo previsto en los cánones 1.501, siguientes y concordantes, del Corpus Iuris Canonici.

El canón 1.057-1, según el cual "el matrimonio lo produce el consentimiento de las partes legítimamente manifestado entre personas jurídicamente hábiles, consentimiento que ningún poder humano puede suplir", así como que “El consentimiento matrimonial es el acto de la voluntad por el cual el varón y la mujer se entregan y aceptan mutuamente en alianza irrevocable para constituir el matrimonio”

El canon 124 dispone que “para que un acto jurídico sea válido, se requiere que haya sido realizado por una persona capaz, y que en el mismo concurran los elementos que constituyen esencialmente ese acto, así como los requisitos y formalidades impuestos por el derecho para la validez de ese acto”

Según el canon 1.101, el consentimiento interno de la voluntad se presume que está conforme con las palabras o los signos empleados al celebrar el matrimonio, pero si uno de los contrayentes, o ambos, excluye con un acto positivo de la voluntad el matrimonio mismo, o un elemento esencial del matrimonio o una propiedad esencial, contrae inválidamente.

La simulación puede ser parcial cuando se excluye, no el matrimonio en sí, sino uno de sus elementos esenciales, o puede ser total, cuando de lo que se trata es de que no existe ánimo de contraer o cuando ese ánimo está justificado de modo exclusivo en motivaciones finalistas extrañas al mismo matrimonio.

El canon 1.483 del CIC, en relación con los artículos 101 al 113 de la Instrucción Pontificia “Dignitas Connubii”, en lo que se refiere a los requisitos de abogados y procuradores.

En su virtud,

SUPLICO AL TRIBUNAL, que habiendo presentado esta demanda, la admita, teniéndome por comparecido en la representación que ostento, se sirva dar traslado de la misma a la esposa demandada y al Defensor del Vínculo; y en su día, tras recibimiento a prueba en fase de instrucción de la causa y demás trámites legales, dicte sentencia por la que declare la nulidad del matrimonio contraído por el actor con la demandada por el capítulo de Simulación total por exclusión del matrimonio mismo, concurrente en la esposa.

PRIMER OTROSI DIGO: Que reuniendo quien suscribe los requisitos necesarios para defender y representar a la actora, interesa del Tribunal confiera a su favor la oportuna comisión canónica a tal efecto, SUPLICO DEL TRIBUNAL, así se acuerde.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

[COMPLETAR]

========================================================================
