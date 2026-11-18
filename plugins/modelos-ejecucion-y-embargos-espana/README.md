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

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 11.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-ejecucion-y-embargos-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-ejecucion-y-embargos-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-ejecucion-y-embargos-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-ejecucion-y-embargos-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (37)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 35 | Demanda de gastos no incluidos en la tasación de costas (juicio verbal) | 2024 | `demanda-gastos-no-incluidos-tasacion-costas-juicio-35` |
| 48 | Demanda del propietario para exigir a la comunidad obras de mantenimiento de elementos comunes | 2023 | `demanda-propietario-exigir-comunidad-obras-mantenimiento-48` |
| 97 | Ejecución de sentencia por crédito revolving: demanda | 2022 | `ejecucion-sentencia-credito-revolving-demanda-97` |
| 105 | Demanda verbal por defectos en obras de una vivienda | 2022 | `demanda-verbal-defectos-obras-vivienda-105` |
| 121 | Demanda ejecutiva del decreto que aprueba la tasación de costas | 2022 | `demanda-ejecutiva-decreto-aprueba-tasacion-costas-121` |
| 154 | Demanda ejecutiva de la sentencia de desahucio por precario | 2021 | `demanda-ejecutiva-sentencia-desahucio-precario-154` |
| 159 | Demanda ejecutiva basada en escritura de reconocimiento de deuda | 2021 | `demanda-ejecutiva-basada-escritura-reconocimiento-deuda-159` |
| 160 | Demanda de resolución de contrato de obra por cumplimiento defectuoso | 2021 | `demanda-resolucion-contrato-obra-cumplimiento-defectuoso-160` |
| 164 | Reconocimiento y ejecución de resolución extranjera sin convenio internacional: modelo general | 2021 | `reconocimiento-ejecucion-resolucion-extranjera-sin-164` |
| 252 | Demanda ejecutiva por aval a primer requerimiento (título no judicial) | 2020 | `demanda-ejecutiva-aval-primer-requerimiento-titulo-no-252` |
| 340 | Demanda de ejecución de acuerdos de la junta de propietarios | 2019 | `demanda-ejecucion-acuerdos-junta-propietarios-340` |
| 397 | Ejecución de título judicial extranjero conforme al Reglamento (UE) 1215/2012 | 2019 | `ejecucion-titulo-judicial-extranjero-conforme-reglamento-397` |
| 408 | Ejecución de concesión administrativa: demanda | 2018 | `ejecucion-concesion-administrativa-demanda-408` |
| 473 | Demanda ejecutiva de sentencia de condena con bases de liquidación | 2017 | `demanda-ejecutiva-sentencia-condena-bases-liquidacion-473` |
| 526 | Demanda de ejecución hipotecaria parcial de crédito sindicado | 2016 | `demanda-ejecucion-hipotecaria-parcial-credito-sindicado-526` |
| 593 | Demanda ejecutiva de sentencia firme que anula la cláusula suelo y ordena devolver cantidades | 2016 | `demanda-ejecutiva-sentencia-firme-anula-clausula-suelo-593` |
| 601 | Ejecución contra el sucesor mortis causa del ejecutado: demanda | 2016 | `ejecucion-contra-sucesor-mortis-causa-ejecutado-demanda-601` |
| 620 | Demanda de exequátur para ejecutar resoluciones extranjeras en España | 2016 | `demanda-exequatur-ejecutar-resoluciones-extranjeras-620` |
| 667 | Ejecución del acta notarial de deuda dineraria no contradicha | 2015 | `ejecucion-acta-notarial-deuda-dineraria-no-contradicha-667` |
| 668 | Ejecución de acto de conciliación con avenencia | 2015 | `ejecucion-acto-conciliacion-avenencia-668` |
| 870 | Demanda ejecutiva con ampliación por nuevos plazos (general) | 2013 | `demanda-ejecutiva-ampliacion-nuevos-plazos-general-870` |
| 885 | Demanda ejecutiva con ejecución provisional de sentencia de apelación | 2013 | `demanda-ejecutiva-ejecucion-provisional-sentencia-885` |
| 908 | Demanda ejecutiva ordinaria sin habilitación de fondos | 2013 | `demanda-ejecutiva-ordinaria-sin-habilitacion-fondos-908` |
| 920 | Ejecución de sentencia por impago de pensiones | 2013 | `ejecucion-sentencia-impago-pensiones-920` |
| 937 | Demanda ejecutiva por el saldo de una cuenta | 2013 | `demanda-ejecutiva-saldo-cuenta-937` |
| 945 | Demanda ejecutiva de condena dineraria hasta 2.000 euros | 2013 | `demanda-ejecutiva-condena-dineraria-hasta-2-000-euros-945` |
| 1165 | Demanda ejecutiva hipotecaria contra el deudor y el tercer poseedor | 2015 | `demanda-ejecutiva-hipotecaria-contra-deudor-tercer-1165` |
| 1191 | Apelación contra el auto que desestima la oposición a ejecución hipotecaria por abusividad | 2014 | `apelacion-contra-auto-desestima-oposicion-ejecucion-1191` |
| 1195 | Demanda ejecutiva sobre auto que aprueba una transacción judicial | 2014 | `demanda-ejecutiva-sobre-auto-aprueba-transaccion-1195` |
| 1246 | Ejecución de acuerdo de mediación en propiedad horizontal | 2013 | `ejecucion-acuerdo-mediacion-propiedad-horizontal-1246` |
| 1346 | Demanda ejecutiva derivada de monitorio | 2013 | `demanda-ejecutiva-derivada-monitorio-1346` |
| 1350 | Ejecución de sentencia: demanda | 2013 | `ejecucion-sentencia-demanda-1350` |
| 1358 | Demanda ejecutiva por condena en acción de cesación | 2013 | `demanda-ejecutiva-condena-accion-cesacion-1358` |
| 1359 | Demanda ejecutiva contra la comunidad por condena de hacer no personalísimo | 2013 | `demanda-ejecutiva-contra-comunidad-condena-hacer-no-1359` |
| 1449 | Demanda ordinaria por incumplimiento de contrato de obra (comunidad de propietarios) | 2014 | `demanda-ordinaria-incumplimiento-contrato-obra-comunidad-1449` |
| 1462 | Apelación contra el auto que deniega el despacho de ejecución hipotecaria | 2014 | `apelacion-contra-auto-deniega-despacho-ejecucion-1462` |
| 1465 | Apelación contra el auto que deniega el despacho de ejecución | 2014 | `apelacion-contra-auto-deniega-despacho-ejecucion-1465` |

### Recursos e impugnaciones (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 107 | Reposición contra el decreto que aplaza un lanzamiento | 2022 | `reposicion-contra-decreto-aplaza-lanzamiento-107` |
| 194 | Recurso de revisión directo contra el decreto que resuelve la impugnación de tasación de costas | 2021 | `recurso-revision-directo-contra-decreto-resuelve-194` |
| 832 | Apelación contra el auto de sobreseimiento de la ejecución por cláusula abusiva | 2013 | `apelacion-contra-auto-sobreseimiento-ejecucion-clausula-832` |
| 914 | Impugnación de la tasación de costas por partidas excesivas o superfluas | 2013 | `impugnacion-tasacion-costas-partidas-excesivas-914` |
| 1057 | Impugnar la tasación de costas como parte solicitante | 2013 | `impugnar-tasacion-costas-como-parte-solicitante-1057` |
| 1464 | Recurso de revisión directo contra decreto del LAJ con medidas ejecutivas | 2014 | `recurso-revision-directo-contra-decreto-laj-medidas-1464` |

### Contestaciones, oposiciones y alegaciones (14)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 24 | Alegaciones a la propuesta de requerimiento de pago por cláusulas abusivas | 2024 | `alegaciones-propuesta-requerimiento-pago-clausulas-24` |
| 57 | Alegaciones sobre suspensión del lanzamiento de vivienda habitual de colectivos vulnerables | 2023 | `alegaciones-sobre-suspension-lanzamiento-vivienda-57` |
| 119 | Oposición del arrendador a suspender el desahucio y lanzamiento (art. 1 RDL 11/2020) | 2022 | `oposicion-arrendador-suspender-desahucio-lanzamiento-art-119` |
| 244 | Oposición a la demanda de reconocimiento y ejecución de resolución extranjera | 2020 | `oposicion-demanda-reconocimiento-ejecucion-resolucion-244` |
| 268 | Oposición a la ejecución hipotecaria por abusividad del interés IRPH | 2020 | `oposicion-ejecucion-hipotecaria-abusividad-interes-irph-268` |
| 515 | Oposición a la ejecución del fiador solidario o avalista | 2016 | `oposicion-ejecucion-fiador-solidario-avalista-515` |
| 652 | Oposición a ejecutar un acta notarial de deudas dinerarias no contradichas | 2015 | `oposicion-ejecutar-acta-notarial-deudas-dinerarias-no-652` |
| 938 | Oposición a la suspensión por prejudicialidad penal en la ejecución de sentencia | 2013 | `oposicion-suspension-prejudicialidad-penal-ejecucion-938` |
| 946 | Oposición a la ejecución provisional de sentencia (general) | 2013 | `oposicion-ejecucion-provisional-sentencia-general-946` |
| 947 | Oposición a la ejecución de título no judicial | 2013 | `oposicion-ejecucion-titulo-no-judicial-947` |
| 948 | Oposición a ejecutar resoluciones procesales o arbitrales | 2013 | `oposicion-ejecutar-resoluciones-procesales-arbitrales-948` |
| 1044 | Oponerse a actuaciones ejecutivas concretas en condena dineraria: modelo general | 2013 | `oponerse-actuaciones-ejecutivas-concretas-condena-1044` |
| 1510 | Oposición a la ejecución de auto que homologa un acuerdo de mediación | 2014 | `oposicion-ejecucion-auto-homologa-acuerdo-mediacion-1510` |
| 1511 | Oposición a la ejecución de un acuerdo de mediación | 2014 | `oposicion-ejecucion-acuerdo-mediacion-1511` |

### Solicitudes y expedientes (37)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 58 | Suspensión del lanzamiento de vivienda habitual (Ley 12/2023, derecho a la vivienda) | 2023 | `suspension-lanzamiento-vivienda-habitual-ley-12-2023-58` |
| 123 | Inmovilización y subasta de un vehículo embargado | 2022 | `inmovilizacion-subasta-vehiculo-embargado-123` |
| 165 | Enervar el embargo con aval bancario en el declarativo tras oposición a monitorio | 2021 | `enervar-embargo-aval-bancario-declarativo-tras-oposicion-165` |
| 195 | Suspensión del lanzamiento arrendaticio de vulnerables sin alternativa (art. 1 RDL 11/2020) | 2021 | `suspension-lanzamiento-arrendaticio-vulnerables-sin-195` |
| 197 | Suspensión de lanzamiento (precario, tutela sumaria, derechos reales): art. 1 bis RDL 11/2020 | 2021 | `suspension-lanzamiento-precario-tutela-sumaria-derechos-197` |
| 204 | Homologación judicial de transacción en ejecución de sentencia | 2020 | `homologacion-judicial-transaccion-ejecucion-sentencia-204` |
| 246 | Administración judicial de empresa embargada | 2020 | `administracion-judicial-empresa-embargada-246` |
| 256 | Homologación judicial de acuerdo de mediación en ejecución | 2020 | `homologacion-judicial-acuerdo-mediacion-ejecucion-256` |
| 355 | Alzamiento de la suspensión del lanzamiento tras un mes del aviso de servicios sociales | 2019 | `alzamiento-suspension-lanzamiento-tras-mes-aviso-355` |
| 357 | Sobreseimiento de ejecución hipotecaria por vencimiento anticipado abusivo (STJUE 26-3-2019) | 2019 | `sobreseimiento-ejecucion-hipotecaria-vencimiento-357` |
| 386 | Nulidad de embargo indeterminado | 2019 | `nulidad-embargo-indeterminado-386` |
| 418 | Nulidad de actuaciones en proceso de ejecución | 2018 | `nulidad-actuaciones-proceso-ejecucion-418` |
| 437 | Embargo de intereses, rentas o frutos | 2018 | `embargo-intereses-rentas-frutos-437` |
| 483 | Subasta voluntaria de bien en proindiviso | 2017 | `subasta-voluntaria-bien-proindiviso-483` |
| 493 | Impulso procesal en el proceso ejecutivo | 2017 | `impulso-procesal-proceso-ejecutivo-493` |
| 622 | Subasta voluntaria: solicitud | 2016 | `subasta-voluntaria-solicitud-622` |
| 780 | Ejecución de la resolución firme que cierra el expediente de jurisdicción voluntaria | 2015 | `ejecucion-resolucion-firme-cierra-expediente-780` |
| 796 | Mandamiento a registro público para inscribir la resolución final del expediente | 2015 | `mandamiento-registro-publico-inscribir-resolucion-final-796` |
| 904 | Modificación del embargo a instancia del ejecutante | 2013 | `modificacion-embargo-instancia-ejecutante-904` |
| 907 | Requerimiento al ejecutado para que presente sus títulos | 2013 | `requerimiento-ejecutado-presente-titulos-907` |
| 911 | Tasación de costas: solicitud | 2013 | `tasacion-costas-solicitud-911` |
| 924 | Testimonio de haber instado la ejecución y certificado de imposibilidad de llevarla a cabo | 2013 | `testimonio-haber-instado-ejecucion-certificado-924` |
| 936 | Conversión de la ejecución provisional en definitiva | 2013 | `conversion-ejecucion-provisional-definitiva-936` |
| 939 | Suspensión por prejudicialidad penal en ejecución de sentencia (falsedad del título) | 2013 | `suspension-prejudicialidad-penal-ejecucion-sentencia-939` |
| 943 | Apremios para garantizar la entrega de cosa determinada | 2013 | `apremios-garantizar-entrega-cosa-determinada-943` |
| 963 | Suspensión de la ejecución del acuerdo impugnado | 2013 | `suspension-ejecucion-acuerdo-impugnado-963` |
| 1050 | Liquidación de daños y perjuicios por obras prohibidas en sentencia | 2013 | `liquidacion-danos-perjuicios-obras-prohibidas-sentencia-1050` |
| 1055 | Interrogatorio del ejecutado condenado a entregar cosa determinada | 2013 | `interrogatorio-ejecutado-condenado-entregar-cosa-1055` |
| 1059 | Mandamiento de cancelación de embargo | 2013 | `mandamiento-cancelacion-embargo-1059` |
| 1060 | Medidas de garantía en ejecución no dineraria | 2013 | `medidas-garantia-ejecucion-no-dineraria-1060` |
| 1199 | Embargo preventivo de buque (convenio de 12 de marzo de 1999) | 2014 | `embargo-preventivo-buque-convenio-12-marzo-1999-1199` |
| 1338 | Otrosí: suspensión de la ejecución del acuerdo impugnado | 2013 | `otrosi-suspension-ejecucion-acuerdo-impugnado-1338` |
| 1351 | Embargo preventivo: solicitud | 2013 | `embargo-preventivo-solicitud-1351` |
| 1431 | Comunero pide acceder a instalación de mejora energética ya ejecutada | 2013 | `comunero-pide-acceder-instalacion-mejora-energetica-ya-1431` |
| 1488 | Alzamiento de suspensión de ejecución tras desestimar la anulación del laudo, con indemnización | 2014 | `alzamiento-suspension-ejecucion-tras-desestimar-1488` |
| 1493 | Suspensión del lanzamiento de vivienda habitual de colectivos vulnerables | 2014 | `suspension-lanzamiento-vivienda-habitual-colectivos-1493` |
| 1496 | Prórroga de anotación preventiva de embargo | 2014 | `prorroga-anotacion-preventiva-embargo-1496` |

### Escritos de trámite (19)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 124 | Impugnación por el ejecutante de la oposición a la ejecución de título judicial | 2022 | `impugnacion-ejecutante-oposicion-ejecucion-titulo-124` |
| 158 | Impugnación de la oposición a la ejecución en familia por motivos de fondo | 2021 | `impugnacion-oposicion-ejecucion-familia-motivos-fondo-158` |
| 260 | Comunicar nuevo domicilio del deudor y pedir requerimiento de pago por auxilio judicial | 2020 | `comunicar-nuevo-domicilio-deudor-pedir-requerimiento-260` |
| 334 | Impago tras el requerimiento y petición de decreto que ponga fin al desahucio | 2019 | `impago-tras-requerimiento-peticion-decreto-ponga-fin-334` |
| 362 | Oposición extraordinaria a la ejecución hipotecaria: cláusula abusiva sobre la cantidad exigible | 2019 | `oposicion-extraordinaria-ejecucion-hipotecaria-clausula-362` |
| 363 | Oposición extraordinaria a la ejecución hipotecaria: cláusula abusiva que fundamenta la ejecución | 2019 | `oposicion-extraordinaria-ejecucion-hipotecaria-clausula-363` |
| 419 | Denuncia por el ejecutado de infracciones en los actos de la ejecución | 2018 | `denuncia-ejecutado-infracciones-actos-ejecucion-419` |
| 482 | Aprobación del remate pedida por el solicitante de la subasta | 2017 | `aprobacion-remate-pedida-solicitante-subasta-482` |
| 484 | Sobreseimiento del expediente pedido por el solicitante de la subasta | 2017 | `sobreseimiento-expediente-pedido-solicitante-subasta-484` |
| 683 | Personación del tercer poseedor de inmueble en la ejecución | 2015 | `personacion-tercer-poseedor-inmueble-ejecucion-683` |
| 713 | Notificar la ejecución al ocupante del inmueble embargado por el procurador | 2015 | `notificar-ejecucion-ocupante-inmueble-embargado-713` |
| 714 | Inspección del inmueble subastado pedida por un licitador | 2015 | `inspeccion-inmueble-subastado-pedida-licitador-714` |
| 923 | Otrosí: acreditación de pago en arrendamientos con lanzamiento | 2013 | `otrosi-acreditacion-pago-arrendamientos-lanzamiento-923` |
| 935 | Otrosí: suspensión de la ejecución de sentencia | 2013 | `otrosi-suspension-ejecucion-sentencia-935` |
| 957 | Otrosí: suspensión de la ejecución en el incidente de nulidad | 2013 | `otrosi-suspension-ejecucion-incidente-nulidad-957` |
| 1047 | Otrosí: caución del ejecutante en condena no dineraria | 2013 | `otrosi-caucion-ejecutante-condena-no-dineraria-1047` |
| 1130 | Desistimiento del ejecutante en la ejecución provisional | 2013 | `desistimiento-ejecutante-ejecucion-provisional-1130` |
| 1157 | Otrosí: ampliación de la ejecución | 2013 | `otrosi-ampliacion-ejecucion-1157` |
| 1159 | Mandamiento al Registro de la Propiedad por extinción de la hipoteca (pago) | 2015 | `mandamiento-registro-propiedad-extincion-hipoteca-pago-1159` |

### Actos y resoluciones de la Administración o del órgano judicial (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 67 | Requerimiento al inquilino para pagar el IBI | 2023 | `requerimiento-inquilino-pagar-ibi-67` |
| 241 | Resolución de contrato de obra por mutuo acuerdo | 2020 | `resolucion-contrato-obra-mutuo-acuerdo-241` |
| 551 | Requerimiento de pago de gastos generales en propiedad horizontal | 2016 | `requerimiento-pago-gastos-generales-propiedad-horizontal-551` |
| 552 | Requerimiento para pagar servicios individuales | 2016 | `requerimiento-pagar-servicios-individuales-552` |
| 1509 | Acuerdo de mediación alcanzado en ejecución de sentencia | 2014 | `acuerdo-mediacion-alcanzado-ejecucion-sentencia-1509` |

### Contratos, escrituras y documentos (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 116 | Pacto de ejecución y cumplimiento de un contrato de mandato | 2022 | `pacto-ejecucion-cumplimiento-contrato-mandato-116` |
| 257 | Burofax de requerimiento de pago en arrendamiento de industria | 2020 | `burofax-requerimiento-pago-arrendamiento-industria-257` |

### Comunicaciones, requerimientos y reclamaciones (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1355 | Aviso al tribunal de entrega de la finca antes del lanzamiento, con la sentencia cumplida | 2013 | `aviso-tribunal-entrega-finca-antes-lanzamiento-sentencia-1355` |

### Otros (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 299 | Vulnerabilidad del arrendador frente a la suspensión del lanzamiento (art. 1.4 RDL 11/2020) | 2020 | `vulnerabilidad-arrendador-frente-suspension-lanzamiento-299` |
| 638 | Testimonio del decreto de aprobación de remate para constituir hipoteca | 2015 | `testimonio-decreto-aprobacion-remate-constituir-hipoteca-638` |
| 664 | Oposición del deudor al requerimiento en reclamación notarial de deudas dinerarias | 2015 | `oposicion-deudor-requerimiento-reclamacion-notarial-664` |
| 850 | Declaración responsable de especial vulnerabilidad contra el lanzamiento | 2013 | `declaracion-responsable-especial-vulnerabilidad-contra-850` |
| 905 | Postura por escrito en subasta | 2013 | `postura-escrito-subasta-905` |
| 942 | Caución ofrecida en sustitución del embargo | 2013 | `caucion-ofrecida-sustitucion-embargo-942` |
| 1330 | Enervar el embargo preventivo | 2013 | `enervar-embargo-preventivo-1330` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

