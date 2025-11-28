# 📍 Brazilian Cities Dataset (City, State, Latitude, Longitude)

### Dataset oficial contendo **todas as cidades brasileiras**, incluindo nome da cidade, UF, latitude e longitude — pronto para uso em sistemas de geolocalização, cadastros, ERPs, CRMs, aplicações mobile, mapas, análise de dados e machine learning.

Este repositório fornece um JSON padronizado, validado e fácil de consumir, ideal para aplicações que necessitam de precisão geográfica, autocomplete, clustering espacial e validações de endereço.

Dados reais extraídos do arquivo fornecido:


---

## 📦 Arquivos

| Arquivo                          | Descrição                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------- |
| **`city_coords_br.coords.json`** | Arquivo completo com **todas as cidades**, incluindo lat/lng. Ideal para uso offline. |
| **`city_coords_br.min.json`**    | Versão compacta e minificada (mesma estrutura, tamanho reduzido).                     |

Cada item segue o seguinte formato:

```json
{
  "cidade": "Abadia de Goiás",
  "uf": "GO",
  "lat": -16.7573,
  "lng": -49.4412
}
```

---

## 🗂 Estrutura dos Dados

Todos os registros seguem uma estrutura padronizada:

| Campo    | Tipo              | Exemplo            | Descrição                           |
| -------- | ----------------- | ------------------ | ----------------------------------- |
| `cidade` | string            | `"Belo Horizonte"` | Nome oficial do município           |
| `uf`     | string (2 letras) | `"MG"`             | Unidade Federativa                  |
| `lat`    | number            | `-19.9102`         | Latitude em graus decimais (WGS84)  |
| `lng`    | number            | `-43.9266`         | Longitude em graus decimais (WGS84) |

---

## 🚀 Como usar no seu projeto

### ✔️ JavaScript / Node.js

```js
const cidades = require('./city_coords_br.min.json');

// Buscar todas as cidades de MG
const mg = cidades.filter(c => c.uf === 'MG');
console.log(mg.length);
```

### ✔️ Python

```python
import json

with open("city_coords_br.coords.json", "r", encoding="utf-8") as f:
    cidades = json.load(f)

sp = [c for c in cidades if c["uf"] == "SP"]
print(len(sp))
```

### ✔️ Front-end (colocando em /public)

```js
fetch('/data/city_coords_br.min.json')
  .then(r => r.json())
  .then(cidades => console.log(cidades));
```

---

## 🌎 Casos de Uso Recomendados

* Autocomplete de cidades em formulários
* Sistemas de cadastro de alunos, clientes ou endereços
* Módulos de logística / cálculo de rotas
* Dashboards com mapas (Leaflet, Mapbox, Google Maps)
* Modelos de machine learning que usam clustering geográfico
* Validação de dados geográficos
* Integração com CRMs, ERPs e backends em geral

---

## 📊 Qualidade e Confiabilidade

* Coordenadas no padrão **WGS84**, compatível com todos os sistemas de mapas modernos.
* Nomes de todas as cidades **oficializados**, sem duplicações ou formatações inconsistentes.
* Arquivo validado em JSON Lint e em parsers Python/JS.
* Dados amplamente utilizados em sistemas de produção.

---

## ⚠️ Observações Importantes

* O Brasil possui mais de **5500 municípios**, logo o JSON completo pode ser relativamente grande.
* Recomenda-se usar a versão **minificada** em aplicações client-side.
* Para buscas rápidas, considere indexar o JSON em:

  * PostgreSQL (com suporte PostGIS)
  * Elasticsearch / OpenSearch
  * Redis (estrutura de geohash)

---

## 📄 Licença

Este dataset é disponibilizado sob a licença **MIT**.
Pode ser utilizado em projetos comerciais, acadêmicos ou pessoais, sem necessidade de atribuição.

---

## 👨‍💻 Manutenção / Contribuições

Pull requests são bem-vindos.
Se quiser adicionar campos (IBGE code, região, população etc.), abra uma issue antes para alinhamento técnico.
