---
name: declinatoria-competencia-objetiva-576
description: "Redacta el escrito «Declinatoria por competencia objetiva» (formulario 576 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declinatoria por competencia objetiva

> Formulario 0576 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Formulario «adaptado a la LO 1/2025» que mantenía el límite de 90 € del juez de paz: ahora 150 € (art. 47.1 LEC). Corregido en procesal.json.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (4 veces)
- [ ] CALLE
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LUGAR
- [ ] FECHA

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 49 y 63.2 LEC
- art. 63.1 LEC
- art. 65 LEC
- art. 64.1 LEC
- arts. 99 y 100 LOPJ
- art. 47 LEC
- art. 250.1 LEC
- art. 394.1 LEC

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

### Formulario 0576 · Declinatoria por competencia objetiva

- Año del modelo: 2016
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Formulario «adaptado a la LO 1/2025» que mantenía el límite de 90 € del juez de paz: ahora 150 € (art. 47.1 LEC). Corregido en procesal.json.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito formulando declinatoria por falta de competencia objetiva del Tribunal de Instancia por tratarse del ejercicio de una acción personal de reclamación de cantidad de cuantía no superior a 150 euros [NOTA DE REVISIÓN: Competencia del juez o jueza de paz: asuntos de cuantía no superior a 150 € no comprendidos en el art. 250.1 LEC. Fuente: LEC art. 47.1 (redacc. LO 1/2025, BOE-A-2025-76, vigente desde 3-4-2025).] cuyo conocimiento corresponde a los Jueces y Juezas de Paz.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante la escritura de poder otorgada al efecto, que acepto y acompaño para su unión a los autos por copia testimoniada bastante, con devolución del original por necesitarlo a otros usos; dirigido el poderdante por el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO], del Iltre. Colegio de [LOCALIDAD], con despacho abierto en [LOCALIDAD], calle [CALLE], ante el Tribunal comparezco y como mejor proceda en derecho, DIGO:

Que por medio del presente escrito, y conforme a lo establecido en el art. 49, en relación a los arts. 63 y concordantes de la LEC, formulo en plazo y forma, declinatoria por falta de competencia objetiva de este Tribunal para conocer de los presentes autos de juicio verbal n.º [Nº DE PROCEDIMIENTO]/[AÑO], en base a los siguientes

HECHOS

PRIMERO

Se ejercita frente a mi mandante una acción personal en reclamación de cantidad derivada de un contrato de reconocimiento de deuda por un importe de 80 euros.

SEGUNDO

Como se observa en la documental obrante en autos, así como en los fundamentos de la pretensión de la actora, existe una clara falta de competencia objetiva de los Tribunales de Instancia al ser una cuestión que debe tramitarse ante los Jueces y Juezas de Paz, por tratarse de una reclamación que debe sustanciarse exclusivamente por razón de la cuantía, siendo ésta no superior a 150 euros, sin que nos encontremos ante ninguna materia cuya decisión se reserve al juicio verbal. Por consiguiente, siendo demandante y demandado personas físicas con domicilio en [LOCALIDAD], la competencia para el conocimiento de las presentes actuaciones no se encuentra atribuida al Tribunal que me dirijo sino al Juez o Jueza de Paz de [LOCALIDAD].

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

El presente escrito se presenta ante el Tribunal que está conociendo del asunto, conforme a lo dispuesto en los arts. 49 y 63.2 LEC.

II.- LEGITIMACIÓN

Conforme a lo dispuesto en el art. 63.1 LEC, mi mandante está legitimado para proponer esta cuestión de competencia, puesto que es el demandado en el proceso.

III.- PROCEDIMIENTO

Procede, como cauce procesal, la presente declinatoria, según trámite del art. 65 LEC, habida cuenta que es el único para denunciar la falta de competencia de todo tipo (art. 63.1, párrafo 2.º LEC).

Conforme prevé el art. 64.1 LEC, la declinatoria se habrá de proponer dentro de los diez primeros días del plazo para contestar a la demanda, y surtirá el efecto de suspender, hasta que sea resuelta, el plazo para contestar y el curso del procedimiento principal, suspensión que declarará el Letrado de la Administración de Justicia.

IV.- FONDO

Conforme a lo previsto en los arts. 99 y 100 LOPJ, los Jueces y Juezas de Paz conocerán, en el orden civil, de la substanciación en primera instancia, fallo y ejecución de los procesos que la Ley determine; y según dispone el art. 47 LEC les corresponde el conocimiento, en primera instancia, de los asuntos civiles de cuantía no superior a ciento cincuenta euros que no estén comprendidos en ninguno de los casos a que, por razón de la materia, se refiere el art. 250.1 LEC.

V.- COSTAS

De conformidad al principio de vencimiento objeto del art. 394.1 LEC, las costas deberán imponerse a la demandante.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito con sus copias, se sirva admitir uno y otras, tenerme por comparecido y parte en la representación que ostento, a los solos efectos de plantear la presente declinatoria, ordenando se extiendan conmigo las sucesivas diligencias y notificaciones; y por promovida cuestión de competencia objetiva:

1) Se acuerde por el Letrado de la Administración de Justicia la suspensión del curso de las presentes actuaciones.
2) Dé traslado de esta petición a la parte contraria para que en el plazo de cinco días manifieste lo que a su derecho convenga.
3) Dicte Auto por el que acuerde abstenerse del conocimiento de este asunto señalando que la parte actora deberá usar su derecho ante el Juez o Jueza de Paz.
4) Imponga las costas a la parte actora.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
