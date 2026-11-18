---
name: partija-conjunta-extratestamentaria-documento-privado-549
description: "Redacta el escrito «Partija conjunta extratestamentaria en documento privado» (formulario 549 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Partija conjunta extratestamentaria en documento privado

> Formulario 0549 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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

- [ ] NÚMERO (5 veces)
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] Otros 66 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Doña»; «…, mayor de edad, casada (), vecina de»; «…,; con D.N.I. número [NÚMERO]. Don»; «…mayor de edad, casado (), vecino de»; «…, tomo»; «…, tomo [COMPLETAR], libro»; «…, libro [COMPLETAR], folio»; «…ento abierto mancomunado ante el Notario»; «…el día [FECHA] en»; «…lecimiento de cualquiera de ambos; - Don»; «…ha efectuado un legado a favor de»; «…; - Doña»; …

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

### Formulario 0549 · Partija conjunta extratestamentaria en documento privado

- Año del modelo: 2016
- Revisión 17-11-2026: 75 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Doña [COMPLETAR], mayor de edad, casada (), vecina de [COMPLETAR],; con D.N.I. número [NÚMERO].

Don [COMPLETAR] mayor de edad, casado (), vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Intervienen, en su propio nombre y derecho y se reconocen capacidad suficiente para otorgar esta PARTIJA CONJUNTA DE HERENCIA, y, al efecto,

Exponen

I. Que han contraído matrimonio () el día [FECHA] y que está inscrito en el Registro Civil de [LOCALIDAD], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], ().

II. Que ambos han otorgado un testamento abierto mancomunado ante el Notario [COMPLETAR] el día [FECHA] en [COMPLETAR].

III. Que en el referido instrumento han incluido las siguientes disposiciones:

- han instituido por iguales partes a sus tres hijos, estableciendo la sustitución vulgar a favor de sus respectivos descendientes;

- han efectuado el nombramiento de contador-partidor condicionado al evento de la revocación unilateral de la partija por el supérstite tras el fallecimiento de cualquiera de ambos;

- Don [COMPLETAR] ha efectuado un legado a favor de [COMPLETAR];

- Doña [COMPLETAR] ha instituido otro legado a favor de [COMPLETAR];

- los dos referidos legados tienen carácter correspectivo.

IV. Que el inventario de los bienes de ambos es el siguiente; todos ellos de naturaleza ganancial:

1. Rústica: finca número [NÚMERO] del Plano General de Concentración Parcelaria de [COMPLETAR], terreno dedicado a labradío y monte, al sitio de [COMPLETAR], de una superficie de [COMPLETAR] áreas y [COMPLETAR] centiáreas.

Linda: Norte, terreno excluido; Sur, finca [COMPLETAR]; Este, camino y finca [COMPLETAR]; y Oeste, terreno excluido y [COMPLETAR].

Inscripción: Registro de la Propiedad de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Referencia catastral: Tiene asignada referencia catastral número [NÚMERO], según resulta de la fotocopia que se adjunta a este documento.

Valor: [IMPORTE] euros.

2. Sepulturas números [COMPLETAR] y [COMPLETAR] en el Cementerio de [COMPLETAR], municipio de [COMPLETAR].

Valor: [IMPORTE] euros.

3. Urbana: vivienda número [NÚMERO], con una extensión superficial de [COMPLETAR] metros cuadrados, que consta de planta baja, con una edificación de planta rectangular, y que ocupa un solar de [COMPLETAR] metros cuadrados, con una construcción o trastero de [COMPLETAR] metros cuadrados y un terreno anejo dedicado a huerta.

Linda: Norte, con herederos de [COMPLETAR]; Sur, con parcela denominada [COMPLETAR]; Este, con camino [COMPLETAR]; y Oeste, con vivienda unifamiliar [COMPLETAR] y parcela de terreno en que se asienta.

Referencia catastral: Tiene asignada la referencia catastral [COMPLETAR], como resulta de la certificación catastral descriptiva y gráfica que se incorpora a este documento.

Valor: [IMPORTE] euros

4. El saldo [COMPLETAR] en la cuenta corriente [COMPLETAR] en la entidad bancaria [COMPLETAR].

5. El saldo [COMPLETAR] en la cuenta corriente [COMPLETAR] en la entidad bancaria [COMPLETAR].

6. El saldo [COMPLETAR] en la cuenta corriente [COMPLETAR] en la entidad bancaria [COMPLETAR].

V. Y esto expuesto,

Otorgan

Primero. Distribución conjunta de la herencia. Don [COMPLETAR] y Doña [COMPLETAR], acuerdan distribuir los bienes que comprenden las herencias de ambos del siguiente modo.

a) a Don [COMPLETAR] en pago de sus derechos en las herencias de ambos, el bien inventariado en el número 1.

b) a Don [COMPLETAR] en pago de sus derechos en las herencias de ambos, los bienes inventariados en los números 2 y 4.

c) a Don [COMPLETAR] en pago de sus derechos en las herencias de ambos, el bien inventariado en el número 3.

d) a Don [COMPLETAR], como legado, el bien inventariado en el número 5.

e) a Don [COMPLETAR], como legado, el bien inventariado en el número 6.

Segundo. Ambos cónyuges [COMPLETAR] manifiestan:

- que la partija conjunta incluida en esta escritura quedará sin efecto de producirse el divorcio, nulidad, separación judicial o de hecho del matrimonio [COMPLETAR];

- que cualquiera de ambos cónyuges [COMPLETAR] tiene libertad para revocar unilateralmente por cualquier medio toda la partija en vida del otro, siempre que se lo notifique de manera fehaciente, o tras el fallecimiento del primero que muera;

- que en caso de revocación unilateral tras el fallecimiento de cualquiera de los cónyuges [COMPLETAR], la partición de los bienes del premuerto se efectuará por don [COMPLETAR] a quien nombran como contador-partidor a tal efecto;

- que los legitimarios no podrán reclamar el pago de sus legítimas hasta el fallecimiento del último de los cónyuges [COMPLETAR] o hasta la revocación unilateral por el cónyuge supérstite [COMPLETAR] tras el fallecimiento del primero;

- que en caso de que exista alguna discordancia entre las cuotas en que los herederos han sido instituidos en el testamento señalado en el expositivo [COMPLETAR] y los bienes ahora atribuidos, prevalecerán estas últimas atribuciones, siempre sin perjuicio de las legítimas;

- que prevalecerán las atribuciones efectuadas por medio de esta partija conjunta en el caso de que el supérstite disponga de algún bien correspondiente a alguna de las cuotas, siempre sin perjuicio de las legítimas;

- que cualquiera de los cónyuges [COMPLETAR] puede, tras el fallecimiento del primero de ellos, cumplir las previsiones particionales de esta partija conjunta por medio de negocios jurídicos intervivos dándole así eficacia anticipada;

- que cualquiera de los cónyuges [COMPLETAR] puede, tras el fallecimiento del primero de ellos, otorgar pactos sucesorios o realizar otro tipo de negocios inter vivos o mortis causa sobre los bienes objeto de esta partija conjunta, siempre que, de manera individual o conjuntamente con los herederos del fallecido, tenga la titularidad suficiente para ello sin que por tal motivo decaiga la partija.

Así lo dicen y otorgan en el presente documento extendido [COMPLETAR] folios de papel de copia simple, números [COMPLETAR] y los [COMPLETAR] siguientes en orden correlativo, que firman a continuación en prueba de conformidad.

En [LUGAR], a [FECHA].

Firma 	Firma

========================================================================
