# Alquileres y desahucios (reforma 2026) · España

> Plugin de Claude Code `modelos-alquiler-y-desahucio-espana` · **187 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para los conflictos de alquiler (LAU, con las reformas de la Ley 12/2023 y del RDL 29/2026): desahucio por impago, por expiración del plazo o por precario (también contra grandes tenedores), reclamación de rentas y de la fianza, prórrogas, desistimiento del inquilino y determinación de la renta, además de arrendamientos de local, de temporada y rústicos.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 187 está al final):

- **Demandas, interposiciones y peticiones iniciales** (42). Por ejemplo: Desahucio por precario del gran tenedor (adaptada a la Ley 12/2023); Desahucio y rentas del gran tenedor sin enervación (adaptada a la Ley 12/2023); Desahucio por expiración del plazo del gran tenedor (adaptada a la Ley 12/2023).
- **Contestaciones, oposiciones y alegaciones** (23). Por ejemplo: Alegaciones del arrendador gran tenedor en el incidente de suspensión del arrendatario; Contestación a la demanda de desahucio por precario; Contestación a la demanda por daños en la vivienda arrendada tras el arrendamiento.
- **Solicitudes y expedientes** (16). Por ejemplo: Solicitud de prórroga extraordinaria del arrendamiento (Ley 12/2023); Moratoria automática de renta en uso distinto de vivienda (arts. 1 y 2 RDL 35/2020); Suspensión del desahucio de vulnerables sin alternativa habitacional (art. 1 RDL 11/2020).
- **Escritos de trámite** (4). Por ejemplo: Desistir el arrendatario en contratos prorrogados; Propuesta de prueba en juicio verbal de desahucio por impago; Propuesta de prueba en juicio de reclamación de rentas.
- **Actos y resoluciones de la Administración o del órgano judicial** (14). Por ejemplo: Acuerdo de moratoria y pago de renta con cargo a la fianza en local de negocio; Desistimiento del arrendatario en arrendamiento de uso distinto del de vivienda; Acuerdo de extinción del arrendamiento con arrendatario persona jurídica.
- **Contratos, escrituras y documentos** (28). Por ejemplo: Cláusula de no vulnerabilidad económica del arrendatario; Arrendamiento de servicios de administración de fincas en propiedad vertical; Arrendamiento de derechos de caza.
- **Comunicaciones, requerimientos y reclamaciones** (37). Por ejemplo: Requerimiento al fiador o avalista del arrendamiento por incumplimiento del arrendatario; Entrega de llaves con desacuerdo en arrendamiento de uso distinto de vivienda; Aviso del arrendador a persona jurídica: extinción a los veinte años (actividad no comercial).
- **Otros** (23). Por ejemplo: Negativa del arrendador no gran tenedor a la prórroga extraordinaria (Ley 12/2023); Declaración responsable del arrendatario para la moratoria del RDL 35/2020; Prórroga del arrendamiento de vivienda.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de desahucio por impago con reclamación de rentas»
   - «Demanda de devolución de la fianza»
   - «Solicitud del inquilino de prórroga extraordinaria del contrato (Ley 12/2023)»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-alquiler-y-desahucio-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-alquiler-y-desahucio-espana:alegaciones-arrendador-gran-tenedor-incidente-suspension-23`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 17.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-alquiler-y-desahucio-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-alquiler-y-desahucio-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

