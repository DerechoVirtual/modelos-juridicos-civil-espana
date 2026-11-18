# Cobrar deudas: monitorio y cambiario · España

> Plugin de Claude Code `modelos-monitorio-espana` · **37 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para el proceso monitorio y el juicio cambiario: petición inicial, oposición del deudor (prescripción, pluspetición, cláusulas abusivas…), impugnación de la oposición y paso al declarativo, y oposición en el juicio cambiario.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 37 está al final):

- **Demandas, interposiciones y peticiones iniciales** (12). Por ejemplo: Petición inicial de monitorio contra la comunidad por honorarios del administrador; Demanda ordinaria contra el propietario tras oposición al monitorio; Oposición por abusividad al juicio cambiario: demanda.
- **Recursos e impugnaciones** (3). Por ejemplo: Impugnación de la oposición al monitorio; Apelación contra el auto que rechaza cláusulas abusivas en el monitorio; Impugnación de la oposición al monitorio por el trámite del verbal.
- **Contestaciones, oposiciones y alegaciones** (10). Por ejemplo: Oposición al monitorio por prescripción de la deuda; Oposición al monitorio por cláusula rebus sic stantibus; Oposición al monitorio por cláusulas abusivas.
- **Solicitudes y expedientes** (4). Por ejemplo: Inicio de expediente de título de crédito: cheque; Monitorio por deuda de alquiler impagado; Monitorio: petición.
- **Escritos de trámite** (5). Por ejemplo: Impugnación de la oposición al monitorio (financiación de vehículo); Petición inicial de monitorio por contrato de financiación de vehículos; Petición inicial de monitorio por contrato de renting.
- **Contratos, escrituras y documentos** (3). Por ejemplo: Modelo normalizado de reclamación monitoria; Modelo normalizado de reclamación monitoria de gastos comunes de comunidad; Monitorio simplificado con documentación mercantil habitual.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Oposición a un monitorio por prescripción de la deuda»
   - «Impugnación de la oposición al monitorio»
   - «Oposición a un juicio cambiario»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-monitorio-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-monitorio-espana:peticion-inicial-monitorio-contra-comunidad-honorarios-49`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 3.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-monitorio-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-monitorio-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

