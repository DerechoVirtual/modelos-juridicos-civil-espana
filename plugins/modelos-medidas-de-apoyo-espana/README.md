# Curatela y medidas de apoyo (Ley 8/2021) · España

> Plugin de Claude Code `modelos-medidas-de-apoyo-espana` · **60 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para el sistema de apoyos a las personas con discapacidad de la Ley 8/2021: curatela y autocuratela, medidas voluntarias de apoyo, guarda de hecho, defensor judicial, y revisión de las medidas acordadas antes de la reforma.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 60 está al final):

- **Demandas, interposiciones y peticiones iniciales** (6). Por ejemplo: Demanda de nulidad de compraventa de inmueble sin autorización judicial del tutor o curador; Demanda de medidas voluntarias de apoyo: autocuratela; Demanda de medidas judiciales de apoyo a persona con discapacidad: curatela.
- **Contestaciones, oposiciones y alegaciones** (4). Por ejemplo: Oposición a la provisión de medidas judiciales de apoyo; Oposición a la rendición final de cuentas del tutor por fallecimiento del tutelado; Contestación a demanda de filiación por defensor judicial del menor.
- **Solicitudes y expedientes** (30). Por ejemplo: Autorización judicial para vender inmuebles de persona con discapacidad (Cataluña); Medidas de apoyo con curatela tras suprimirse la patria potestad prorrogada; Defensor judicial y autorización para aceptar y adjudicar una herencia.
- **Escritos de trámite** (15). Por ejemplo: Rendición de cuentas del tutor nombrado antes de la Ley 8/2021; Rendición de cuentas del tutor o curador ante el Tribunal; Excusa para ejercer la tutela (Cataluña).
- **Contratos, escrituras y documentos** (2). Por ejemplo: Demanda de medidas de apoyo y curador para ciudadana británica residente en España; Escritura de autotutela e instrucciones previas (Galicia).
- **Otros** (3). Por ejemplo: Alegación de defecto de capacidad en la audiencia previa; Consentimiento del arrendador a obras de persona con discapacidad en la vivienda arrendada; Discapacidad: acreditación.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda de medidas judiciales de apoyo: curatela»
   - «Solicitud de revisión de las medidas de capacidad adoptadas antes de la Ley 8/2021»
   - «Nombramiento de defensor judicial por conflicto de intereses con un progenitor»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-medidas-de-apoyo-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-medidas-de-apoyo-espana:autorizacion-judicial-vender-inmuebles-persona-47`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 5.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-medidas-de-apoyo-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-medidas-de-apoyo-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

