---
name: certificacion-obras-aportaciones-individuales-obras-822
description: "Redacta el escrito «Certificación de obras y aportaciones individuales en obras comunes» (formulario 822 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificación de obras y aportaciones individuales en obras comunes

> Formulario 0822 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (7 veces)
- [ ] IMPORTE (10 veces)
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con DNI nº [DNI/NIE], en su calidad de»; «…, nº [NÚMERO], de»; «…, titular de»; «…(la vivienda o el local) situado en»; «…n realizando obras que tienen por objeto»; «…elaborado por el arquitecto»; «…y la adjudicación a la empresa»; «…tiene una cuota de participación de»; «…euros ingresadas entre los meses»; «…y»; «…y [COMPLETAR] de»; «… subvención a la Comunidad concedida por»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 5/2011

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

### Formulario 0822 · Certificación de obras y aportaciones individuales en obras comunes

- Año del modelo: 2015
- Revisión 17-11-2026: 40 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

D./Dña. [NOMBRE Y APELLIDOS], con DNI nº [DNI/NIE], en su calidad de [COMPLETAR] (Secretario, Administrador o Presidente) de la Comunidad de Propietarios de la C/ [CALLE], nº [NÚMERO], de [COMPLETAR], CERTIFICA a favor de D./Dña. [NOMBRE Y APELLIDOS], titular de [COMPLETAR] (la vivienda o el local) situado en [COMPLETAR], y con DNI n.º [DNI/NIE], lo siguiente:

1.º Que en el edificio situado en la C/ [CALLE] nº [NÚMERO], se están realizando obras que tienen por objeto [COMPLETAR] (la reforma integral del edificio, la mejora de la eficiencia energética, la instalación de ascensor, la sustitución de instalaciones de electricidad, de cañerías de suministro de gas, de aislamiento del edificio, de mejora de accesibilidad, …), según proyecto de obra de fecha [FECHA] elaborado por el arquitecto [COMPLETAR], y que cuenta con las oportunas licencias.

2.ºQue las obras han comenzado en fecha [FECHA] Teniendo prevista su conclusión en fecha [FECHA]

3.º Que la ejecución de las obras se acordó en Junta de Propietarios de fecha [FECHA] y la adjudicación a la empresa [COMPLETAR] que las lleva a cabo se acordó en Junta de Propietarios de fecha [FECHA], suscribiendo el oportuno contrato con ella en fecha [FECHA], por un importe total de [IMPORTE] euros más IVA ( euros).

4.º Que D./Dña. [NOMBRE Y APELLIDOS] tiene una cuota de participación de [COMPLETAR] % en el total del edificio y que, en consecuencia contribuya al pago de la indicada obra con [IMPORTE] euros.

Este pago se ha realizado de la siguiente manera:

— Anticipo mediante derramas extraordinarias de [IMPORTE] euros ingresadas entre los meses [COMPLETAR] y [COMPLETAR] de [COMPLETAR] en la cuenta de la Comunidad nº [NÚMERO], a razón de [IMPORTE] Euros/mes, lo que hace un total de [IMPORTE] euros.

— Ingreso de importe final de [IMPORTE] euros en fecha [FECHA], en la misma cuenta.

— (En su caso) Pendiente de abonar mediante derramas extraordinarias hasta el mes de [IMPORTE], [IMPORTE] euros.

— (En su caso) Porcentaje atribuible de la subvención a la Comunidad concedida por [COMPLETAR] para la realización de las obras: [IMPORTE] euros.

— (En su caso) Subvención individual concedida a D./Dña. [NOMBRE Y APELLIDOS] por [COMPLETAR] para la realización de las obras: [IMPORTE] euros.

5.º Que las obras objeto de esta certificación se incluyen dentro de las descritas en el Real Decreto-Ley 5/2011, de 29 de abril, de rehabilitación de viviendas y en el Plan estatal de vivienda y rehabilitación 2009-2012.

Y para que conste y surta los efectos oportunos, suscribe esta certificación: (Administrador, Secretario o Presidente)

========================================================================
