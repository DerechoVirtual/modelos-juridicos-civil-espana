# Divorcio, custodia y pensiones · España

> Plugin de Claude Code `modelos-divorcio-y-familia-espana` · **216 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para el derecho de familia de principio a fin: separación y divorcio (de mutuo acuerdo o contencioso), convenio regulador, medidas provisionales, custodia y régimen de visitas, pensión de alimentos, filiación, adopción, régimen económico matrimonial y liquidación de gananciales, con especialidades forales (Aragón, Cataluña, Galicia, País Vasco…).

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 216 está al final):

- **Demandas, interposiciones y peticiones iniciales** (80). Por ejemplo: Demanda de ejecución del convenio regulador del matrimonio de mutuo acuerdo; Demanda para pasar de custodia compartida a custodia individual; Demanda de modificación de medidas por falta de ratificación (art. 777.3 LEC).
- **Recursos e impugnaciones** (3). Por ejemplo: Apelación contra la formación de inventario para liquidar gananciales; Apelación contra la sentencia de modificación de medidas; Apelación para obtener la custodia compartida de hijos menores.
- **Contestaciones, oposiciones y alegaciones** (16). Por ejemplo: Contestación al divorcio con reconvención sobre el animal de compañía; Contestación en proceso de menores con guarda compartida y medidas provisionales coetáneas; Contestación a la modificación del uso de la vivienda por convivencia del custodio con un tercero.
- **Solicitudes y expedientes** (54). Por ejemplo: Intervención judicial (art. 156 CC): retirar imágenes en redes de menor de 14 años; Solicitud de los progenitores para revocar el desamparo de un menor; Cambio de la mención registral del sexo en menores de 12 a 13 años, con cambio de nombre.
- **Escritos de trámite** (19). Por ejemplo: Oposición a medidas por menores en riesgo con tutela de la Generalitat (Cataluña); Otrosí de demanda ejecutiva: notificar al cónyuge el embargo de bienes gananciales; Oposición inicial de los progenitores a la declaración de desamparo.
- **Actos y resoluciones de la Administración o del órgano judicial** (6). Por ejemplo: Acuerdo prematrimonial para prever los efectos de una ruptura; Certificado de resolución en materia de regímenes económicos matrimoniales; Certificado de documento público en materia de regímenes económicos matrimoniales.
- **Contratos, escrituras y documentos** (28). Por ejemplo: Convenio de divorcio de mutuo acuerdo con mascota, sin hijos ni bienes (Cataluña); Convenio de divorcio con animal de compañía; Convenio de divorcio de mutuo acuerdo con hijos mayores de edad.
- **Comunicaciones, requerimientos y reclamaciones** (1). Por ejemplo: Reclamación a la aseguradora del cónyuge perjudicado.
- **Otros** (9). Por ejemplo: Plan contradictorio de custodia compartida de un cónyuge; Plan de relaciones familiares (Aragón); Extinción individual de la pareja de hecho (Galicia).

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Convenio regulador con custodia compartida»
   - «Demanda de modificación de medidas para pasar a la custodia compartida»
   - «Ampliar la ejecución por impago de pensiones y embargar bienes»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-divorcio-y-familia-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-divorcio-y-familia-espana:demanda-ejecucion-convenio-regulador-matrimonio-mutuo-19`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 18.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-divorcio-y-familia-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-divorcio-y-familia-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

