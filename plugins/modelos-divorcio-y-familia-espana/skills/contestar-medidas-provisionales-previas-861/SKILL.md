---
name: contestar-medidas-provisionales-previas-861
description: "Redacta el escrito «Contestar a las medidas provisionales previas» (formulario 861 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestar a las medidas provisionales previas

> Formulario 0861 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº (5 veces)
- [ ] IMPORTE (7 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] DNI/NIE
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…esolver sobre la pretensión principal de»; «…teresa que se le atribuya la custodia de»; «…mplio: alimentación, higiene, educación,»; «… no custodio con sus hijos las tardes de»; «… sus ingresos de trabajo de los meses de»; «…a»; «…gualmente deberá requerirse a la empresa»; «…l uso de la vivienda familiar situada en»; «…irir la vivienda familiar con la entidad»; «…, n.º [Nº] de préstamo»; «…Código Civil. La custodia se atribuirá a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 771 de la LEC
- arts. 102 y 103 del CC
- art. 328 de la LEC
- art. 96 del CC
- art. 154 del Código Civil

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

### Formulario 0861 · Contestar a las medidas provisionales previas

- Año del modelo: 2013
- Revisión 17-11-2026: 34 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Con la venia:

Procedemos a contestar a la solicitud de medidas previas promovidas por D./Dña. [NOMBRE Y APELLIDOS] en el sentido de oponernos parcialmente a las pretensiones de contrario en atención a las siguientes consideraciones, razonamientos y fundamentos jurídicos:

1.º El art. 771 de la LEC permite la adopción de las medidas a las que se refieren los arts. 102 y 103 del CC antes de resolver sobre la pretensión principal de [COMPLETAR] (separación o divorcio) sin que medie ninguna justificación, razón por la cual no podemos oponernos a la tramitación de este procedimiento aunque sí a las concretas pretensiones de contrario.

Mostramos nuestra conformidad con lo expuesto de contrario sobre las fechas de celebración del matrimonio, nacimiento de los hijos, régimen económico matrimonial y establecimiento del domicilio familiar en

2.º Respecto a la patria potestad, guarda y custodia: Nada hay que objetar sobre el ejercicio conjunto de la patria potestad y sí contra la petición por la otra parte de la atribución para sí de la custodia de los hijos comunes.

Mi representado interesa que se le atribuya la custodia de [COMPLETAR] (nombres de los hijos): por las siguientes razones:

Desde su nacimiento ambos progenitores han compartido las tareas de atención de los menores en un sentido amplio: alimentación, higiene, educación, [COMPLETAR] Por esa razón y desde este momento interesamos que por el equipo psicosocial adscrito a este Tribunal se elabore informe tras oír al núcleo familiar sobre la adopción del régimen de custodia. A esto hay que añadir que el horario de trabajo de los padres propicia esta situación, ya que

3.º En cuanto al régimen de comunicaciones, visitas y vacaciones por esta parte se propone que el progenitor no custodio pueda comunicarse libremente con sus hijos telefónicamente o por medios informáticos siempre que no afecte a su descanso y rendimiento escolar.

Entre semana podrá estar el progenitor no custodio con sus hijos las tardes de [COMPLETAR] desde la salida del colegio hasta las [Nº] horas. Estará también con ellos fines de semanas alternos desde el viernes a las [Nº] horas, hasta el domingo a las [Nº] horas.

Las vacaciones de Navidad, Semana Santa y verano se repartirán por mitad entre los cónyuges (especificar días y horarios si resulta necesario).

Los hijos se recogerán y reintegrarán al hogar familiar por el progenitor que ejerza el derecho de visitas, salvo los días especificados en que se recoja a los menores a la salida del colegio.

4.º Contribución a las cargas del matrimonio:

Para hacer frente a las necesidades de los hijos el progenitor no custodio deberá ingresar por anticipado y dentro de los cinco primeros días de cada mes en la cuenta que al efecto se designe de contrario, la cantidad de [IMPORTE] euros, a razón de [IMPORTE] euros por cada hijo. Esta cantidad se actualizará anualmente de acuerdo al IPC elaborado por el INE o índice que lo sustituya.

Los gastos extraordinarios de los hijos serán sufragados al 50% entre ambos progenitores, entendiéndose por tales los médicos y sanitarios no cubiertos por la Seguridad Social o seguro que tenga contratado cualquiera de los padres y, respecto a los educativos, las clases extraordinarias necesarias para superar un curso escolar.

La presente propuesta tiene su razón de ser no solo en la pretensión de custodia que se interesa, sino también en las necesidades de los hijos consistentes en [DESCRIBIR] (según se acredita con los documentos n.º [NÚMERO] que presentamos, consistentes en [DESCRIBIR]) y en los ingresos de quienes deben prestarlos. Presentamos como documentos n.º [NÚMERO] declaración de IRPF de D./Dña. [NOMBRE Y APELLIDOS] del último año y las nóminas por sus ingresos de trabajo de los meses de [COMPLETAR] a [COMPLETAR] Con estos datos se puede comprobar que sus ingresos mensuales, prorrateadas las pagas extras, ascienden a unos [IMPORTE] euros al mes.

La parte demandante no ha probado sus ingresos, pero esta parte entiende que ascienden a unos [IMPORTE] euros mensuales. Interesamos que por este Tribunal se acceda a la base de datos fiscal a fin de que recabe información sobre la declaración de IRPF de D./Dña. [NOMBRE Y APELLIDOS] con DNI n.º [DNI/NIE] de los años

En aplicación del art. 328 de la LEC igualmente interesaremos que se proceda a exhibir por la parte demandante sus nóminas de los últimos [Nº] meses, e igualmente deberá requerirse a la empresa [COMPLETAR] para que, con relación a este trabajador certifique sobre las cantidades abonadas por todos los conceptos a

5.º Atribución del uso de la vivienda familiar:

En atención a lo establecido en el art. 96 del CC el uso de la vivienda familiar situada en [COMPLETAR] deberá atribuirse a mi patrocinado al interesar igualmente esta parte la custodia de los menores.

(En su caso) Solicitamos, no obstante la limitación en el tiempo de la atribución del uso de la vivienda al cónyuge custodio hasta la liquidación dé gananciales en todo caso con un plazo máximo de dos años.

6.º Otros gastos:

Sin perjuicio de ser considerada como una deuda de la sociedad de gananciales, interesamos que se declare la expresa obligación de ser sufragado al 50% el préstamo contratado por ambos para adquirir la vivienda familiar con la entidad [COMPLETAR], n.º [Nº] de préstamo [COMPLETAR] (Presentamos como documentos n.º [NÚMERO] copia de escritura de préstamo hipotecario, así como últimos recibos de liquidación de la deuda en los que se comprueba que el capital pendiente de abonar asciende a [IMPORTE] euros y la cuota mensual a [IMPORTE] euros). Igualmente deberán liquidarse en esa proporción los gastos de comunidad de propietarios y el IBI.

En definitiva esta parte interesa la adopción de las siguientes medidas:

1.º Que se acuerde el derecho a vivir separados de D. y Dña. [NOMBRE Y APELLIDOS] y fijar libremente su domicilio, así como que cese la presunción de convivencia y el derecho a vincular bienes del otro cónyuge en el ejercicio de su actividad económica, quedando revocados todos los consentimientos y poderes mutuos.

2.º Que se adopten las siguientes medidas para las relaciones futuras entre los cónyuges y de éstos con los hijos menores.

a) La patria potestad se ejercerá conjuntamente por ambos progenitores con las obligaciones establecidas en el art. 154 del Código Civil. La custodia se atribuirá a [COMPLETAR] (la madre o el padre)

b) Se establecerá el siguiente régimen de comunicación, visitas y vacaciones:

c) El progenitor no custodio contribuirá a las cargas del matrimonio con la cantidad de [IMPORTE] euros al mes, cantidad que será anualmente actualizada de acuerdo al IPC elaborado por el INE o índice que lo sustituya. Esta cantidad se abonará por anticipado dentro de los primeros cinco días de cada mes y será ingresada en la cuenta que al efecto se designe.

Los gastos extraordinarios de los hijos serán sufragados al 50% entre ambos progenitores, entendiéndose por tales los médicos y sanitarios no cubiertos por la Seguridad Social o seguro que tenga contratado cualquiera de los padres y, respecto a los educativos, las clases extraordinarias necesarias para superar un curso escolar.

d) Se atribuirá el uso de la vivienda familiar y el ajuar a D./Dña. [NOMBRE Y APELLIDOS] para que viva en ella con sus hijos. El otro cónyuge podrá retirar, previo inventario, sus bienes y enseres de uso personal.

e) Determinar, respecto a las deudas de la sociedad de gananciales consistentes en [DESCRIBIR] la obligación de abono al 50% entre ambos cónyuges.

========================================================================
