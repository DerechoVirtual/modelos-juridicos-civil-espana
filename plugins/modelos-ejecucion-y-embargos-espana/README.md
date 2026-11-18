# Ejecutar sentencias: embargos, subastas e hipotecaria · España

> Plugin de Claude Code `modelos-ejecucion-y-embargos-espana` · **128 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para hacer cumplir sentencias y títulos: demanda ejecutiva, ejecución hipotecaria, oposición a la ejecución (también por cláusulas abusivas), embargos, subasta, tasación de costas y liquidación de intereses.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 128 está al final):

- **Demandas, interposiciones y peticiones iniciales** (37). Por ejemplo: Demanda de gastos no incluidos en la tasación de costas (juicio verbal); Demanda del propietario para exigir a la comunidad obras de mantenimiento de elementos comunes; Ejecución de sentencia por crédito revolving: demanda.
- **Recursos e impugnaciones** (6). Por ejemplo: Reposición contra el decreto que aplaza un lanzamiento; Recurso de revisión directo contra el decreto que resuelve la impugnación de tasación de costas; Recurso de revisión directo contra decreto del LAJ con medidas ejecutivas.
- **Contestaciones, oposiciones y alegaciones** (14). Por ejemplo: Alegaciones a la propuesta de requerimiento de pago por cláusulas abusivas; Alegaciones sobre suspensión del lanzamiento de vivienda habitual de colectivos vulnerables; Oposición del arrendador a suspender el desahucio y lanzamiento (art. 1 RDL 11/2020).
- **Solicitudes y expedientes** (37). Por ejemplo: Suspensión del lanzamiento de vivienda habitual (Ley 12/2023, derecho a la vivienda); Inmovilización y subasta de un vehículo embargado; Enervar el embargo con aval bancario en el declarativo tras oposición a monitorio.
- **Escritos de trámite** (19). Por ejemplo: Impugnación por el ejecutante de la oposición a la ejecución de título judicial; Impugnación de la oposición a la ejecución en familia por motivos de fondo; Comunicar nuevo domicilio del deudor y pedir requerimiento de pago por auxilio judicial.
- **Actos y resoluciones de la Administración o del órgano judicial** (5). Por ejemplo: Requerimiento al inquilino para pagar el IBI; Resolución de contrato de obra por mutuo acuerdo; Requerimiento de pago de gastos generales en propiedad horizontal.
- **Contratos, escrituras y documentos** (2). Por ejemplo: Pacto de ejecución y cumplimiento de un contrato de mandato; Burofax de requerimiento de pago en arrendamiento de industria.
- **Comunicaciones, requerimientos y reclamaciones** (1). Por ejemplo: Aviso al tribunal de entrega de la finca antes del lanzamiento, con la sentencia cumplida.
- **Otros** (7). Por ejemplo: Vulnerabilidad del arrendador frente a la suspensión del lanzamiento (art. 1.4 RDL 11/2020); Testimonio del decreto de aprobación de remate para constituir hipoteca; Oposición del deudor al requerimiento en reclamación notarial de deudas dinerarias.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda ejecutiva de una sentencia de condena dineraria»
   - «Oposición a la ejecución hipotecaria por una cláusula abusiva»
   - «Solicitud de embargo preventivo»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-ejecucion-y-embargos-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-ejecucion-y-embargos-espana:alegaciones-propuesta-requerimiento-pago-clausulas-24`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 11.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-ejecucion-y-embargos-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-ejecucion-y-embargos-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

