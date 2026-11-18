# Escritos del proceso civil (LO 1/2025) · España

> Plugin de Claude Code `modelos-proceso-civil-espana` · **343 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para los escritos del proceso civil (LEC y LO 1/2025): demandas y contestaciones, encabezamientos ante las Secciones del Tribunal de Instancia, audiencia previa y vista, proposición de prueba, conclusiones, suspensión, recusación y el resto de escritos de trámite.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 343 está al final):

- **Demandas, interposiciones y peticiones iniciales** (23). Por ejemplo: Demanda en procedimiento testigo; Demanda de condena a una obligación de hacer; Demanda para reconocer la condición de beneficiario de un plan de pensiones y reclamar prestaciones.
- **Recursos e impugnaciones** (10). Por ejemplo: Impugnación por el solicitante de la denegación de justicia gratuita; Impugnar un documento privado aportado por vía telemática; Impugnación del valor probatorio de documento público presentado por vía telemática.
- **Contestaciones, oposiciones y alegaciones** (49). Por ejemplo: Alegaciones del demandante a las excepciones procesales de la contestación (juicio verbal); Alegaciones sobre la prueba propuesta e impugnación de la cuantía (juicio verbal); Contestación y reconvención alegando compensación judicial.
- **Solicitudes y expedientes** (85). Por ejemplo: Proposición de prueba y citación de testigos o peritos a la vista del juicio verbal; Solicitar la celebración de la vista por videoconferencia; Solicitud de amparo al colegio de la abogacía por un letrado.
- **Escritos de trámite** (101). Por ejemplo: Desistimiento del actor y anuncio de extensión de efectos de la sentencia del procedimiento testigo; Solicitud del actor de extensión de efectos de la sentencia del procedimiento testigo; Propuesta comercial de servicios de administración de fincas.
- **Actos y resoluciones de la Administración o del órgano judicial** (18). Por ejemplo: Autorización al inquilino para hacer obras en la vivienda alquilada; Acta de inventario; Diligencia de ordenación que suspende un señalamiento civil por el estado de alarma COVID-19.
- **Contratos, escrituras y documentos** (9). Por ejemplo: Estatutos de sociedad limitada unipersonal de administración de fincas; Estatutos de la comunidad de plazas de garaje; Certificado de destrucción de documentación.
- **Comunicaciones, requerimientos y reclamaciones** (8). Por ejemplo: Comunicación del propietario discrepante de un acuerdo de la junta; Aviso del propietario de plaza de garaje de instalar un punto de recarga eléctrica; Entrega al titular de la vivienda del certificado energético del edificio.
- **Otros** (40). Por ejemplo: No aceptar la oferta motivada de la aseguradora; Aceptar la oferta de la aseguradora; Planteamiento de cuestión prejudicial ante el TJUE.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Minuta de proposición de prueba para la audiencia previa»
   - «Contestación a una demanda de juicio verbal pidiendo vista»
   - «Contestación a la demanda oponiendo la prescripción de la acción»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-proceso-civil-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-proceso-civil-espana:alegaciones-demandante-excepciones-procesales-1`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 30.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-proceso-civil-espana@modelos-juridicos-civil-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
claude plugin install modelos-proceso-civil-espana@modelos-juridicos-civil-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

