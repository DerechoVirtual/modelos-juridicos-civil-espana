---
name: escritura-autotutela-e-instrucciones-previas-galicia-537
description: "Redacta el escrito «Escritura de autotutela e instrucciones previas (Galicia)» (formulario 537 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de autotutela e instrucciones previas (Galicia)

> Formulario 0537 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- Escritura de «autotutela» (Galicia, 2016) en previsión de «modificación judicial de la capacidad»: hoy es autocuratela (arts. 271-274 CC) y/o poderes preventivos (arts. 256-262 CC); el notario la comunica al Registro Civil (art. 255 párr. 4.º CC). Rehacer el documento.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] FECHA
- [ ] COLEGIO
- [ ] NOMBRE Y APELLIDOS
- [ ] IMPORTE
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con residencia en»; «…, mayor de edad, vecino/a de»; «…io, y que su estado civil es y que tiene»; «…redacción Ley 8/2021 (BOE-A-2021-9233).]»; «… razones que fueran, nombro sustitutos a»; «…sulas tercera y cuarta de este documento»; «…erencia de mis ascendientes, nombrando a»; «…euros al año. -»; «…tad expresada en el presente documento a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 2/2006
- Ley 3/2001

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

### Formulario 0537 · Escritura de autotutela e instrucciones previas (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 13 campos de relleno marcados en blanco
- Avisos de la revisión: Escritura de «autotutela» (Galicia, 2016) en previsión de «modificación judicial de la capacidad»: hoy es autocuratela (arts. 271-274 CC) y/o poderes preventivos (arts. 256-262 CC); el notario la comunica al Registro Civil (art. 255 párr. 4.º CC). Rehacer el documento.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

ANTE MI, Notario del Ilustre Colegio de [COLEGIO], con residencia en [COMPLETAR],

COMPARECE

D/Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en Exhibe DNI/NIF

Sujeto/a al Derecho civil de Galicia.

Interviene en su propio nombre y derecho.

Le identifico por su expresado Documento Nacional de Identidad, cuyo número coincide con el de Identificación Fiscal y tiene, a mi juicio, capacidad legal y legitimación para esta ESCRITURA DE AUTOTUTELA e INSTRUCCIONES PREVIAS, y

EXPONE

Que es natural de donde nació el día que su nacimiento consta inscrito en el Registro Civil de al Tomo y Folio, y que su estado civil es y que tiene [COMPLETAR] hijos/ carece de descendientes

Que expresa su firme resolución de otorgar la presente escritura y, de conformidad con la Ley 2/2006, de Derecho civil de Galicia y con la la Ley 3/2001, de 28 de mayo, reguladora del consentimiento informado y de la historia clínica de los pacientes.

DISPONE

En previsión de padecer enfermedad o deficiencia física o psíquica que me dificulte el ejercicio de mi capacidad jurídica en igualdad de condiciones con las demás, propongo como curador a [NOTA DE REVISIÓN (comprobar): Autocuratela del art. 271 CC; revisar el resto de la escritura (ver aviso). Fuente: Código Civil (BOE-A-1889-4763) art. 271, redacción Ley 8/2021 (BOE-A-2021-9233).] [COMPLETAR] (persona o personas, físicas o jurídicas, para que ejerzan el cargo)/delego en mi cónyuge /en mi hijo la elección de mi la persona que vaya a ser mi curador o tutor, de entre la siguiente relación (relacionar e identificar a personas físicas y/o jurídicas entre las que se pueda elegir).

Para el caso de que el designado no pudiese tomar posesión del cargo, por las razones que fueran, nombro sustitutos a [COMPLETAR]

Además, expresamente excluyo de ese cargo a

En el ejercicio del cargo por mi futuro curador o tutor, dejo dicho lo siguiente (establecer reglas generales de funcionamiento y contenido del cargo y medidas de vigilancia, control y administración):

- En todo lo posible, quiero permanecer en mi vivienda habitual, rodeado de mis enseres personales, evitando internamientos de todo tipo.

- El designado como curador/tutor será mi representante en la toma de decisiones relacionadas con mi asistencia y cuidado médico, en aquello que no esté incluido en las cláusulas tercera y cuarta de este documento [COMPLETAR].

- Excluyo de la administración y disposición los bienes que forman la herencia de mis ascendientes, nombrando a [COMPLETAR] Administrador de ese haber.

- Establezco una retribución al curador/tutor de [IMPORTE] euros al año.

- [COMPLETAR]

Para la hipótesis descrita en la cláusula primera o para el supuesto en que no pueda tomar o manifestar decisiones sobre mi cuidado médico, como consecuencia de mi deterioro físico y/o mental y teniendo en cuenta que para mi proyecto vital es muy importante la calidad de vida, es mi deseo que no se prolongue cuando la situación es ya irreversible.

En este sentido, es mi voluntad que, si a juicio de los médicos que entonces me atiendan, no hay expectativas de recuperación sin que se sigan secuelas que impidan una vida digna según yo lo entiendo, mi voluntad es que:

- No sean aplicadas/se retiren si ya han empezado a aplicarse medidas de soporte vital o cualquier otra que intenten prolongar mi supervivencia.

- Se instauren las medidas paliativas que sean necesarias para el control de cualquier síntoma que puedan ser causa de dolor o sufrimiento.

- Se me preste una asistencia necesaria para proporcionarme un digno final de mi vida, con el máximo alivio del dolor, siempre y cuando no resulten contrarias a la buena práctica clínica.

Asimismo, quiero que se tengan en cuenta las siguientes instrucciones:

- Es mi deseo que, tras mi fallecimiento, se puedan utilizar mis órganos, para ser trasplantados a otras personas que los necesiten/no se donen mis órganos.

- Es mi deseo que, tras mi fallecimiento, mi cuerpo sea: enterrado en / inhumado/ donado a la ciencia.

Para el caso de que no se hubiere procedido al nombramiento de curador o tutor, y yo no pueda tomar o manifestar decisiones sobre mi cuidado médico, como consecuencia de mi deterioro físico y/o mental, nombro como mi representante e interlocutor válido y necesario con el equipo sanitario responsable de mi asistencia, para tomar las decisiones en mi nombre que no estén incluidas en las cláusulas tercera y cuarta de este documento, ser responsable de mi asistencia y garantizador de mi voluntad expresada en el presente documento a [COMPLETAR]:

Así lo dice y otorga.

Hago las reservas y advertencias legales, en especial le advierto de la trascendencia de este otorgamiento y del carácter revocable del mismo.

Leo esta escritura íntegramente a la compareciente, una vez advertida del derecho que tiene a hacerlo por si, del que hace uso; enterada de su contenido manifiesta que el mismo es conforme con su voluntad, la aprueba y firma conmigo la notario que doy de su contenido, en lo pertinente, y de ir extendida en

========================================================================
