---
name: impugnacion-resolucion-reconoce-justicia-gratuita-ante-896
description: "Redacta el escrito «Impugnación de la resolución que reconoce la justicia gratuita, ante el órgano judicial» (formulario 896 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de la resolución que reconoce la justicia gratuita, ante el órgano judicial

> Formulario 0896 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NÚMERO (5 veces)
- [ ] SEDE
- [ ] FECHA
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ISIÓN DE ASISTENCIA JURÍDICA GRATUITA DE»; «…damente acreditado en autos de juicio de»; «…numeración del juzgado de procedencia).]»; «…a a efectos múltiples fijado para el año»; «…puestos Generales del Estado para el año»; «…ene fuera de esta ciudad, en concreto en»; «…gresos del cónyuge por su actividad como»; «… que perciben por la minusvalía del hijo»; «…y que ascienden a»; «…clusivamente por intereses propios, pues»; «…y una certificación de ésta, al Tribunal»; «…en juicio de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 20 de la Ley 1/1996

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

### Formulario 0896 · Impugnación de la resolución que reconoce la justicia gratuita, ante el órgano judicial

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

AL SECRETARIO DE LA COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA DE [COMPLETAR]

PARA ANTE EL TRIBUNAL COMPETENTE

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A] (parte contraria en el proceso principal), según tengo debidamente acreditado en autos de juicio de [COMPLETAR] n.º [NÚMERO] tramitados ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] (ciudad), ante el Secretario de la Comisión de Asistencia Jurídica Gratuita comparece y EXPONE:

Que mediante el presente escrito y en aplicación del art. 20 de la Ley 1/1996, de asistencia jurídica gratuita, procedo a impugnar la resolución n.º [NÚMERO] de fecha [FECHA] dictada en el expediente de asistencia jurídica gratuita n.º [NÚMERO] por el Organismo al que me dirijo, basándome en las siguientes

ALEGACIONES

(En su caso) Nos oponemos en este momento a la concesión del derecho a la asistencia jurídica concedido a D./Dña. [NOMBRE Y APELLIDOS] y del que esta parte no ha tenido conocimiento hasta la fecha por no habérsele dado traslado del expediente por la Comisión.

El art. 3.º de la Ley 1/1996 establece que se reconocerá el derecho a aquellas personas cuyos ingresos económicos computados anualmente por todos los conceptos y por unidad familiar no superen el doble del salario mínimo interprofesional vigente en el momento de efectuar la solicitud.

El indicador público de la renta a efectos múltiples fijado para el año [COMPLETAR] es de [IMPORTE] euros mensuales según establece la Ley de Presupuestos Generales del Estado para el año [COMPLETAR].

Por otro lado el art. 4.º de la Ley 1/1996 de Asistencia Jurídica Gratuita excluye la concesión del derecho si los signos externos manifiestan una capacidad económica superior a la declarada.

No se ha tenido en cuenta en el reconocimiento del derecho las propiedades que la unidad familiar tiene fuera de esta ciudad, en concreto en [COMPLETAR], según se acredita con las notas simples del Registro de la Propiedad n.º [NÚMERO] de esa ciudad. Tampoco se consideraron los ingresos del cónyuge por su actividad como [COMPLETAR], dejando acotados desde este momento los archivos de la Delegación de Hacienda a efectos probatorios, ni las ayudas que perciben por la minusvalía del hijo [COMPLETAR] y que ascienden a [COMPLETAR], tal como figura en el documento n.º [NÚMERO] del expediente.

En principio negamos también la afirmación de que se está litigando exclusivamente por intereses propios, pues [COMPLETAR] (razones de fondo).

(En el caso de que se hubiera reconocido parcialmente el derecho) Finalmente y una vez acreditado que los ingresos familiares exceden del doble del salario mínimo interprofesional e incluso del cuádruplo deberá denegarse el derecho de asistencia jurídica gratuita afectando a todas las prestaciones recogidas en el art. 6.º de la Ley 1/1996.

Por lo expuesto,

SOLICITO AL SECRETARIO DE LA COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y acuerde su remisión, junto con el expediente correspondiente a la resolución impugnada y una certificación de ésta, al Tribunal [COMPLETAR] (el competente) a fin de que en su día, previos los trámites legales oportunos, se dicte por éste resolución revocando la ahora recurrida y acordando denegar a D./Dña. [NOMBRE Y APELLIDOS] el derecho a la asistencia jurídica gratuita para litigar contra D./Dña. [NOMBRE Y APELLIDOS] en juicio de [COMPLETAR] ante el Tribunal

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
