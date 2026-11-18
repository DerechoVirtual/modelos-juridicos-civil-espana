---
name: medidas-civiles-junto-orden-proteccion-853
description: "Redacta el escrito «Medidas civiles junto con la orden de protección» (formulario 853 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas civiles junto con la orden de protección

> Formulario 0853 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (15 veces)
- [ ] CALLE (2 veces)
- [ ] DNI/NIE
- [ ] Nº (4 veces)
- [ ] IMPORTE (6 veces)
- [ ] NÚMERO (2 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 22 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, de»; «…, con domicilio en la C/ [CALLE] de»; «… pudieran ser constitutivos de delito de»; «…iguientes medidas: 1.º De carácter penal»; «…preventiva, orden de alejamiento, fianza»; «… del ejercicio de la patria potestad por»; «…tribuya la custodia de los hijos menores»; «… entender que la actitud de violencia de»; «…as intereso que no se acuerde a favor de»; «…nción de personal especializado los días»; «…en horario de»; «…horas del»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 544 ter de la LECr
- art. 158 del CC

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

### Formulario 0853 · Medidas civiles junto con la orden de protección

- Año del modelo: 2013
- Revisión 17-11-2026: 55 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE INSTRUCCIÓN DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en la C/ [CALLE], de [COMPLETAR] y DNI n.º [DNI/NIE], comparece y EXPONE:

Que mediante el presente escrito procedo a denunciar a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en la C/ [CALLE] de [COMPLETAR] por los siguientes hechos que pudieran ser constitutivos de delito de [COMPLETAR] relacionado con violencia doméstica: (narración de los hechos y relación de las pruebas en que se basan las afirmaciones).

Ante estos claros indicios de violencia doméstica, y con el fin de evitar riesgos para esta parte, interesamos que previas las actuaciones oportunas pero a la mayor urgencia posible, se dicte ORDEN DE PROTECCIÓN a favor de D./Dña. [NOMBRE Y APELLIDOS] acordando las siguientes medidas:

1.º De carácter penal [COMPLETAR] (prisión preventiva, orden de alejamiento, fianza [COMPLETAR])

2.º De carácter civil:

A) Custodia de los hijos menores: Sin perjuicio de en el momento procesal oportuno se resuelva sobre la situación futura del ejercicio de la patria potestad por [COMPLETAR] (ambos o uno de los progenitores), desde este momento intereso que se me atribuya la custodia de los hijos menores [COMPLETAR] (nombres) por entender que la actitud de violencia de [COMPLETAR] hacia la familia perjudica su natural desarrollo.

B) Régimen de visitas: (Opciones):

– En atención a las medidas de carácter penal solicitadas intereso que no se acuerde a favor de [COMPLETAR] ningún derecho de visitas, puesto que la compañía a los menores en estos momentos sólo puede causarles perjuicios.

– D./Dña. [NOMBRE Y APELLIDOS] podrá estar en compañía de sus hijos en centro habilitado al efecto y siempre bajo la atención de personal especializado los días [COMPLETAR] en horario de [COMPLETAR], o el tiempo que se estime pertinente por dicho centro.

– D./Dña. [NOMBRE Y APELLIDOS] podrá estar en compañía de sus hijos fines de semana alternos desde las [Nº] horas del [COMPLETAR] hasta las [Nº] horas del [COMPLETAR]

C) Atribución del uso de la vivienda conyugal a D./Dña. [NOMBRE Y APELLIDOS] para que resida en ella con sus hijos, por ser éste el interés más necesitado de protección.

D) Alimentos a favor de los hijos: D./Dña. [NOMBRE Y APELLIDOS] deberá contribuir a las necesidades de sus hijos con la cantidad mensual de [IMPORTE] euros para cada uno. Esta cifra se ingresará por anticipado dentro de los cinco primeros días de cada mes en la cuenta abierta en [COMPLETAR] con n.º [NÚMERO] y en su momento deberá ser objeto de actualización anual conforme al IPC o índice que lo sustituya.

Hay que tener en cuenta a la hora de fijar esta aportación que los ingresos de la persona denunciada ascienden a [IMPORTE] euros mensuales aproximadamente, mientras que la persona denunciante [ÓRGANO] (carece de ingresos o tiene unos ingresos de [COMPLETAR]) y que las necesidades mensuales de cada hijo suponen unos gastos fijos de [IMPORTE] euros por los siguientes conceptos

E) Contribución a las cargas comunes: En el período de convivencia se han creado una serie de cargas comunes que entiendo que tienen que ser sufragadas al cincuenta por ciento por cada uno de los obligados, y que consisten en: Por tanto intereso que D./Dña. [NOMBRE Y APELLIDOS] aporte la cantidad mensual de [IMPORTE] euros para el levantamiento de las mismas.

Las siguientes peticiones tienen su fundamento legal en el art. 544 ter de la LECr. y el art. 158 del CC. Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito con los documentos que acompaño, admita a trámite esta denuncia acordando la práctica de las diligencias oportunas para el esclarecimiento de los hechos, así como que, previos los trámites legales oportunos, se dicte orden de protección con las siguientes:

1) Medidas cautelares de orden penal [COMPLETAR]

2) Medidas de naturaleza civil:

A) Custodia de los hijos menores: que se atribuya a D./Dña. [NOMBRE Y APELLIDOS] la custodia de los hijos menores [COMPLETAR] (nombres).

B) Régimen de visitas: (Opciones):

– Que no se acuerde a favor de D./Dña. [NOMBRE Y APELLIDOS] ningún derecho de visitas.

– D./Dña. [NOMBRE Y APELLIDOS] podrá estar en compañía de sus hijos en centro habilitado al efecto, y siempre bajo la atención de personal especializado, los días [COMPLETAR] en horario de [COMPLETAR], o el tiempo que se estime pertinente por dicho centro.

– D./Dña. [NOMBRE Y APELLIDOS] podrá estar en compañía de sus hijos fines de semana alternos desde las [Nº] horas del [COMPLETAR] hasta las [Nº] horas del [COMPLETAR]

C) Atribución del uso de la vivienda conyugal a D./Dña. [NOMBRE Y APELLIDOS] para que resida en ella con sus hijos.

D) Alimentos a favor de los hijos: D./Dña. [NOMBRE Y APELLIDOS] deberá contribuir a las necesidades de sus hijos con la cantidad mensual de [IMPORTE] euros para cada uno. Esta cifra se ingresará por anticipado dentro de los cinco primeros días de cada mes en la cuenta abierta en [COMPLETAR] con n.º [NÚMERO] y en su momento deberá ser objeto de actualización anual conforme al IPC o índice que lo sustituya.

E) Contribución a las cargas comunes: que D./Dña. [NOMBRE Y APELLIDOS] aporte la cantidad mensual de [IMPORTE] euros para el levantamiento de las cargas comunes.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
