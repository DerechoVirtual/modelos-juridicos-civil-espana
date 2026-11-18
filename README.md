# Modelos jurídicos de España para Claude · Civil

13 plugins de modelos de escritos de Civil, uno por tema. Cada modelo es una skill que Claude rellena paso a paso con los datos del caso: 1533 skills en total, más una skill `indice` por plugin para encontrar el modelo adecuado.

Todas las skills trabajan con **Jurisprudenciator** (https://jurisprudenciator.lexiaipro.org): antes de redactar comprueban que el conector responde, verifican en fuentes oficiales los artículos y la jurisprudencia que se citan y revisan el escrito con `verificar_escrito` antes de entregarlo. Sin Jurisprudenciator conectado, las skills no redactan.

Las demás jurisdicciones están en repositorios propios: [Administrativo](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana), [Laboral](https://github.com/DerechoVirtual/modelos-juridicos-laboral-espana), [Penal](https://github.com/DerechoVirtual/modelos-juridicos-penal-espana).

## Instalación

En Claude Code:

```
/plugin marketplace add DerechoVirtual/modelos-juridicos-civil-espana
/plugin install modelos-alquiler-y-desahucio-espana@modelos-juridicos-civil-espana
```

Cada plugin ocupa contexto en la conversación, así que conviene instalar solo los de los temas con los que se trabaja.

En Claude (web y escritorio) también se puede subir cada plugin como ZIP desde **Personalizar → Plugins**. Los ZIP están en la página de [versiones](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest): uno por plugin y [Civil.zip](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/Civil.zip) con todos.

## Plugins

| Plugin | Contenido | Skills | ZIP |
|---|---|---:|---|
| `modelos-alquiler-y-desahucio-espana` | Alquileres y desahucios (reforma 2026) · España | 188 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-alquiler-y-desahucio-espana.zip) |
| `modelos-comunidad-de-propietarios-espana` | Comunidades de propietarios: juntas, acuerdos y morosos · España | 79 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-comunidad-de-propietarios-espana.zip) |
| `modelos-divorcio-y-familia-espana` | Divorcio, custodia y pensiones · España | 217 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-divorcio-y-familia-espana.zip) |
| `modelos-ejecucion-y-embargos-espana` | Ejecutar sentencias: embargos, subastas e hipotecaria · España | 129 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-ejecucion-y-embargos-espana.zip) |
| `modelos-herencias-espana` | Herencias: testamentos, partición y legítimas · España | 88 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-herencias-espana.zip) |
| `modelos-masc-mediacion-y-arbitraje-espana` | MASC obligatorios (LO 1/2025), mediación y arbitraje · España | 92 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-masc-mediacion-y-arbitraje-espana.zip) |
| `modelos-medidas-cautelares-civiles-espana` | Medidas cautelares y diligencias preliminares · España | 21 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-medidas-cautelares-civiles-espana.zip) |
| `modelos-medidas-de-apoyo-espana` | Curatela y medidas de apoyo (Ley 8/2021) · España | 61 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-medidas-de-apoyo-espana.zip) |
| `modelos-monitorio-espana` | Cobrar deudas: monitorio y cambiario · España | 38 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-monitorio-espana.zip) |
| `modelos-proceso-civil-espana` | Escritos del proceso civil (LO 1/2025) · España | 344 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-proceso-civil-espana.zip) |
| `modelos-propiedad-y-posesion-espana` | Propiedad, posesión, ocupaciones y servidumbres · España | 16 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-propiedad-y-posesion-espana.zip) |
| `modelos-reclamaciones-y-consumo-espana` | Reclamaciones: contratos, consumo, seguros y accidentes · España | 184 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-reclamaciones-y-consumo-espana.zip) |
| `modelos-recursos-civiles-espana` | Apelación, casación y recursos civiles · España | 76 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana/releases/latest/download/modelos-recursos-civiles-espana.zip) |

## Estructura

```
.claude-plugin/marketplace.json  catálogo del marketplace
plugins/<plugin>/                .claude-plugin/plugin.json, .mcp.json, skills/, README.md, PRIVACY.md, LICENSE
```

## Aviso

Los escritos que se generan son borradores que debe revisar un abogado; no constituyen asesoramiento jurídico. Las skills no guardan datos del cliente y las consultas a Jurisprudenciator describen el problema jurídico, no los datos personales.

Soporte: https://jurisprudenciator.lexiaipro.org/incidencias · Licencia: ver [LICENSE](LICENSE).
