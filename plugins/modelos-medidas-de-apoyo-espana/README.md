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

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 5.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-medidas-de-apoyo-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-medidas-de-apoyo-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-medidas-de-apoyo-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-medidas-de-apoyo-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 74 | Demanda de nulidad de compraventa de inmueble sin autorización judicial del tutor o curador | 2023 | `demanda-nulidad-compraventa-inmueble-sin-autorizacion-74` |
| 141 | Demanda de medidas voluntarias de apoyo: autocuratela | 2021 | `demanda-medidas-voluntarias-apoyo-autocuratela-141` |
| 143 | Demanda de medidas judiciales de apoyo a persona con discapacidad: curatela | 2021 | `demanda-medidas-judiciales-apoyo-persona-discapacidad-143` |
| 393 | Sustitución de tutor: demanda | 2019 | `sustitucion-tutor-demanda-393` |
| 855 | Demanda de reintegración de la capacidad | 2013 | `demanda-reintegracion-capacidad-855` |
| 1456 | Demanda de nulidad matrimonial por incapacidad (canon 1095.3) | 2014 | `demanda-nulidad-matrimonial-incapacidad-canon-1095-3-1456` |

### Contestaciones, oposiciones y alegaciones (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 146 | Oposición a la provisión de medidas judiciales de apoyo | 2021 | `oposicion-provision-medidas-judiciales-apoyo-146` |
| 236 | Oposición a la rendición final de cuentas del tutor por fallecimiento del tutelado | 2020 | `oposicion-rendicion-final-cuentas-tutor-fallecimiento-236` |
| 1102 | Contestación a la demanda de medidas judiciales de apoyo a personas con discapacidad | 2013 | `contestacion-demanda-medidas-judiciales-apoyo-personas-1102` |
| 1194 | Contestación a demanda de filiación por defensor judicial del menor | 2014 | `contestacion-demanda-filiacion-defensor-judicial-menor-1194` |

### Solicitudes y expedientes (30)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 47 | Autorización judicial para vender inmuebles de persona con discapacidad (Cataluña) | 2023 | `autorizacion-judicial-vender-inmuebles-persona-47` |
| 113 | Medidas de apoyo con curatela tras suprimirse la patria potestad prorrogada | 2022 | `medidas-apoyo-curatela-tras-suprimirse-patria-potestad-113` |
| 126 | Defensor judicial y autorización para aceptar y adjudicar una herencia | 2022 | `defensor-judicial-autorizacion-aceptar-adjudicar-126` |
| 144 | Aprobación judicial de la partición hecha por un defensor judicial | 2021 | `aprobacion-judicial-particion-hecha-defensor-judicial-144` |
| 145 | Revisión de medidas de capacidad adoptadas antes de la Ley 8/2021: solicitud | 2021 | `revision-medidas-capacidad-adoptadas-antes-ley-8-2021-145` |
| 147 | Jurisdicción voluntaria para medidas judiciales de apoyo: curatela | 2021 | `jurisdiccion-voluntaria-medidas-judiciales-apoyo-147` |
| 148 | Revisión de medidas anteriores a la Ley 8/2021 en proceso de capacidad | 2021 | `revision-medidas-anteriores-ley-8-2021-proceso-capacidad-148` |
| 149 | Medidas por guarda o administración inadecuada de bienes de persona con discapacidad | 2021 | `medidas-guarda-administracion-inadecuada-bienes-persona-149` |
| 150 | Revisión de medidas de apoyo: extinguir la curatela o limitar los actos asistidos | 2021 | `revision-medidas-apoyo-extinguir-curatela-limitar-actos-150` |
| 183 | Gravamen de bienes de menor o persona con apoyos: división de cosa común | 2021 | `gravamen-bienes-menor-persona-apoyos-division-cosa-comun-183` |
| 364 | Defensor judicial como cautelar junto a la demanda de medidas de apoyo | 2019 | `defensor-judicial-como-cautelar-junto-demanda-medidas-364` |
| 377 | Constitución de tutela (art. 213.1º CC) | 2019 | `constitucion-tutela-art-213-1o-cc-377` |
| 392 | Autorización para aceptar una herencia en nombre de persona con discapacidad | 2019 | `autorizacion-aceptar-herencia-nombre-persona-392` |
| 407 | Remoción del tutor | 2018 | `remocion-tutor-407` |
| 474 | Medidas por ejercicio inadecuado de la guarda o administración de bienes (art. 158 CC) | 2017 | `medidas-ejercicio-inadecuado-guarda-administracion-474` |
| 480 | Defensor judicial por conflicto de intereses con un progenitor | 2017 | `defensor-judicial-conflicto-intereses-progenitor-480` |
| 514 | Constitución de tutela (art. 199.2º CC) | 2016 | `constitucion-tutela-art-199-2o-cc-514` |
| 651 | Habilitación de edad y defensor judicial posterior | 2015 | `habilitacion-edad-defensor-judicial-posterior-651` |
| 654 | Autorización para disponer o gravar bienes de persona con discapacidad | 2015 | `autorizacion-disponer-gravar-bienes-persona-discapacidad-654` |
| 738 | Defensor judicial para administrar bienes | 2015 | `defensor-judicial-administrar-bienes-738` |
| 748 | Medidas por ejercicio inadecuado de la guarda o administración de bienes (art. 164 CC) | 2015 | `medidas-ejercicio-inadecuado-guarda-administracion-748` |
| 753 | Autorización de gravamen o extinción de derechos reales de menor o persona con apoyos | 2015 | `autorizacion-gravamen-extincion-derechos-reales-menor-753` |
| 754 | Autorización para enajenar bienes de menores o personas con apoyos | 2015 | `autorizacion-enajenar-bienes-menores-personas-apoyos-754` |
| 755 | Autorización para transigir sobre derechos de menores o personas con apoyos | 2015 | `autorizacion-transigir-sobre-derechos-menores-personas-755` |
| 777 | Defensor judicial por no desempeño de funciones: inicio del expediente | 2015 | `defensor-judicial-no-desempeno-funciones-inicio-777` |
| 781 | Defensor judicial por conflicto de intereses con el curador: inicio del expediente | 2015 | `defensor-judicial-conflicto-intereses-curador-inicio-781` |
| 789 | Autorización judicial para vender bienes de menores o personas con apoyos | 2015 | `autorizacion-judicial-vender-bienes-menores-personas-789` |
| 799 | Autorización judicial para el titular de la patria potestad menor no emancipado | 2015 | `autorizacion-judicial-titular-patria-potestad-menor-no-799` |
| 1052 | Declaración o exhibición de documentos sobre capacidad, representación o legitimación | 2013 | `declaracion-exhibicion-documentos-sobre-capacidad-1052` |
| 1420 | Pedir que se acredite la discapacidad | 2013 | `pedir-acredite-discapacidad-1420` |

### Escritos de trámite (15)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 114 | Rendición de cuentas del tutor nombrado antes de la Ley 8/2021 | 2022 | `rendicion-cuentas-tutor-nombrado-antes-ley-8-2021-114` |
| 117 | Rendición de cuentas del tutor o curador ante el Tribunal | 2022 | `rendicion-cuentas-tutor-curador-ante-tribunal-117` |
| 247 | Excusa para ejercer la tutela (Cataluña) | 2020 | `excusa-ejercer-tutela-cataluna-247` |
| 248 | Excusa para ejercer la tutela: modelo general | 2020 | `excusa-ejercer-tutela-modelo-general-248` |
| 249 | Excusa para ejercer la tutela por causa sobrevenida | 2020 | `excusa-ejercer-tutela-causa-sobrevenida-249` |
| 250 | Excusa sobrevenida para ejercer la tutela y nombramiento de nuevo tutor (Cataluña) | 2020 | `excusa-sobrevenida-ejercer-tutela-nombramiento-nuevo-250` |
| 342 | Exhibición de documentos sobre capacidad o legitimación frente a una comunidad de bienes | 2019 | `exhibicion-documentos-sobre-capacidad-legitimacion-342` |
| 433 | Autorización judicial al curador para demandar en nombre de la persona apoyada | 2018 | `autorizacion-judicial-curador-demandar-nombre-persona-433` |
| 463 | Rendición de cuentas del defensor judicial al concluir su gestión | 2017 | `rendicion-cuentas-defensor-judicial-concluir-gestion-463` |
| 588 | Aprobación judicial de la partición de herencia pedida por el curador | 2016 | `aprobacion-judicial-particion-herencia-pedida-curador-588` |
| 681 | Oposición del tutor o curador a su remoción | 2015 | `oposicion-tutor-curador-remocion-681` |
| 733 | Autorización del tutor o curador para aceptar sin beneficio de inventario o repudiar herencia | 2015 | `autorizacion-tutor-curador-aceptar-sin-beneficio-733` |
| 791 | Informe del guardador de hecho sobre la persona y los bienes del menor o de la persona con apoyos | 2015 | `informe-guardador-hecho-sobre-persona-bienes-menor-791` |
| 793 | Comunicación del defensor judicial de que ha desaparecido la causa de su nombramiento | 2015 | `comunicacion-defensor-judicial-ha-desaparecido-causa-793` |
| 794 | Defensor judicial comunica que los representantes comparecen o acaba la habilitación | 2015 | `defensor-judicial-comunica-representantes-comparecen-794` |

### Contratos, escrituras y documentos (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 294 | Demanda de medidas de apoyo y curador para ciudadana británica residente en España | 2020 | `demanda-medidas-apoyo-curador-ciudadana-britanica-294` |
| 537 | Escritura de autotutela e instrucciones previas (Galicia) | 2016 | `escritura-autotutela-e-instrucciones-previas-galicia-537` |

### Otros (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 986 | Alegación de defecto de capacidad en la audiencia previa | 2013 | `alegacion-defecto-capacidad-audiencia-previa-986` |
| 1304 | Consentimiento del arrendador a obras de persona con discapacidad en la vivienda arrendada | 2013 | `consentimiento-arrendador-obras-persona-discapacidad-1304` |
| 1419 | Discapacidad: acreditación | 2013 | `discapacidad-acreditacion-1419` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

