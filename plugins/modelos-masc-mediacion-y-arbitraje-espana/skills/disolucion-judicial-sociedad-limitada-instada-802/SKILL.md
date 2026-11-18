---
name: disolucion-judicial-sociedad-limitada-instada-802
description: "Redacta el escrito «Disolución judicial de sociedad limitada instada por los administradores» (formulario 802 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Disolución judicial de sociedad limitada instada por los administradores

> Formulario 0802 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NIF
- [ ] CALLE
- [ ] NÚMERO (4 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…único de la mercantil SL, constituida el»; «…, Notario de»; «…de los de»; «…de los de [COMPLETAR] el»; «… los de [COMPLETAR] el [COMPLETAR], Tomo»; «…el [COMPLETAR], Tomo [COMPLETAR], Folio»; «…omo [COMPLETAR], Folio [COMPLETAR], Hoja»; «… representado apreció la concurrencia de»; «…, por lo que procedió a convocar»; «…convocatoria con los recortes del diario»; «…y»; «…los que se acompañan al presente escrito»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 126.1 LJV
- arts. 13 a 22 LJV
- art. 126.2 LJV
- art. 126.3 LJV

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

### Formulario 0802 · Disolución judicial de sociedad limitada instada por los administradores

- Año del modelo: 2015
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de demanda de juicio ordinario interpuesta por administradores en la que se solicita la disolución judicial de una Sociedad de Responsabilidad Limitada, tras no haberse procedido a celebrar la Junta General en un plazo determinado a pesar de haber sido requerida notarialmente por los demandantes al considerar que la sociedad está incursa en alguna de las causas de disolución establecidas legalmente.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de D./Dña. [NOMBRE Y APELLIDOS], en su calidad de administrador único de la mercantil SL, según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y al amparo de lo dispuesto en los arts. 125 y siguientes de la Ley de la Jurisdicción Voluntaria (LJV), promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA SOBRE DISOLUCIÓN JUDICIAL de la mercantil SL, con NIF [NIF] y domicilio en

Fundamento mi pretensión en los siguientes:

HECHOS

PRIMERO.- Mi mandante es administrador único de la mercantil SL, constituida el [COMPLETAR], según consta en la escritura autorizada el por D./Dña. [NOMBRE Y APELLIDOS], Notario de [COMPLETAR], su domicilio social se halla sito en la calle [CALLE] de esta localidad, y fue inscrita en el Registro Mercantil n.º [NÚMERO] de los de [COMPLETAR] el [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], Hoja [COMPLETAR], con NIF

Acredito estos extremos con el documento n.º [NÚMERO] de los que se acompañan a este escrito, y consistente en copia simple de la escritura de nombramiento y aceptación del cargo, así como con el documento n.º [NÚMERO], que recoge la certificación del Registro Mercantil donde constan los datos mencionados.

SEGUNDO.- Que el pasado día [FECHA], mi representado apreció la concurrencia de [COMPLETAR], por lo que procedió a convocar [COMPLETAR] debidamente junta de socios de SL, en cuyo punto n.º [NÚMERO] de su Orden del Día consta el extremo citado.

Acredito la legalidad de la convocatoria con los recortes del diario [COMPLETAR] y del BORM que acompaño como documentos número [Nº DE DOCUMENTO] y [COMPLETAR] de los que se acompañan al presente escrito [COMPLETAR].

TERCERO.- Que así pues, el [COMPLETAR], SL celebró junta general de socios, siendo el acuerdo social contrario a la disolución, no pudiendo lograrse el acuerdo por no alcanzar la mayoría prevista al efecto [COMPLETAR].

Así se indica en el acta de la junta debidamente firmada por el Secretario de la misma y en la que consta el visto bueno de su Presidente, mi mandante, que adjunto como documento n.º [Nº DE DOCUMENTO]

CUARTO.- Que mi mandante, pese al acuerdo social descrito en el ordinal precedente, considera que la sociedad efectivamente se halla incursa en la siguiente causa que legitima su disolución [COMPLETAR] puesto que [COMPLETAR], por lo que solicita la disolución judicial de la reiterada sociedad.

Acredito los hechos relativos a la causa de disolución que se cita con los documentos [COMPLETAR]

A los presentes hechos les son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Es competente la Sección de lo Mercantil del Tribunal de Instancia del domicilio social de la sociedad, al que se dirige el presente escrito, por aplicación de lo dispuesto en el art. 126.1 LJV en relación con el art. 366.1 LSC.

II.- TRAMITACIÓN.

El procedimiento a seguir es el de la jurisdicción voluntaria, con aplicación de las prescripciones de los arts. 13 a 22 LJV, en lo que no se opongan a las normas específicas sobre la materia de los arts. 127 y 128 de la misma Ley.

III.- LEGITIMACIÓN.

El art. 126.2 LJV en relación con el art. 366.2 LSC atribuyen legitimación a mi representado para instar la disolución judicial de la sociedad.

IV.- CAUSA DE DISOLUCIÓN.

En virtud de lo previsto en el art. 363 LSC la [COMPLETAR] constituye causa legítima de disolución social.

V.- POSTULACIÓN Y DEFENSA.

Conforme a lo previsto en el art. 126.3 LJV, en la tramitación del expediente es preceptiva la intervención de Abogado y Procurador.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovido EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA SOBRE DISOLUCIÓN JUDICIAL de la mercantil SL, previos los trámites legales, se dicte auto que declare disuelta la citada mercantil, acordando el cese de D./Dña. [NOMBRE Y APELLIDOS] como administrador social, quedando convertido en liquidador de la misma, librando igualmente en su día el oportuno testimonio al Registro Mercantil de [COMPLETAR] para constancia tabular de la resolución.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
