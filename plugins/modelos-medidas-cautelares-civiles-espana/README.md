# Medidas cautelares y diligencias preliminares · España

> Plugin de Claude Code `modelos-medidas-cautelares-civiles-espana` · **20 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para asegurar el pleito: medidas cautelares antes o durante el proceso (solicitud, oposición y alzamiento), caución, anotación preventiva de la demanda, y diligencias preliminares para preparar la demanda (en especial, las de propiedad horizontal).

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 20 está al final):

- **Contestaciones, oposiciones y alegaciones** (2). Por ejemplo: Oposición a medidas cautelares acordadas por arbitraje pendiente sin audiencia del demandado; Oposición a diligencias preliminares de propiedad horizontal.
- **Solicitudes y expedientes** (7). Por ejemplo: Devolución de la caución prestada en diligencias preliminares; Medida cautelar previa a la demanda: acceso a vivienda o local; Prórroga de anotación preventiva de demanda.
- **Escritos de trámite** (3). Por ejemplo: Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial; Impugnación de la oposición a las diligencias preliminares; Otrosí: caución.
- **Actos y resoluciones de la Administración o del órgano judicial** (1). Por ejemplo: Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad.
- **Otros** (7). Por ejemplo: Caución en sustitución de la medida de aseguramiento; Audiencia de las partes sobre la caución en tercería de dominio; Caución ofrecida en sustitución de medidas (general).

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Solicitud de medidas cautelares»
   - «Ofrecer caución en sustitución de una medida cautelar»
   - «Diligencias preliminares para que la comunidad exhiba sus documentos»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-medidas-cautelares-civiles-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-medidas-cautelares-civiles-espana:otrosi-medidas-cautelares-art-727-lec-inventario-168`. Los nombres están en la lista de formularios de abajo.

## Qué hace Claude cuando usas un formulario

1. Comprueba que Jurisprudenciator está conectado. Si no lo está, se para y te dice cómo conectarlo: no redacta nada sin él.
   Todos los datos jurídicos del escrito (artículos vigentes, sentencias con su ECLI, convenios, datos registrales) salen de Jurisprudenciator; nunca de memoria.
2. Te pide en una sola tanda los datos del caso (partes, órgano, fechas, importes…). Lo que no sepas queda como hueco visible.
3. Resuelve contigo las opciones que el formulario deja abiertas y decide qué párrafos opcionales entran según los hechos.
4. Aplica las correcciones y avisos de la revisión del 17-11-2026 (reformas legales, órganos, plazos).
5. Comprueba en el BOE, con Jurisprudenciator, cada norma que cita el escrito; si alguna ha cambiado, usa la redacción vigente y te lo dice.
6. Te indica el plazo y ante quién se presenta, y te entrega el escrito en Word con un resumen de lo que queda pendiente.

El resultado es un borrador para que lo revise un profesional antes de presentarlo.

## Antes de empezar

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 2.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-medidas-cautelares-civiles-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-medidas-cautelares-civiles-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-medidas-cautelares-civiles-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-medidas-cautelares-civiles-espana:<skill>`.

### Contestaciones, oposiciones y alegaciones (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1399 | Oposición a diligencias preliminares de propiedad horizontal | 2013 | `oposicion-diligencias-preliminares-propiedad-horizontal-1399` |
| 1484 | Oposición a medidas cautelares acordadas por arbitraje pendiente sin audiencia del demandado | 2014 | `oposicion-medidas-cautelares-acordadas-arbitraje-1484` |

### Solicitudes y expedientes (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 187 | Devolución de la caución prestada en diligencias preliminares | 2021 | `devolucion-caucion-prestada-diligencias-preliminares-187` |
| 512 | Medida cautelar previa a la demanda: acceso a vivienda o local | 2016 | `medida-cautelar-previa-demanda-acceso-vivienda-local-512` |
| 1040 | Medidas cautelares (general) | 2013 | `medidas-cautelares-general-1040` |
| 1100 | Alzamiento de medidas cautelares por no presentar la demanda en plazo | 2013 | `alzamiento-medidas-cautelares-no-presentar-demanda-plazo-1100` |
| 1107 | Medida cautelar con el proceso iniciado (general) | 2013 | `medida-cautelar-proceso-iniciado-general-1107` |
| 1401 | Abono de gastos de diligencias preliminares de propiedad horizontal | 2013 | `abono-gastos-diligencias-preliminares-propiedad-1401` |
| 1494 | Prórroga de anotación preventiva de demanda | 2014 | `prorroga-anotacion-preventiva-demanda-1494` |

### Escritos de trámite (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 168 | Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial | 2021 | `otrosi-medidas-cautelares-art-727-lec-inventario-168` |
| 634 | Impugnación de la oposición a las diligencias preliminares | 2015 | `impugnacion-oposicion-diligencias-preliminares-634` |
| 1038 | Otrosí: caución | 2013 | `otrosi-caucion-1038` |

### Actos y resoluciones de la Administración o del órgano judicial (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1373 | Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad | 2013 | `diligencias-preliminares-propiedad-horizontal-exhibir-1373` |

### Otros (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 981 | Caución en sustitución de la medida de aseguramiento | 2013 | `caucion-sustitucion-medida-aseguramiento-981` |
| 1022 | Audiencia de las partes sobre la caución en tercería de dominio | 2013 | `audiencia-partes-sobre-caucion-terceria-dominio-1022` |
| 1054 | Caución ofrecida en sustitución de medidas (general) | 2013 | `caucion-ofrecida-sustitucion-medidas-general-1054` |
| 1106 | Medida cautelar de depósito de cosa mueble con la demanda | 2013 | `medida-cautelar-deposito-cosa-mueble-demanda-1106` |
| 1110 | Caución prestada por el demandante | 2013 | `caucion-prestada-demandante-1110` |
| 1340 | Fijación de caución en diligencias preliminares de propiedad horizontal | 2013 | `fijacion-caucion-diligencias-preliminares-propiedad-1340` |
| 1400 | Pérdida de la caución de diligencias preliminares por no presentar la demanda | 2013 | `perdida-caucion-diligencias-preliminares-no-presentar-1400` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

## Uso interno

Plugin de uso interno. Antes de venderlo o dárselo a alumnos, hay que sustituir los textos por plantillas de redacción propia.
