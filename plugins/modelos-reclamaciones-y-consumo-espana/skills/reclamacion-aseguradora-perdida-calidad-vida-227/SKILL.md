---
name: reclamacion-aseguradora-perdida-calidad-vida-227
description: "Redacta el escrito «Reclamación a la aseguradora por pérdida de calidad de vida» (formulario 227 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamación a la aseguradora por pérdida de calidad de vida

> Formulario 0227 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA
- [ ] Nº (2 veces)
- [ ] MARCA/MODELO (2 veces)
- [ ] DESCRIBIR
- [ ] MATRÍCULA
- [ ] IMPORTE (6 veces)
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A la atención de: Compañía de Seguros»; «…Póliza de seguro: Vehículo»; «…a las [Nº] horas»; «…a las [Nº] horas [COMPLETAR] en»; «…, matrícula de titularidad»; «…, asegurado en»; «…a del automóvil cubierta por la Compañía»; «…con nº [Nº] de póliza»; «…o se me causaron las siguientes lesiones»; «…y secuelas»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 50/1980

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, MASC si es una demanda civil).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0227 · Reclamación a la aseguradora por pérdida de calidad de vida

- Año del modelo: 2020
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS]

A la atención de:

Compañía de Seguros [COMPLETAR]

Póliza de seguro:

Vehículo [COMPLETAR]

Tomador:

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Muy Sres. Míos:

El día [FECHA] a las [Nº] horas [COMPLETAR] en [COMPLETAR], cuando conducía el vehículo modelo [MARCA/MODELO], matrícula de titularidad [COMPLETAR], asegurado en [COMPLETAR], sufrí un accidente de tráfico consistente en [DESCRIBIR] al colisionar con el vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA] conducido por D./Dña. [NOMBRE Y APELLIDOS], con cobertura de responsabilidad civil obligatoria del automóvil cubierta por la Compañía [COMPLETAR] con nº [Nº] de póliza [COMPLETAR].

El accidente fue causado por D./Dña [NOMBRE Y APELLIDOS] según..

Como consecuencia del mismo se me causaron las siguientes lesiones [COMPLETAR] y secuelas [COMPLETAR]

Por consecuencia de las anteriores lesiones y secuelas, se me causaron los siguientes PERJUICIO MORAL POR PÉRDIDA DE CALIDAD DE VIDA (elegir entre los posibles):

- PERJUICIO MUY GRAVE (es aquél en el que el lesionado pierde su autonomía personal para realizar la casi totalidad de actividades esenciales en el desarrollo de la vida ordinaria): [IMPORTE] euros (tabla 2.B.3; de 107.123,05 hasta 178.538,42 €)

- PERJUICIO GRAVE (es aquél en el que el lesionado pierde su autonomía personal para realizar algunas de las actividades esenciales en el desarrollo de la vida ordinaria o la mayor parte de sus actividades específicas de desarrollo personal. El perjuicio moral por la pérdida de toda posibilidad de realizar una actividad laboral o profesional también se considera perjuicio grave): [IMPORTE] euros (tabla 2.B.3; de 47.610,25 hasta 119.025,61 €)

- PERJUICIO MODERADO: (es aquél en el que el lesionado pierde la posibilidad de llevar a cabo una parte relevante de sus actividades específicas de desarrollo personal. El perjuicio moral por la pérdida de la actividad laboral o profesional que se venía ejerciendo también se considera perjuicio moderado): [IMPORTE] euros (tabla 2.B.3; de 11.902,56 hasta 59.512,81 €)

- PERJUICIO LEVE: (es aquél en el que el lesionado con secuelas de más de seis puntos pierde la posibilidad de llevar a cabo actividades específicas que tengan especial trascendencia en su desarrollo personal. El perjuicio moral por la limitación o pérdida parcial de la actividad laboral o profesional que se venía ejerciendo se considera perjuicio leve con independencia del número de puntos que se otorguen a las secuelas): [IMPORTE] euros (tabla 2.B.3; de 1.785,38 hasta 17.853,84 €).

Además, se solicita indemnización por PERJUICIO MORAL POR PÉRDIDA DE CALIDAD DE VIDA DE FAMILIARES DE GRANDES LESIONADOS: [IMPORTE] euros (tabla 2.B.4; de 35.707,68 hasta 172.587,14 €).

Por todo lo anterior, el importe total de la cuantía indemnizatoria que reclamamos es de [IMPORTE] euros.

Pongo estos hechos en su conocimiento a los efectos previstos en el artículo 7.1 de la Ley de responsabilidad civil y seguro en la circulación de vehículos a motor. Y se comunica que, según el art. 20. 6.º de la Ley 50/1980, de 8 de octubre, Ley del Contrato de Seguro, el deber de comunicar el siniestro por parte del asegurado es el que figura en la póliza, o en su defecto el de 7 días a partir de haberlo conocido, lo que deberá tenerse en cuenta a los efectos del interés por mora del asegurador.

Se adjunta la siguiente documentación:

A la espera de sus noticias, reciba un saludo:
