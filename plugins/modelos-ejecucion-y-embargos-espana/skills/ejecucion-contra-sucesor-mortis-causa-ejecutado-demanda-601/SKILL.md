---
name: ejecucion-contra-sucesor-mortis-causa-ejecutado-demanda-601
description: "Redacta el escrito «Ejecución contra el sucesor mortis causa del ejecutado: demanda» (formulario 601 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución contra el sucesor mortis causa del ejecutado: demanda

> Formulario 0601 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] NOMBRE Y APELLIDOS (16 veces)
- [ ] NÚMERO (11 veces)
- [ ] FECHA (10 veces)
- [ ] CALLE
- [ ] Nº
- [ ] IMPORTE (3 veces)
- [ ] DNI/NIE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 31 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de fecha [FECHA] de»; «…de fecha [FECHA] de [COMPLETAR] de»; «…n.º [NÚMERO] de»; «…de»; «…de [COMPLETAR] de»; «…ediante la que se condena al demandado a»; «…de fecha [FECHA] de»; «…de fecha [FECHA] de [COMPLETAR] de»; «…icado de últimas voluntades, resultó que»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] ante el notario de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 540 de la LEC
- art. 548 de la LEC
- art. 550 de la LEC
- art. 549 de la LEC
- art. 592 LEC
- art. 549 LEC
- art. 576 de la LEC
- art. 152 LEC

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

### Formulario 0601 · Ejecución contra el sucesor mortis causa del ejecutado: demanda

- Año del modelo: 2016
- Revisión 17-11-2026: 74 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (DNI/NIE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, interviniendo en nombre de d/dña., en virtud de la representación que tengo acreditada en los autos referenciados seguidos a instancia de mi poderdante contra d/dña [NOMBRE Y APELLIDOS], ante el Tribunal comparezco bajo la dirección del Letrado/a d./dña [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que por medio del presente escrito formulo demanda ejecutiva mediante la que solicito que se despache la EJECUCIÓN de la sentencia n.º [NÚMERO] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en el presente proceso frente a d/dña [NOMBRE Y APELLIDOS], domiciliado en calle [CALLE] n.º [NÚMERO] de [COMPLETAR], cuyas demás circunstancias personales constan en los indicados autos, con objeto de que, previa la tramitación oportuna, se dicte por el Tribunal auto conteniendo orden general de ejecución y de despacho de ella y por el Letrado de la Administración de Justicia decreto para su efectividad en los términos interesados en el suplico de esta demanda ejecutiva que baso en los siguientes:

HECHOS

Con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se dictó, en la tramitación de este proceso, la sentencia n.º [NÚMERO] mediante la que se condena al demandado a [COMPLETAR] (Opciones):

1. No habiendo sido objeto de recurso, la sentencia referenciada ha resultado firme.

2. Habiéndose recurrido la sentencia, la Audiencia Provincial mediante sentencia n.º [NÚMERO] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en el recurso de apelación n.º [NÚMERO] ha confirmado el fallo dictado en la instancia.

No cumplió voluntariamente el demandado la obligación derivada del pronunciamiento de la sentencia, por lo que mediante el presente escrito formalizo esta demanda ejecutiva para impulsar su ejecución.

Han transcurrido más de veinte días hábiles desde la firmeza de la sentencia.

El ejecutado falleció el día [FECHA] Solicitado certificado de últimas voluntades, resultó que [COMPLETAR] (Opciones):

1. Otorgó testamento de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] ante el notario de [COMPLETAR] don/doña [NOMBRE Y APELLIDOS] en el que eran declarados sus herederos los siguientes [COMPLETAR] Con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] los mentados herederos otorgaron escritura de aceptación y partición de herencia ante el notario de [COMPLETAR] don/doña [NOMBRE Y APELLIDOS] autorizada con el número [NÚMERO] de su protocolo.

2. Falleció sin haber otorgado testamento. Instado procedimiento de declaración de herederos abintestato ante el Tribunal de Instancia núm. (o en su caso acta notarial de declaración de herederos abintestato autorizada por el/la notario d/doña [COMPLETAR]) fueron declarados sus herederos los siguientes [COMPLETAR] Con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] los mentados herederos otorgaron escritura de aceptación y partición de herencia ante el notario de [COMPLETAR] don/doña [NOMBRE Y APELLIDOS] autorizada con el número [NÚMERO] de su protocolo.

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

- Es competente para conocer de esta ejecución el Tribunal a que me dirijo por ser quien dictó la resolución cuya ejecución se pide (Arts. 61 y 545 de la LEC).

(En su caso, si se ejecutan resoluciones del Letrado de la Administración de Justicia), es competente el Tribunal que conoció del asunto en primera instancia o que homologó o aprobó la transacción o acuerdo.

Legitimación

- Art. 549 de la LEC: La ejecución se despachará “a petición de parte”.

?- A los efectos del art. 540 de la LEC aporto, como documentos fehacientes para acreditar quiénes son los sucesores mortis causa del fallecido ejecutado: certificado de defunción del mismo, certificado de últimas voluntades, testamento de fecha [FECHA] otorgado ante el/la notario/a d/dña [NOMBRE Y APELLIDOS] (o en su caso, testimonio del Auto de declaración de herederos abintestato tramitado ante el Tribunal de Instancia núm. [Nº], o acta notarial de declaración de herederos abintestato autorizada por el/la notario/a d/dña [NOMBRE Y APELLIDOS]) y escritura de aceptación y partición de herencia otorgada ante el/la notario/a de [COMPLETAR] don/doña [NOMBRE Y APELLIDOS] y autorizada con el número [NÚMERO] de su protocolo.

Trámite y requisitos procesales

- Consta acreditada la representación del procurador firmante, por lo que no es preciso aportar nuevamente su acreditación (Art. 550.1.2º de la LEC).

- A los efectos previstos en el art. 549.1.1º de la LEC se reseña que el título ejecutivo en que se funda esta demanda ejecutiva es [COMPLETAR] (el decreto del Letrado de la Administración de Justicia o la sentencia) n.º [NÚMERO] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en los autos de juicio [COMPLETAR] n.º [NÚMERO] de este Tribunal.

- A los efectos previstos en el art. 549.1.2º de la LEC se señala que la tutela jurídica perseguida es el cumplimiento del fallo de la sentencia cuya ejecución se pide, mediante la que se condena a D./Dña. [NOMBRE Y APELLIDOS] a pagar a mi mandante la suma de [IMPORTE] euros.

- Art. 517.2.1º LEC: La sentencia firme es título que lleva aparejada ejecución.

- Art. 580 de la LEC: No procede requerimiento de pago al ejecutado para embargar bienes cuando el título sea resolución judicial que obliga a entregar una cantidad determinada de dinero.

- Art. 548 de la LEC: No se despachará ejecución dentro de los veinte días posteriores a aquel en que la resolución de condena sea firme. La demanda se presenta transcurrido el plazo señalado en el art. 548 de la LEC.

- El art. 550 de la LEC exime de la obligación de presentar el título cuando la ejecución se funde en resolución que obre en los autos.

- Arts. 551 y ss. de la LEC sobre trámite para el despacho de la ejecución y oposición a la misma.

- A los restantes efectos previstos en el art. 549 de la LEC establezco los siguientes presupuestos:

A) Designo como bienes del ejecutado susceptibles de embargo los siguientes: (detallar según el orden legal —art. 592 LEC—). Acompaño reseñados como documentos núms. notas registrales acreditativas de la inscripción de inmuebles de la titularidad del ejecutado.

B) Los bienes detallados en el ordinal precedente no parecen suficientes para cubrir las sumas reclamadas, por lo que, para la localización de bienes del ejecutado con los que hacer frente a su obligación de pago, resultan necesarias las siguientes medidas de investigación judicial:

1.º Que a través del punto neutro de información judicial se proceda a emitir relación de bienes, derechos y cuentas bancarias de la que es titular D./Dña. [NOMBRE Y APELLIDOS] con DNI n.º [DNI/NIE]

2.º Otras:

Fondo

- Art. 517.1º de la LEC: reconoce naturaleza ejecutiva a la sentencia firme.

- Sólo se despachará ejecución a petición de parte y en forma de demanda con los requisitos que se desarrollan en el art. 549 LEC.

- Mora procesal: art. 576 de la LEC. Desde que se dictó sentencia, la cantidad devengará un interés anual igual al del interés legal del dinero incrementado en dos puntos. La Ley de Presupuestos Generales del Estado, fija el interés legal del dinero para este año en el [COMPLETAR] %.

Costas

- Arts. 539, 561.1.1ª y 583 de la LEC: Deberán imponerse al demandado ejecutado.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, documentos y copias de todo ello, se sirva admitirlo, teniendo por formulada demanda ejecutiva frente a d/dña. (sucesor/es de d/dña [NOMBRE Y APELLIDOS]), en solicitud de despacho de ejecución de la sentencia n.º [NÚMERO] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en estos autos, la admita a trámite y acuerde lo siguiente:

1.º Que se dicte auto de orden general de ejecución despachando la misma en el que se determine que se despacha ejecución a favor de d/dña [NOMBRE Y APELLIDOS] frente a d/dña (sucesor/es de d/dña [NOMBRE Y APELLIDOS]) por el principal de [IMPORTE] euros y otros [IMPORTE] euros que por el momento y sin perjuicio de ulterior liquidación se consideran bastantes para intereses, gastos y costas. (En su caso, añadir las precisiones necesarias respecto de las partes, o del contenido de la ejecución, de los responsables personales de la deuda o personas a las que ha de extenderse la ejecución).

2.º Que en el mismo día o en el siguiente hábil por el Letrado de la Administración de Justicia:

• Decrete el embargo de los siguientes bienes concretos del demandado: (o que se adopten las siguientes medidas ejecutivas [COMPLETAR]).

• Practique las siguientes medidas de averiguación de bienes: [COMPLETAR];

y se dé a los autos la tramitación procesal pertinente, para que se dicte en su día, si mediare oposición y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante, acordando, en todo caso, hacer trance y remate de los bienes embargados y pagar con el importe obtenido al demandante el principal reclamado, intereses, gastos y las costas.

Con expresa imposición de costas, en todo caso, al/los ejecutado/s d/dña (sucesor/es de d/dña [NOMBRE Y APELLIDOS]).

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(En su caso, si se pretende que los actos de comunicación con la otra parte se lleven a cabo por el Procurador) OTROSÍ DIGO: Que según permite el art. 152 LEC, con el presente escrito intereso que se autorice a este Procurador a realizar los actos de comunicación con la parte demandada.

NUEVAMENTE SUPLICO: Que se acuerde conforme se interesa en el presente otrosí, por ser justicia que pido en mismo lugar y fecha.

========================================================================
