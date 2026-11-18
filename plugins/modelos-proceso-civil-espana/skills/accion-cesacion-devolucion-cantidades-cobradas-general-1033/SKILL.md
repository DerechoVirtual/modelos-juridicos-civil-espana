---
name: accion-cesacion-devolucion-cantidades-cobradas-general-1033
description: "Redacta el escrito «Acción de cesación con devolución de cantidades cobradas (general)» (formulario 1033 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acción de cesación con devolución de cantidades cobradas (general)

> Formulario 1033 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] ACTO O RESOLUCIÓN (2 veces)
- [ ] NIF
- [ ] IMPORTE (7 veces)
- [ ] NÚMERO (15 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…entación de la Asociación Profesional de»; «…y sede o delegación en»; «…y sede o delegación en [COMPLETAR] de»; «…La demandada se dedica a la actividad de»; «…(certificación del Registro Mercantil de»; «…t. figura su objeto social o contrato de»; «… demandado la prestación de servicios de»; «…entre las siguientes fechas»; «…rechos entre las partes contratantes son»; «… de lo previsto se requirió a la Empresa»; «…, [IMPORTE] euros por»; «…, [IMPORTE] euros por»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 21 y 22.4 de la LOPJ
- art. 249.5 de la LEC
- art. 423.3 de la LEC
- art. 253 de la LEC
- art. 11.2 de la LEC
- arts. 23 y 31 de la LEC
- art. 1091 del CC
- art. 1258 del CC
- art. 1256 del CC
- art. 1303 del CC
- art. 394 de la LEC
- Ley Orgánica 1/2025
- Ley 7/1998
- Ley 26/1984

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

### Formulario 1033 · Acción de cesación con devolución de cantidades cobradas (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 2 puntualizaciones normativas añadidas en el texto; 50 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de la Asociación Profesional de [COMPLETAR], según acredito mediante poder notarial que acompaño otorgado por su presidente D./Dña. [NOMBRE Y APELLIDOS]

[NOMBRE Y APELLIDOS], que a su vez actúa en nombre de la misma, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo demanda contra [ACTO O RESOLUCIÓN], con DNI/NIF n.º [NIF] y sede o delegación en [COMPLETAR] de [COMPLETAR] (ciudad) en ejercicio de acción colectiva de cesación de la utilización de las condiciones generales de contratación que en el suplico se especificarán y, acumulada a ésta, acción de devolución de la cantidad total de [IMPORTE] euros a las personas integrantes de esta asociación en la cuantía que a cada una corresponde especificada también en el suplico. Esta demanda se tramitará por el cauce del juicio ordinario conforme a los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

La demandada se dedica a la actividad de [COMPLETAR] según acredito con documento n.º [NÚMERO] (certificación del Registro Mercantil de [COMPLETAR] de la constitución de la Sociedad y la aprobación de sus Estatutos en cuyo art. figura su objeto social o contrato de [COMPLETAR]).

Los integrantes de la Asociación demandante contrataron de forma individual con el demandado la prestación de servicios de [COMPLETAR] entre las siguientes fechas [COMPLETAR] Adjunto copias de todos los contratos como docs. n.º [NÚMERO] a

Como se puede comprobar dichos contratos contenían condiciones de contratación impuestas de manera unilateral en lo que sin duda son contratos de adhesión.

Todo intento de negociación para modificar su contenido resultó infructuoso, tal como acreditamos con carta dirigida por este colectivo a dicha entidad que acompañamos como doc. n.º [NÚMERO], pero la necesidad de los profesionales demandantes de la productos y servicios que ofrece el demandado determinó la necesidad de contratar con él, a pesar de las reticencias expresadas.

Las condiciones generales que esta parte consideraba abusivas, tal como se manifestaba en dicho escrito eran las siguientes:

Los motivos por los que se considera que esas cláusulas producen un grave desequilibrio de las obligaciones y derechos entre las partes contratantes son [COMPLETAR]

Antes de llegar a esta vía judicial y un vez comprobado que los efectos de la aplicación de esas cláusulas eran aún más oneroso de lo previsto se requirió a la Empresa [COMPLETAR] para que las modificara sin haber obtenido resultado positivo.

Acompaño como doc. n.º [NÚMERO], el requerimiento efectuado y como doc. n.º [NÚMERO], la contestación de la entidad demandada.

La aplicación como regla general de la estipulación n.º [NÚMERO], cuando aparentemente se configuraba como una excepción, ha determinado en la práctica que el demandado ha cobrado unas tarifas que deberían incluirse en las generales de mantenimiento. En concreto se determinan las cantidades que se han abonado por los integrantes de la Asociación como consecuencia de la aplicación de las condiciones generales que se consideran nulas:

D. [NOMBRE Y APELLIDOS], [IMPORTE] euros por [COMPLETAR] (Doc. n.º [NÚMERO]).

D. [NOMBRE Y APELLIDOS], [IMPORTE] euros por [COMPLETAR] (Doc. n.º [NÚMERO]).

D. [NOMBRE Y APELLIDOS], [IMPORTE] euros por [COMPLETAR] (Doc. n.º [NÚMERO]).

D. [NOMBRE Y APELLIDOS], [IMPORTE] euros por [COMPLETAR] (Doc. n.º [NÚMERO]).

Adjuntamos informe pericial con el n.º [NÚMERO] emitido por D./Dña. [NOMBRE Y APELLIDOS], titulado en [COMPLETAR] sobre la valoración de la aplicación de dobles tarifas a actuaciones únicas.

Las cantidades arriba citadas deberán ser reintegradas en su totalidad a este grupo de afectados que constituyen la Asociación demandante.

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21 y 22.4 de la LOPJ y 36 de la LEC en relación con el R.D. Leg. 1/2007, de 16 de noviembre, en materia de protección de los intereses de los consumidores y usuarios, atribuyen al orden civil el conocimiento de esta materia.

Los arts. 85.1º de la LOPJ y 45 de la LEC determinan la competencia de las secciones civiles de los Tribunales de Instancia, salvo que la ley expresamente designe otro Tribunal para conocer del pleito.

Finalmente el art. 52.1.16.º de la LEC dice que en los procesos en los que se ejercite la acción de cesación en defensa de los intereses tanto colectivos como difusos de los consumidores y usuarios, será competente el Tribunal del lugar donde el demandado tenga un establecimiento y, a falta de éste, el de su domicilio y si carece de domicilio en territorio español, el del lugar del domicilio del actor. En sentido similar se pronuncia el n.º 14 del mismo precepto.

Tramitación y cuantía de la demanda

El art. 249.5 de la LEC establece que se seguirá el cauce del juicio ordinario en las demandas en que se ejerciten acciones relativas a condiciones generales de la contratación, salvo la acción de cesación que sigue el cauce del juicio verbal. En este caso al acumularse dos acciones una de cesación y otra de devolución de cantidades sobre el mismo objeto de condiciones generales de la contratación cuya nulidad se interesa, entendemos que se seguirá el CAUCE del juicio ordinario, sin perjuicio de la aplicación del art. 423.3 de la LEC si finalmente se considerara por el Juzgador que es otro el procedimiento adecuado.

Según prescribe el art. 253 de la LEC deberá determinarse la CUANTÍA que fijamos en [IMPORTE] euros que son las cantidades que deben reintegrarse a los afectados.

Legitimación

Activa: El art. 6.1, apdos. 3, 7 y 8 de la LEC reconoce capacidad para ser parte a las personas jurídicas, a los grupos de consumidores y usuarios y a las entidades habilitadas conforme a la normativa europea para el ejercicio de esta acción y el art. 11.2 de la LEC legitima a los grupos de afectados, a las asociaciones de consumidores y usuarios y a las entidades legalmente constituidas que tengan por objeto la defensa y protección de éstos cuando los afectados sean un grupo con componentes determinados o fácilmente determinables. El art. 16.1 de la Ley sobre Condiciones Generales de la Contratación legitima a las asociaciones o corporaciones de empresarios, profesionales y agricultores que estatutariamente tengan encomendada la defensa de los intereses de sus miembros.

Pasiva: El art. 17.1 y 4 de la Ley de Condiciones Generales de la Contratación establece que procede la acción de cesación contra cualquier profesional que utilice condiciones generales que se reputen nulas y que también pueden dirigirse conjuntamente contra varios profesionales del mismo sector económico o contra sus asociaciones que utilicen o recomienden la utilización de condiciones generales idénticas que se consideren nulas.

Postulación

Será preceptiva la intervención de Procurador y Abogado en aplicación de los arts. 23 y 31 de la LEC.

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con el requisito de procedibilidad exigido por la DA 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

1.º El art. 1091 del CC dice que las obligaciones que nacen de los contratos tienen fuerza de ley entre las partes y que deben cumplirse a tenor de los mismos y el art. 1255 del mismo texto prohíbe que los pactos, cláusulas o condiciones de los contratos sean contrarios a la ley, la moral o el orden público.

En este caso se considera que las condiciones generales recogidas en los apartados n.º [NÚMERO] del contrato modelo que adjuntamos como documento n.º [NÚMERO] son contrarias a la normativa sobre consumo y sobre condiciones generales de contratación.

2.º El art. 12 de la Ley sobre Condiciones Generales de Contratación reconoce el derecho a interponer acción de cesación dirigida a obtener una sentencia que condene al demandado a eliminar de sus condiciones generales las que reputen nulas y a abstenerse de utilizarlas en lo sucesivo, determinando, o aclarando cuando sea necesario, el contenido del contrato que ha de considerarse válido y eficaz. Esta es la acción que se interpone en la presente demanda.

3.º El art. 8 de la citada Ley 7/1998, de 13 de abril, considera nulas de pleno derecho las condiciones generales que contradigan en perjuicio del adherente lo dispuesto en esta ley o en cualquier otra norma imperativa o prohibitiva. En particular son nulas las condiciones generales abusivas cuando el contrato se haya celebrado con un consumidor, entendiéndose por tales las definidas en los arts. 10 bis y D.A. primera de la Ley 26/1984, de 19 de julio [NOTA DE REVISIÓN: La Ley 26/1984 está derogada (DD única.2 RDLeg 1/2007); el art. 8.2 LCGC conserva esa remisión literal, pero las cláusulas abusivas se regulan hoy en los arts. 82 a 91 TRLGDCU. Fuente: Ley 7/1998, art. 8.2, BOE-A-1998-8789; TRLGDCU DD única y art. 82, BOE-A-2007-20555.].

4.º El art. 49.1.i) del R.D. Leg. 1/2007, de 16 de noviembre, sanciona la introducción de cláusulas abusivas en los contratos, que se definen en el art. 82 de la misma norma.

El art. 83 de esta regulación declara su nulidad, exigiendo la integración del contrato conforme a lo regulado en su art. 1258 del CC.

5.º El art. 1256 del CC afirma que la validez y el cumplimiento de los contratos no puede dejarse al arbitrio de uno de los contratantes como en el caso presente porque

6.º El art. 1303 del CC considera que cuando se declara la nulidad de una obligación los contratantes deben restituirse recíprocamente las cosas que hubiesen sido materia del contrato salvo, art. 1306.2 del mismo texto, que la culpa sea de un solo contratante, pues en este supuesto el otro podrá reclamar lo que hubiera dado, sin obligación de cumplir lo que hubiera ofrecido.

Se ha acreditado que el demandado aplicaba una doble tarifa por la prestación de un único servicio en atención a lo establecido en las cláusulas del contrato que se consideran nulas. Así deberá procederse a la devolución de lo indebidamente cobrado.

Costas

En aplicación del art. 394 de la LEC deberán imponerse a la parte demandada. Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos e informe que acompaño y tenga por formulada demanda contra [ACTO O RESOLUCIÓN], la admita a trámite y de traslado a la parte contraria a los efectos oportunos convocando posteriormente a las partes a la audiencia previa a fin de que en su día dicte sentencia:

1.º Por la que se declare la nulidad de las cláusulas n.º [NÚMERO] contenidas en los contrato modelo relativos a [DESCRIBIR] y presentados como doc. n.º [NÚMERO] en la presente demanda, cuyo contenido es el siguiente [COMPLETAR];

2.º Que en consecuencia se declare la obligación de eliminar en sus contratos dichas condiciones generales de la contratación;

3.º Que igualmente se declare la obligación de abstenerse de utilizarlas en lo sucesivo en los contratos de [COMPLETAR];

4.º Que se declare la validez del resto del contenido del contrato;

5.º Que se condene al demandado a abonar la cantidad de [IMPORTE] euros como deuda global al conjunto de los integrantes de la Asociación derivada de la aplicación indebida de las cláusulas objeto de este juicio;

6.º Que se impongan las costas a la parte demandada.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
