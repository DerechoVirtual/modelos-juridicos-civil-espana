# Herencias: testamentos, partición y legítimas · España

> Plugin de Claude Code `modelos-herencias-espana` · **87 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para herencias: testamentos, declaración de herederos, aceptación y repudiación, partición y cuaderno particional, legítimas, desheredación y las acciones judiciales sobre la herencia.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 87 está al final):

- **Demandas, interposiciones y peticiones iniciales** (30). Por ejemplo: Demanda declarativa de prescripción de los derechos legitimarios; Demanda contra el cuaderno particional del contador-partidor dativo de notaría; Nulidad de la partición hereditaria: demanda.
- **Contestaciones, oposiciones y alegaciones** (7). Por ejemplo: Contestación a la demanda de nulidad de testamento (juicio ordinario); Contestación a la demanda de adición a la partición hereditaria; Oposición a la división judicial de la herencia e intervención del caudal.
- **Solicitudes y expedientes** (19). Por ejemplo: Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación; Requerimiento para aceptar o repudiar la herencia (Aragón); Cese de la intervención judicial de la herencia.
- **Escritos de trámite** (3). Por ejemplo: Sucesión del fiador en la posición procesal del ejecutante; Autorización al acreedor para aceptar la herencia; Jura de cuentas del procurador contra la herencia yacente.
- **Actos y resoluciones de la Administración o del órgano judicial** (2). Por ejemplo: Acta de sorteo del contador-partidor por acuerdo mayoritario (Galicia); Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia).
- **Contratos, escrituras y documentos** (18). Por ejemplo: Designación del delegado de protección de datos en el sector público; Designación del delegado de protección de datos en el sector privado; Testamento en caso de epidemia.
- **Comunicaciones, requerimientos y reclamaciones** (2). Por ejemplo: Honorarios de abogado contra herencia yacente: reclamación; Requerir al contador-partidor.
- **Otros** (6). Por ejemplo: Ineficacia sobrevenida del testamento por premoriencia de los herederos; Revocar conjuntamente el testamento mancomunado correspectivo (Galicia); Revocar unilateralmente el testamento mancomunado correspectivo (Galicia).

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de nulidad de la partición hereditaria»
   - «Demanda contra el cuaderno particional del contador-partidor dativo»
   - «Oposición a la división judicial de la herencia»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-herencias-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-herencias-espana:contestacion-demanda-nulidad-testamento-juicio-ordinario-17`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 7.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-herencias-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-herencias-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

