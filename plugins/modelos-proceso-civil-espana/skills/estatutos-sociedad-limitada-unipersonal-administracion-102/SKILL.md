---
name: estatutos-sociedad-limitada-unipersonal-administracion-102
description: "Redacta el escrito «Estatutos de sociedad limitada unipersonal de administración de fincas» (formulario 102 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Estatutos de sociedad limitada unipersonal de administración de fincas

> Formulario 0102 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LUGAR

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

### Formulario 0102 · Estatutos de sociedad limitada unipersonal de administración de fincas

- Año del modelo: 2022
- Revisión 17-11-2026: 1 huecos del original que se habían perdido sin marca, marcados (LUGAR)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Estatutos de la mercantil

CAPÍTULO I. DISPOSICIONES GENERALES.

ARTÍCULO 1.º–La sociedad se denomina «SS, S.L.».

ARTÍCULO 2.º–La sociedad tiene por objeto:

«a) El asesoramiento, la tramitación, la gestión, la administración, la representación, la negociación, la contratación, el estudio y el informe relativo a operaciones inmobiliarias o urbanísticas del cualquier tipo, así como relativos a expedientes de viviendas, de viviendas de protección oficial, expropiaciones, arrendamientos urbanos o de cualquier otro tipo.

b) El asesoramiento legal a Comunidades de Propietarios y a arrendadores de locales de negocio».

Dichas actividades podrán desarrollarse bien directamente, bien a través de la participación en otras sociedades mercantiles.

ARTÍCULO 3.º– Quedan excluidas del objeto social todas aquellas actividades para cuyo ejercicio la Ley exija requisitos especiales que no queden cumplidos por esta Sociedad.

ARTÍCULO 4.º– La duración de la Sociedad es indefinida, y da comienzo a sus operaciones el día del otorgamiento de la escritura fundacional.

ARTÍCULO 5.º– La fecha del cierre del ejercicio social será el día 31 de diciembre de cada año.

ARTÍCULO 6.º– El domicilio de la Sociedad se establece en.

ARTÍCULO 7.º– El capital social es de 4.010 € dividido en 802 participaciones sociales, números 1 al 802, inclusive, de 5 € de valor nominal cada una, acumulables e indivisibles, que no podrán incorporarse a títulos negociables ni denominarse acciones. El capital social está íntegramente suscrito y desembolsado.

Las prestaciones accesorias realizadas por los socios profesionales relativas a la actividad profesional no serán retribuidas.

CAPÍTULO II. RÉGIMEN DE LAS PARTICIPACIONES SOCIALES.

ARTÍCULO 8.º– Las participaciones sociales están sujetas al régimen previsto en la Ley de Sociedades Profesionales, y en lo no previsto, en la Ley de la forma societaria a la que pertenezca la Sociedad.

ARTÍCULO 9.º– La transmisión de participaciones sociales y la constitución del derecho real de prenda deberá constar en documento público. La constitución de otros derechos reales deberá constar en Escritura Pública.

Los derechos frente a la Sociedad se podrán ejercer desde que ésta tenga conocimiento de la transmisión o constitución del gravamen.

La Sociedad llevará un libro registro de socios, que cualquier socio podrá examinar, y del que los titulares podrán obtener certificaciones de los derechos registrados a su nombre.

La transmisión de participaciones sociales, y el aumento o reducción del capital social, se regirá por lo dispuesto en la Ley de la forma societaria adoptada por la sociedad profesional.

A estos efectos, se fija como norma de participación de los socios en los resultados de la sociedad, que éstos se distribuirán en proporción al capital social que en cada momento y para cada período, sea titular cada socio.

ARTÍCULO 10.º– En caso de usufructo de participaciones, la cualidad de socio reside en el nudo propietario, pero el usufructuario tendrá derecho en todo caso a los dividendos acordados por la Sociedad durante el usufructo; y en el caso de prenda corresponderá al propietario el ejercicio de los derechos del socio.

CAPÍTULO III. ÓRGANOS SOCIALES.

ARTÍCULO 11.º– Los órganos sociales son la Junta General y los Administradores, y en lo no previsto en estos Estatutos se regirán por lo dispuesto en la Ley de la forma societaria adoptada por la sociedad profesional.

ARTÍCULO 12.º– JUNTA GENERAL.

Los socios reunidos en Junta General decidirán, por mayoría legal, en los asuntos propios de la competencia de la Junta.

ARTÍCULO 13.º–CONVOCATORIA.

La Junta General será convocada por los Administradores, o Liquidadores, en su caso, mediante comunicación individual y escrita del anuncio a todos los socios al domicilio que conste en el libro registro, por correo certificado, con acuse de recibo.

ARTÍCULO 14.º–ASISTENCIA Y REPRESENTACIÓN.

Todos los socios tienen derecho a asistir a la Junta General por sí mismos.

Los socios profesionales únicamente podrán otorgar su representación a otros socios profesionales para actuar en el seno de los órganos sociales.

El resto de socios podrán otorgar su presentación a otro socio, a su cónyuge, ascendientes, descendientes o persona que ostente poder general conferido en documento público con facultades para administrar todo el patrimonio que el representado tuviere en territorio nacional.

La representación comprenderá la totalidad de las participaciones de que sea titular el socio representado y deberá conferirse por escrito. Si no constare en documento público, deberá ser especial para cada Junta.

ARTÍCULO 15.º–ADMINISTRADORES.

La Junta General confiará la Administración de la Sociedad a un Administrador único, dos mancomunados, varios solidarios, con un máximo de cinco, o a un Consejo de Administración.

Habrán de ser socios profesionales las tres cuartas partes de los miembros de los órganos de administración, en su caso, de las sociedades profesionales. Si el órgano de administración fuere unipersonal, o si existieran consejeros delegados, dichas funciones habrán de ser desempeñadas necesariamente por un socio profesional.

ARTÍCULO 16.º– Los Administradores ejercerán su cargo indefinidamente, pudiendo ser separados de su cargo por la Junta General aún cuando la separación no conste en el Orden del Día.

ARTÍCULO 17.º– La representación de la Sociedad en juicio y fuera de él corresponde a los Administradores, y se extenderá a todos los actos comprendidos en el objeto social.

ARTÍCULO 18.º – El cargo de Administrador es gratuito.

ARTÍCULO 19.º–CONSEJO DE ADMINISTRACIÓN.

El Consejo de Administración, de haberlo, estará integrado por un mínimo de tres y un máximo de siete miembros.

Las funciones de los Consejeros Delegados deberán ser desempeñadas necesariamente por un socio profesional.

El Consejo quedará válidamente constituido cuando concurran a la reunión, presentes o representados por otro Consejero, la mitad más uno de sus miembros. La representación se conferirá mediante carta dirigida al Presidente.

Los acuerdos se adoptarán por mayoría absoluta de los asistentes a la reunión, que deberá ser convocada por el Presidente o Vicepresidente, en su caso. La votación por escrito y sin sesión será válida si ningún Consejero se opone a ello. En caso de empate, decidirá el voto personal de quien fuera Presidente.

El Consejo se reunirá siempre que lo acuerde su Presidente, bien a iniciativa propia o cuando lo soliciten dos de sus miembros. La convocatoria se cursará mediante carta o telegrama dirigidos a todos y cada uno de sus componentes, con veinticuatro horas de antelación. Designará a su Presidente y a un Secretario.

CAPÍTULO IV. RÉGIMEN DE RESPONSABILIDAD.

ARTÍCULO 20.º– La concurrencia de causas de incompatibilidad o inhabilitación en cualquiera de los socios, afectará por extensión a la sociedad y a los restantes socios profesionales.

ARTÍCULO 21.º–RESPONSABILIDAD PATRIMONIAL.

De las deudas sociales con todo su patrimonio, según las reglas de la forma social adoptada para determinar la responsabilidad de los socios.

CAPÍTULO V. MODIFICACIÓN DE LA CONDICIÓN DE SOCIOS. SEPARACIÓN Y EXCLUSIÓN.

ARTÍCULO 25.º– El cambio de socios deberá constar en escritura pública.

CAPÍTULO VI. DISOLUCIÓN Y LIQUIDACIÓN.

ARTÍCULO 26.º– La Sociedad se disolverá y liquidará de acuerdo con el régimen establecido en la Ley de la forma societaria adoptada.

ARTÍCULO 27.º– Los Administradores al tiempo de la disolución quedarán convertidos en Liquidadores, salvo que la Junta General hubiese designado otros al acordar la disolución.

Los Liquidadores ejercerán su cargo por tiempo indefinido. Transcurridos tres años desde la apertura de la liquidación sin que se haya sometido a la aprobación de la Junta General el balance final de la liquidación, cualquier socio o persona con interés legítimo podrá solicitar del Juez de Primera Instancia del domicilio social la separaciónde los Liquidadores en la forma prevista por la Ley.

ARTÍCULO 28.º– La cuota de liquidación correspondiente a cada socio separado o excluido, así como en los casos de trasmisión mortis causa y forzosa cuando proceda, vendrá determinada por el valor nominal de su participación más el 25% de las reservas legales y voluntarias de la sociedad.

En los restantes casos vendrá determinada por su participación en el capital social.

ARTÍCULO VII. SOCIEDAD UNIPERSONAL.

ARTÍCULO 29.º– En caso de sociedad unipersonal se estará a lo dispuesto en la Ley de Sociedades Profesionales, y supletoriamente en la Ley correspondiente al tipo social adoptado por la Sociedad Profesional.

Transcurridos seis meses desde que un único socio sea propietario de todas las participaciones sociales, sin que esta circunstancia se hubiese inscrito en el Registro Mercantil, el socio único responderá personal, ilimitada y solidariamente de las deudas sociales contraídas durante el periodo de unipersonalidad. Inscrita la unipersonalidad, el socio único no responderá de las deudas contraídas con posterioridad.

CAPÍTULO VIII. ARBITRAJE.

ARTÍCULO 30.º– Las controversias surgidas entre los socios, entre socios y administrares y entre cualesquiera de éstos y la sociedad, podrán resolverse a través del procedimiento de arbitraje, siempre que tal procedimiento quede establecido en el contrato social.

En [LUGAR] a
