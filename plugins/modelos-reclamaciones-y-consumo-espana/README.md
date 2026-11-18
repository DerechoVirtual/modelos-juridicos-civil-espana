# Reclamaciones: contratos, consumo, seguros y accidentes · España

> Plugin de Claude Code `modelos-reclamaciones-y-consumo-espana` · **183 formularios** · área: Civil (incluye 1 formulario de Procesal, marcado «(Procesal)») · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para reclamaciones civiles y de consumo: incumplimiento de contratos (compraventa, obra, depósito…), cláusulas abusivas, reclamaciones a aseguradoras, accidentes de circulación, responsabilidad civil por daños y la acción de regreso del socio contra la sociedad.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 183 está al final):

- **Demandas, interposiciones y peticiones iniciales** (66). Por ejemplo: Demanda genérica de cantidad en juicio verbal; Demanda de cantidad entre obligados a comunicarse electrónicamente con el tribunal; Demanda de resolución de compraventa de vehículo por falta de conformidad.
- **Recursos e impugnaciones** (1). Por ejemplo: Impugnar la oposición por defectos procesales: modelo general.
- **Contestaciones, oposiciones y alegaciones** (22). Por ejemplo: Contestación a la demanda de cantidad por consumos domésticos de energía; Contestación a demanda de resolución de compraventa (excepción de contrato incumplido); Contestación a demanda de cumplimiento alegando non adimpleti contractus.
- **Solicitudes y expedientes** (12). Por ejemplo: Pedir la exoneración de costas o la moderación de su cuantía; Consignación judicial por reclamación del subcontratista; Conciliación previa para reclamar daños de un accidente de circulación.
- **Escritos de trámite** (11). Por ejemplo: Subsanación de defectos de la solicitud por el promotor; Fianza del perceptor de rendimientos para garantizar su devolución; Daños y perjuicios reclamados por el requerido por no comparecer el solicitante a la conciliación.
- **Actos y resoluciones de la Administración o del órgano judicial** (5). Por ejemplo: Autorización para domiciliar pagos en banco; Informes temporales emitidos por la aseguradora; Resolución por mutuo acuerdo del contrato de prestación de servicios.
- **Contratos, escrituras y documentos** (32). Por ejemplo: Rehabilitación de inmueble: contrato de obras; Cláusula antiinquiokupación; Pacto que declara cumplido un contrato de mandato.
- **Comunicaciones, requerimientos y reclamaciones** (23). Por ejemplo: Reclamación previa por cláusula abusiva en un crédito al consumo; Reclamación a la aseguradora del hermano perjudicado; Reclamación a la aseguradora del nieto perjudicado.
- **Otros** (11). Por ejemplo: Respuesta motivada de la aseguradora que deniega la indemnización; Respuesta motivada de la aseguradora que suspende la indemnización; Pago de la aseguradora del perjudicado por daños causados por un tercero.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda por accidente de circulación contra el conductor, el propietario y la aseguradora»
   - «Demanda para resolver un contrato de obra por incumplimiento del contratista»
   - «Reclamación previa por una cláusula abusiva en un crédito al consumo»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-reclamaciones-y-consumo-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-reclamaciones-y-consumo-espana:pedir-exoneracion-costas-moderacion-cuantia-4`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 17.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-reclamaciones-y-consumo-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-reclamaciones-y-consumo-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

