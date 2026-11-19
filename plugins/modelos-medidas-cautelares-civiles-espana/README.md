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

- **Dónde funciona:** en Claude Code y en Claude (web, escritorio y Cowork).
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 2.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-medidas-cautelares-civiles-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-medidas-cautelares-civiles-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

## Lista completa de formularios

Cada formulario es una skill. Puedes pedirlo con tus palabras o llamarlo por su nombre (`/modelos-medidas-cautelares-civiles-espana:<skill>`). Son 20, agrupados por tipo de escrito:

- **Índice del plugin** (`indice`): te ayuda a elegir el formulario adecuado cuando no sabes cuál usar; le cuentas el caso y te propone uno, o dos o tres para que elijas.

### Contestaciones, oposiciones y alegaciones (2)

- **Oposición a diligencias preliminares de propiedad horizontal** (`oposicion-diligencias-preliminares-propiedad-horizontal-1399`). Escrito de oposición a las diligencias preliminares solicitadas en materia de propiedad horizontal, con las razones por las que no deben practicarse, ante la Sección Civil del Tribunal de Instancia.
- **Oposición a medidas cautelares acordadas por arbitraje pendiente sin audiencia del demandado** (`oposicion-medidas-cautelares-acordadas-arbitraje-1484`). Escrito del demandado que se opone a las medidas cautelares acordadas, sin oírle, en apoyo de un arbitraje pendiente, y pide que se alcen o se modifiquen, ante el Tribunal de Instancia.

### Solicitudes y expedientes (7)

- **Abono de gastos de diligencias preliminares de propiedad horizontal** (`abono-gastos-diligencias-preliminares-propiedad-1401`). Escrito para pedir el abono de los gastos y costas generados en unas diligencias preliminares de propiedad horizontal, ante la Sección Civil del Tribunal de Instancia.
- **Alzamiento de medidas cautelares por no presentar la demanda en plazo** (`alzamiento-medidas-cautelares-no-presentar-demanda-plazo-1100`). Escrito para pedir el alzamiento de las medidas cautelares acordadas antes de la demanda porque el solicitante no la presentó dentro del plazo, ante la Sección Civil del Tribunal de Instancia.
- **Devolución de la caución prestada en diligencias preliminares** (`devolucion-caucion-prestada-diligencias-preliminares-187`). Escrito para pedir que se devuelva la caución prestada en unas diligencias preliminares, una vez cumplida su finalidad, ante la Sección Civil del Tribunal de Instancia.
- **Medida cautelar con el proceso iniciado (general)** (`medida-cautelar-proceso-iniciado-general-1107`). Solicitud de medida cautelar formulada con el proceso ya iniciado, con la justificación de su necesidad y de la caución, dentro de un juicio ordinario ante el Tribunal de Instancia.
- **Medida cautelar previa a la demanda: acceso a vivienda o local** (`medida-cautelar-previa-demanda-acceso-vivienda-local-512`). Solicitud de medida cautelar, previa a la demanda y sin oír al demandado, para acceder a una vivienda o local y hacer obras en régimen de propiedad horizontal.
- **Medidas cautelares (general)** (`medidas-cautelares-general-1040`). Escrito del procurador que solicita medidas cautelares en nombre de su representado, con la apariencia de buen derecho, el riesgo de demora y la caución, ante el Tribunal de Instancia.
- **Prórroga de anotación preventiva de demanda** (`prorroga-anotacion-preventiva-demanda-1494`). Escrito para pedir la prórroga de la anotación preventiva de demanda en el Registro de la Propiedad antes de que caduque, conforme a la Ley Hipotecaria, ante el Tribunal de Instancia.

### Escritos de trámite (3)

- **Impugnación de la oposición a las diligencias preliminares** (`impugnacion-oposicion-diligencias-preliminares-634`). Escrito del solicitante que impugna la oposición a las diligencias preliminares y pide que se acuerde su práctica, ante la Sección Civil del Tribunal de Instancia.
- **Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial** (`otrosi-medidas-cautelares-art-727-lec-inventario-168`). Otrosí de la demanda que pide como medidas cautelares formar inventario de los bienes gananciales y nombrar un administrador judicial, con base en el art. 727 LEC.
- **Otrosí: caución** (`otrosi-caucion-1038`). Otrosí de la demanda sobre la caución: bien renuncia a exigirla al demandado, bien pide que la preste por la cuantía que se calcula provisionalmente para responder de frutos, daños y costas.

### Actos y resoluciones de la Administración o del órgano judicial (1)

- **Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad** (`diligencias-preliminares-propiedad-horizontal-exhibir-1373`). Escrito del procurador de una comunidad de propietarios que pide diligencias preliminares para que se exhiban los documentos de la comunidad, ante la Sección Civil del Tribunal de Instancia.

### Otros (7)

- **Audiencia de las partes sobre la caución en tercería de dominio** (`audiencia-partes-sobre-caucion-terceria-dominio-1022`). Escrito con el que las partes se pronuncian sobre la caución que debe prestar el tercerista en una tercería de dominio, ante la Sección Civil del Tribunal de Instancia, para aceptarla, discutirla o pedir que se ajuste.
- **Caución en sustitución de la medida de aseguramiento** (`caucion-sustitucion-medida-aseguramiento-981`). Escrito para ofrecer una caución que sustituya la medida de aseguramiento acordada, con la cuantía y la forma de prestarla, ante la Sección Civil del Tribunal de Instancia.
- **Caución ofrecida en sustitución de medidas (general)** (`caucion-ofrecida-sustitucion-medidas-general-1054`). Escrito de la parte que ofrece una caución para evitar o sustituir las medidas cautelares solicitadas o acordadas, dirigido a la Sección Civil del Tribunal de Instancia, concretando su clase y su cuantía.
- **Caución prestada por el demandante** (`caucion-prestada-demandante-1110`). Escrito del demandante que presta o ofrece la caución exigida para que se adopte una medida cautelar, indicando su forma y su importe ante la Sección Civil del Tribunal de Instancia que conoce del juicio.
- **Fijación de caución en diligencias preliminares de propiedad horizontal** (`fijacion-caucion-diligencias-preliminares-propiedad-1340`). Escrito dentro de las diligencias preliminares en materia de propiedad horizontal para que el tribunal fije la caución que debe prestar quien las solicita, antes de acordar las diligencias pedidas.
- **Medida cautelar de depósito de cosa mueble con la demanda** (`medida-cautelar-deposito-cosa-mueble-demanda-1106`). Otrosí de la demanda para pedir, como medida cautelar, el depósito de una cosa mueble litigiosa, con o sin audiencia previa de la parte contraria, ante la Sección Civil del Tribunal de Instancia.
- **Pérdida de la caución de diligencias preliminares por no presentar la demanda** (`perdida-caucion-diligencias-preliminares-no-presentar-1400`). Escrito para solicitar que se declare perdida la caución prestada en unas diligencias preliminares porque el solicitante no ha presentado la demanda en plazo, pidiendo su aplicación a los daños y gastos del requerido.
