# Comunidades de propietarios: juntas, acuerdos y morosos · España

> Plugin de Claude Code `modelos-comunidad-de-propietarios-espana` · **78 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para comunidades de propietarios: convocatorias, actas y certificados de la junta, impugnación de acuerdos, acción de cesación de actividades molestas o prohibidas, obras y accesibilidad, cuotas y relaciones con el administrador.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 78 está al final):

- **Demandas, interposiciones y peticiones iniciales** (15). Por ejemplo: Demanda contra la comunidad para obras de accesibilidad: instalación de ascensor; Demanda por obras no autorizadas en la comunidad de propietarios; Demanda verbal contra la comunidad por indemnización al cesar al administrador.
- **Recursos e impugnaciones** (2). Por ejemplo: Impugnación de acuerdo de junta lesivo o perjudicial; Impugnación de acuerdo de junta contrario a la ley o a los estatutos.
- **Contestaciones, oposiciones y alegaciones** (6). Por ejemplo: Contestación a la demanda por alteración de elementos comunes en propiedad horizontal; Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas; Contestación a reclamación de cuotas impagadas por el anterior propietario.
- **Solicitudes y expedientes** (7). Por ejemplo: Prueba pericial anticipada en propiedad horizontal antes del proceso; Permiso para instalaciones provisionales en elementos comunes por obra privativa; Convocatoria de junta solicitada por comuneros al presidente.
- **Escritos de trámite** (5). Por ejemplo: Propietario pide al presidente que requiera a otro el cese de actividades prohibidas; Otrosí: acreditación de pago de cantidades debidas por un comunero; Declinatoria por mediación pactada entre comuneros y comunidad.
- **Actos y resoluciones de la Administración o del órgano judicial** (22). Por ejemplo: Certificado de estar al corriente de pago en la comunidad de propietarios; Certificado del acuerdo de la junta de ejercitar la acción de cesación; Acta que acuerda desafectar elementos comunes para venderlos.
- **Contratos, escrituras y documentos** (6). Por ejemplo: Contrato de la comunidad con instaladora de paneles solares y gestión de la subvención; Cláusula informativa de videovigilancia en comunidades de propietarios; Respuesta de la comunidad al derecho de acceso sobre su videovigilancia.
- **Comunicaciones, requerimientos y reclamaciones** (11). Por ejemplo: Convocatoria de la junta general ordinaria de propietarios (Cataluña); Aviso a la comunidad de obra en vivienda o local; Convocatoria de junta extraordinaria para instalar ascensor.
- **Otros** (4). Por ejemplo: Constitución en comunidad de propietarios de un complejo inmobiliario privado; Comunidad agrupada: estatutos; Constitución en agrupación de comunidades de propietarios.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de impugnación de un acuerdo de la junta contrario a la ley o a los estatutos»
   - «Demanda de cesación de una actividad molesta contra un propietario»
   - «Convocatoria de junta extraordinaria para reclamar cuotas atrasadas»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-comunidad-de-propietarios-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-comunidad-de-propietarios-espana:contestacion-demanda-alteracion-elementos-comunes-5`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 7.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-comunidad-de-propietarios-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-comunidad-de-propietarios-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

