---
name: nombramiento-inmediato-defensor-desaparecido-antes-790
description: "Redacta el escrito «Nombramiento inmediato de defensor del desaparecido antes de la comparecencia» (formulario 790 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nombramiento inmediato de defensor del desaparecido antes de la comparecencia

> Formulario 0790 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (6 veces)
- [ ] NÚMERO
- [ ] Nº
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…aciones jurídicas: 1.ª) Que mi padre, D.»; «…de»; «…de [COMPLETAR], a su lugar de trabajo»; «…administrador social único de la entidad»; «…una urbanización sita en la localidad de»; «…de»; «…, quien reside fuera de»; «…, con domicilio en la calle [CALLE] de»; «…de [COMPLETAR], de mi»; «…, con domicilio en la calle [CALLE] de»; «…de [COMPLETAR], y»; «…, con domicilio en la calle [CALLE] de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 69.2 de la Ley 15/2015
- art. 181 del Código Civil
- art. 69.2 LJV
- artículo 68.1 LJV
- art. 69.1 LJV
- art. 68.4 LJV

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

### Formulario 0790 · Nombramiento inmediato de defensor del desaparecido antes de la comparecencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 36 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de nombramiento urgente de defensor de persona desaparecida.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 69.2 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de nombramiento urgente de defensor de persona desaparecida, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi padre, D. [COMPLETAR], viudo y de [Nº] años de edad, desapareció el pasado [FECHA] sin dejar rastro de su paradero, cuando salió a dar un paseo de su domicilio sito en la calle [CALLE] de [COMPLETAR], a su lugar de trabajo [COMPLETAR]. A pesar de la denuncia presentada ante el Cuerpo Nacional de Policía, y las diversas pesquisas llevadas a cabo en su búsqueda, no se ha podido obtener hasta la fecha noticia alguna de su persona.

2.ª) Que D. es el administrador social único de la entidad [COMPLETAR] SL, que gestiona el negocio de inmobiliaria que procura su sustento. Como tal administrador, es el único representante legal de dicha mercantil y, por ello, la única persona legitimada para tomar decisiones importantes sobre la marcha del negocio. El lunes de la próxima semana, día [FECHA], está prevista la firma de una importantísima serie de contratos relativos a una urbanización sita en la localidad de [COMPLETAR] de [COMPLETAR], y que ha visto retrasada la entrega de las viviendas más de un año. El acto no se puede retrasar más, habida cuenta de las amenazas de reclamaciones de daños y perjuicios por parte de los futuros propietarios; y la inmobiliaria debe asistir como intermediario en todos los contratos. Dado que nadie más que mi padre puede firmar en nombre de la empresa, es ineludible que alguien pueda ocuparse de ello, a fin de que las partes no acudan a otra vía de intermediación que supondría la pérdida de tales contratos, y ocasionaría un daño irreparable a la reputación y marcha del citado negocio.

3.ª) Que, por ello, y de conformidad con el art. 181 del Código Civil y con el art. 69.2 LJV, acudo al presente expediente para instar el nombramiento urgente de un defensor que represente al desaparecido en el negocio indicado, que no admite ningún tipo de demora. Solicito, por ello, que el nombramiento se haga sin convocatoria de comparecencia, sin perjuicio de que posteriormente se continúe por los trámites ordinarios a los efectos de ratificar o revocar el nombramiento, con arreglo a lo dispuesto en el apartado primero del citado precepto legal. Me encuentro legitimado para la presente solicitud, como parte interesada que soy en el mantenimiento del negocio en el que se generan los ingresos con los que vive mi padre, y en el cual trabajo como empleado suyo. En este sentido, y dado que conozco la marcha del negocio en mi desempeño laboral, solicito mi propio nombramiento como defensor. Así, en virtud de lo dispuesto en el párrafo segundo del mencionado art. 181 del Código Civil, siendo mi padre viudo, soy, con mi
hermano D. [NOMBRE Y APELLIDOS]
hermana Dña.
[NOMBRE Y APELLIDOS], quien reside fuera de [COMPLETAR], el pariente más próximo del desaparecido, y quien conoce todos los pormenores del acto urgente que motiva la presente petición.

4.ª) Que, en prueba de todo ello, y en atención a la comparecencia que se convocará con posterioridad al nombramiento, ofrezco la siguiente información testifical: mi
hermano D. [NOMBRE Y APELLIDOS]
hermana Dña.
[NOMBRE Y APELLIDOS], con domicilio en la calle [CALLE] de [COMPLETAR], de mi [COMPLETAR]
tío y hermano de mi padre D. [NOMBRE Y APELLIDOS]
tía y hermana de mi padre Dña.
[NOMBRE Y APELLIDOS], con domicilio en la calle [CALLE] de [COMPLETAR], y [COMPLETAR]
del empleado de la inmobiliaria D. [NOMBRE Y APELLIDOS]
empleada de la inmobiliaria Dña.
[NOMBRE Y APELLIDOS], con domicilio en la calle [CALLE] de [COMPLETAR].

5.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al artículo 68.1 LJV, al encontrarse en su partido judicial el domicilio del cual desapareció D. [COMPLETAR], sito en la calle [CALLE] de [COMPLETAR].

6.ª) Se acompañan a este escrito copia de la denuncia presentada ante el Cuerpo Nacional de Policía, copia de la escritura pública y estatutos sociales de la entidad [COMPLETAR] SL, copia de mi contrato laboral, y documentación preparatoria relativa a la firma de los contratos de la próxima semana.

Por todo lo expuesto, al amparo del art. 181 del Código Civil, y de los arts. 67 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; se dicte de inmediato decreto por el Letrado de la Administración de Justicia nombrándome defensor de mi padre D. [COMPLETAR], desaparecido, sin esperar a la celebración de comparecencia. Y posteriormente, a los efectos de ratificar o revocar el nombramiento, que se continúe por los trámites previstos en el art. 69.1 LJV, con convocatoria de comparecencia y citación del Ministerio Fiscal, de los testigos propuestos y de quien se considere interesado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 68.4 LJV, no exige requisito alguno de postulación.

========================================================================
