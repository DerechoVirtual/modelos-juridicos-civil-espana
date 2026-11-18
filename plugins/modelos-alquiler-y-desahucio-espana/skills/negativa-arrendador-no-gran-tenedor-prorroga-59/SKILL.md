---
name: negativa-arrendador-no-gran-tenedor-prorroga-59
description: "Redacta el escrito «Negativa del arrendador no gran tenedor a la prórroga extraordinaria (Ley 12/2023)» (formulario 59 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Negativa del arrendador no gran tenedor a la prórroga extraordinaria (Ley 12/2023)

> Formulario 0059 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Desde el 8-10-2026 no basta con no ser gran tenedor: en contratos vigentes en esa fecha, la DF 5.ª RDL 29/2026 obliga a cualquier arrendador a aceptar la prórroga de hasta dos años (salvo acuerdo, nuevo contrato o necesidad del art. 9.3) y el art. 10.3 LAU en zona tensionada.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 10.2 de la Ley 29/1994
- art. 10.2 LAU
- art. 3 k) de la Ley 12/2023

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

### Formulario 0059 · Negativa del arrendador no gran tenedor a la prórroga extraordinaria (Ley 12/2023)

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 3 campos de relleno marcados en blanco
- Avisos de la revisión: Desde el 8-10-2026 no basta con no ser gran tenedor: en contratos vigentes en esa fecha, la DF 5.ª RDL 29/2026 obliga a cualquier arrendador a aceptar la prórroga de hasta dos años (salvo acuerdo, nuevo contrato o necesidad del art. 9.3) y el art. 10.3 LAU en zona tensionada.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Negativa del arrendador no gran tenedor a aceptar la prórroga extraordinaria, al amparo del artículo 10.2 de la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos, según la modificación establecida por la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda.

Muy Sr. /Sra. mío/mía:

En relación con la vivienda de mi propiedad, sita en [LOCALIDAD], de la que Usted es arrendatario, según contrato de arrendamiento suscrito en fecha [FECHA], mediante la presente comunicación, a efectos de lo exigido por el art. 10.2 LAU 1994, le informo que concurre causa legal de denegación de la prórroga extraordinaria del contrato de arrendamiento, al no tener esta parte arrendadora la consideración de Gran Tenedor [NOTA DE REVISIÓN: Solo vale frente al art. 10.2 LAU. No frente al art. 10.3 (zona tensionada: obligatoria para cualquier arrendador) ni frente a la DF 5.ª RDL 29/2026 (prórroga de hasta dos años, obligatoria para cualquier arrendador si el inquilino está al corriente y lo ha estado los 8 meses anteriores, salvo acuerdo, nuevo contrato o necesidad del art. 9.3). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 10.2-3; RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755), DF 5.ª.], tal y como prevé el art. 3 k) de la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda.

Sin otro particular reciba un cordial saludo,

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del arrendador
