# Propiedad, posesión, ocupaciones y servidumbres · España

> Plugin de Claude Code `modelos-propiedad-y-posesion-espana` · **15 formularios** · área: Civil · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para defender la propiedad y la posesión: demanda posesoria para retener o recuperar la posesión, suspensión de obra nueva, deslinde, tercería de dominio, retracto, usufructo, servidumbres y la declaración judicial de falta de derecho para ocupar.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 15 está al final):

- **Demandas, interposiciones y peticiones iniciales** (3). Por ejemplo: Demanda posesoria para retener o recuperar la posesión; Demanda de suspensión de obra nueva que pone en peligro la edificación del demandante; Demanda de disolución y liquidación de comunidad de bienes de pareja estable.
- **Contestaciones, oposiciones y alegaciones** (3). Por ejemplo: Oposición al deslinde de fincas no escritas; Contestación a la demanda de tercería de dominio; Oposición a la demanda de retracto.
- **Solicitudes y expedientes** (4). Por ejemplo: Autorización al usufructuario para poner a interés el capital cobrado del crédito vencido; Autorización al usufructuario para reclamar créditos vencidos del usufructo; Inscripción registral de resolución extranjera de jurisdicción voluntaria.
- **Escritos de trámite** (1). Por ejemplo: Oposición del dueño de finca colindante al deslinde antes de la comparecencia.
- **Actos y resoluciones de la Administración o del órgano judicial** (1). Por ejemplo: Notificación de retracto gentilicio (Navarra).
- **Contratos, escrituras y documentos** (1). Por ejemplo: Escritura de usufructo vidual universal recíproco (Galicia).
- **Otros** (2). Por ejemplo: Servidumbre de paso por pacto (Galicia); Consentimiento del propietario a una servidumbre.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Demanda posesoria para recuperar la posesión de una finca»
   - «Oposición al deslinde de una finca»
   - «Contestación a una demanda de tercería de dominio»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-propiedad-y-posesion-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-propiedad-y-posesion-espana:oposicion-deslinde-fincas-no-escritas-157`. Los nombres están en la lista de formularios de abajo.

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

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 1.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-propiedad-y-posesion-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-propiedad-y-posesion-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-propiedad-y-posesion-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-propiedad-y-posesion-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 426 | Demanda de disolución y liquidación de comunidad de bienes de pareja estable | 2008 | `demanda-disolucion-liquidacion-comunidad-bienes-pareja-426` |
| 883 | Demanda posesoria para retener o recuperar la posesión | 2013 | `demanda-posesoria-retener-recuperar-posesion-883` |
| 1150 | Demanda de suspensión de obra nueva que pone en peligro la edificación del demandante | 2013 | `demanda-suspension-obra-nueva-pone-peligro-edificacion-1150` |

### Contestaciones, oposiciones y alegaciones (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 157 | Oposición al deslinde de fincas no escritas | 2021 | `oposicion-deslinde-fincas-no-escritas-157` |
| 178 | Contestación a la demanda de tercería de dominio | 2021 | `contestacion-demanda-terceria-dominio-178` |
| 280 | Oposición a la demanda de retracto | 2020 | `oposicion-demanda-retracto-280` |

### Solicitudes y expedientes (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 701 | Autorización al usufructuario para poner a interés el capital cobrado del crédito vencido | 2015 | `autorizacion-usufructuario-poner-interes-capital-cobrado-701` |
| 708 | Autorización al usufructuario para reclamar créditos vencidos del usufructo | 2015 | `autorizacion-usufructuario-reclamar-creditos-vencidos-708` |
| 739 | Inscripción registral de resolución extranjera de jurisdicción voluntaria | 2015 | `inscripcion-registral-resolucion-extranjera-jurisdiccion-739` |
| 1058 | Declaración judicial de falta de derecho para ocupar | 2013 | `declaracion-judicial-falta-derecho-ocupar-1058` |

### Escritos de trámite (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 709 | Oposición del dueño de finca colindante al deslinde antes de la comparecencia | 2015 | `oposicion-dueno-finca-colindante-deslinde-antes-709` |

### Actos y resoluciones de la Administración o del órgano judicial (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 583 | Notificación de retracto gentilicio (Navarra) | 2016 | `notificacion-retracto-gentilicio-navarra-583` |

### Contratos, escrituras y documentos (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 536 | Escritura de usufructo vidual universal recíproco (Galicia) | 2016 | `escritura-usufructo-vidual-universal-reciproco-galicia-536` |

### Otros (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 546 | Servidumbre de paso por pacto (Galicia) | 2016 | `servidumbre-paso-pacto-galicia-546` |
| 1417 | Consentimiento del propietario a una servidumbre | 2013 | `consentimiento-propietario-servidumbre-1417` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

## Uso interno

Plugin de uso interno. Antes de venderlo o dárselo a alumnos, hay que sustituir los textos por plantillas de redacción propia.
