# Apelación, casación y recursos civiles · España

> Plugin de Claude Code `modelos-recursos-civiles-espana` · **75 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para impugnar resoluciones civiles: recurso de reposición y de revisión, apelación y oposición a la apelación, casación y oposición a la casación, queja y nulidad de actuaciones.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 75 está al final):

- **Demandas, interposiciones y peticiones iniciales** (26). Por ejemplo: Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023); Interposición de casación por infracción procesal en la valoración de la prueba (reforma RDL 5/2023); Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023).
- **Recursos e impugnaciones** (30). Por ejemplo: Recurso de apelación contra la valoración de la prueba testifical; Recurso de apelación en la división de cosa común; Reposición contra la diligencia que señala vista telemática.
- **Contestaciones, oposiciones y alegaciones** (6). Por ejemplo: Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023); Oposición al recurso de apelación en jurisdicción voluntaria; Alegaciones en el incidente de nulidad de actuaciones.
- **Solicitudes y expedientes** (5). Por ejemplo: Nulidad de actuaciones en jurisdicción voluntaria; Certificación de la sentencia para recurrir en casación; Aclaraciones al perito en el juicio o vista.
- **Escritos de trámite** (4). Por ejemplo: Impugnación del recurso de revisión contra decreto en jurisdicción voluntaria; Subsanar la falta de tasa judicial en la apelación; Otrosí de proposición de prueba en apelación.
- **Otros** (4). Por ejemplo: Incidente excepcional de nulidad por defecto de emplazamiento telemático; Reposición oral contra resolución dictada en la comparecencia; Nulidad de actuaciones por vía de recurso.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Recurso de apelación contra una sentencia de desahucio»
   - «Escrito de oposición al recurso de casación»
   - «Recurso de reposición contra la inadmisión de una prueba»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-recursos-civiles-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-recursos-civiles-espana:recurso-apelacion-contra-valoracion-prueba-testifical-22`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 6.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-recursos-civiles-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-recursos-civiles-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

