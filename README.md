# lemmata-links

Curated datasets of Italian lemmas and their structured associations.

---

## Dataset

Every dataset is a JSON object with a `_meta` key containing build metadata, plus one key per entry:

```json
"_meta": {
  "build_date": "2026-04-01T21:07:39+00:00",
  "content_hash": "3435388c9d031467a8528561b6ccecf2fa0d055978e9d331272957e07f3970e9"
}
```

| field | type | description |
| --- | --- | --- |
| `build_date` | string | ISO 8601 UTC timestamp of the last build |
| `content_hash` | string | SHA-256 of the dataset content — changes whenever any entry is updated |

---

### `italian-lemma-emoji.json`

A JSON object mapping Italian lemmas to emoji associations.

```json
{
  "pizza": [
    {
      "char": "🍕",
      "g": 5,
      "gl": "obvious",
      "utf": "U+1F355",
      "utf_compact": "1F355"
    }
  ],
  "acqua termale": [
    {
      "char": "♨️💧",
      "g": 4,
      "gl": "easy",
      "utf": "U+2668 U+FE0F U+1F4A7",
      "utf_compact": "2668-FE0F-1F4A7"
    }
  ],
  "Vincent Van Gogh": [
    {
      "char": "🌻👂",
      "g": 1,
      "gl": "cryptic",
      "utf": "U+1F33B U+1F442",
      "utf_compact": "1F33B-1F442"
    }
  ]
}
```

The root object contains one key per lemma. Each lemma maps to an array of association objects with these fields:

| field | type | description |
| --- | --- | --- |
| `char` | string | Emoji character(s) — single or multi-emoji combination |
| `g` | integer 1–5 | Guessability score |
| `gl` | string | Guessability label |
| `utf` | string | Unicode codepoint(s), space-separated (e.g. `U+1F355`) |
| `utf_compact` | string | Codepoint(s) without `U+` prefix, hyphen-separated (e.g. `1F355`) |

#### Guessability levels

| `g` | `gl` | meaning |
| --- | --- | --- |
| 5 | `obvious` | You see it and say the word instantly |
| 4 | `easy` | One or two seconds, no effort |
| 3 | `medium` | Requires a moment of reasoning |
| 2 | `hard` | Non-obvious association, needs context |
| 1 | `cryptic` | Rebus-style, solvable only by inference |

#### Lemma source

The lemmas in this dataset are a curated subset drawn from [**italian-wordnet-definitions**](https://github.com/linkingtechnologies/italian-wordnet-definitions), an open-licensed JSON dataset mapping Italian lemmas to WordNet synsets with Italian and English definitions (CC BY-SA 4.0).

#### Design principles

- **Guessability first** — an emoji is included only if a human can reasonably infer the lemma from it, with no external knowledge beyond common sense.
- **Minimalism** — at most 3 emoji per lemma, all useful.
- **Multi-emoji combinations** — pairs and triples are used only when they form a natural, readable rebus.

---

### `italian-lemma-numerals.json`

A JSON object mapping Italian numeral lemmas to their definitions and Wikipedia links.

The dataset covers three numeral systems for the range 0–100:

- **Cardinal numbers** — `zero`, `uno`, `due` … `cento`
- **Ordinal numbers** — `primo`, `secondo`, `terzo` … `centesimo`
- **Roman numerals** — `I`, `II`, `III` … `C`

Zero is included as a cardinal only (no ordinal or Roman numeral form in standard use).

```json
{
  "zero": {
    "definition_it": "Numero cardinale che esprime la quantità nulla (Zero). Elemento neutro dell'addizione, precede il uno.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/Zero",
    "wikipedia_en": "https://en.wikipedia.org/wiki/0"
  },
  "uno": {
    "definition_it": "Numero cardinale che esprime la quantità di 1 (Uno). Segue lo zero e precede il due.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/1_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/1"
  },
  "primo": {
    "definition_it": "Numero ordinale che indica la posizione 1 in una serie ordinata (Primo). Occupa la prima posizione assoluta.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/1_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/1"
  },
  "I": {
    "definition_it": "Numero romano che rappresenta il valore 1 (I). Notazione usata nell'antico sistema numerico romano. Primo numero della sequenza, precede II.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/1_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/1"
  },
  "due": {
    "definition_it": "Numero cardinale che esprime la quantità di 2 (Due). Nella sequenza dei numeri naturali, segue il uno e precede il tre.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/2_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/2"
  },
  "secondo": {
    "definition_it": "Numero ordinale che indica la posizione 2 in una serie ordinata (Secondo). Segue il primo e precede il terzo.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/2_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/2"
  },
  "II": {
    "definition_it": "Numero romano che rappresenta il valore 2 (II). Notazione usata nell'antico sistema numerico romano. Segue I e precede III.",
    "wikipedia_it": "https://it.wikipedia.org/wiki/2_(numero)",
    "wikipedia_en": "https://en.wikipedia.org/wiki/2"
  }
}
```

The root object contains one key per lemma. Each lemma maps to an object with these fields:

| field | type | description |
| --- | --- | --- |
| `definition_it` | string | Italian definition of the numeral lemma |
| `wikipedia_it` | string | URL of the Italian Wikipedia page for the number |
| `wikipedia_en` | string | URL of the English Wikipedia page for the number |

---

### `italian-lemma-license-plate-administrative-unit.json`

A JSON object mapping Italian license plate codes to administrative units, enriched with ISTAT, Wikidata, and Wikipedia data.

Each license plate code maps to one or more administrative units.

```json
{
  "AG": [
    {
      "definition_it": "Libero consorzio di comuni di Agrigento",
      "definition_it_source": "ISTAT",
      "istat_province_code": "084",
      "province_name_it": "Agrigento",
      "province_name_it_source": "ISTAT",
      "administrative_unit_type_it": "Libero consorzio di Comuni",
      "administrative_unit_type_code": "4",
      "administrative_unit_type_source": "ISTAT",
      "wikidata_id": "Q16112",
      "wikidata_url": "http://www.wikidata.org/entity/Q16112",
      "wikidata_label_it": "provincia di Agrigento",
      "wikidata_instance_of_it": "libero consorzio comunale della Sicilia",
      "wikidata_instance_of_url": "http://www.wikidata.org/entity/Q21190155",
      "wikipedia_it_url": "https://it.wikipedia.org/wiki/Provincia_di_Agrigento"
    }
  ],
  "AL": [
    {
      "definition_it": "Provincia di Alessandria",
      "definition_it_source": "ISTAT",
      "istat_province_code": "006",
      "province_name_it": "Alessandria",
      "province_name_it_source": "ISTAT",
      "administrative_unit_type_it": "Provincia",
      "administrative_unit_type_code": "1",
      "administrative_unit_type_source": "ISTAT",
      "wikidata_id": "Q15097",
      "wikidata_url": "http://www.wikidata.org/entity/Q15097",
      "wikidata_label_it": "provincia di Alessandria",
      "wikidata_instance_of_it": "provincia d'Italia",
      "wikidata_instance_of_url": "http://www.wikidata.org/entity/Q15089",
      "wikipedia_it_url": "https://it.wikipedia.org/wiki/Provincia_di_Alessandria"
    }
  ]
}
```

The root object contains one key per license plate code. Each code maps to an array of administrative unit objects with these fields:

| field | type | description |
| --- | --- | --- |
| `definition_it` | string | Italian definition of the administrative unit (ISTAT) |
| `definition_it_source` | string | Source of the definition |
| `istat_province_code` | string | ISTAT numeric province code |
| `province_name_it` | string | Italian name of the province |
| `province_name_it_source` | string | Source of the province name |
| `administrative_unit_type_it` | string | Italian label for the administrative unit type |
| `administrative_unit_type_code` | string | ISTAT code for the administrative unit type |
| `administrative_unit_type_source` | string | Source of the administrative unit type |
| `wikidata_id` | string | Wikidata entity ID (e.g. `Q16112`) |
| `wikidata_url` | string | URL of the Wikidata entity |
| `wikidata_label_it` | string | Italian label from Wikidata |
| `wikidata_instance_of_it` | string | Italian label of the `instance of` Wikidata property |
| `wikidata_instance_of_url` | string | URL of the `instance of` Wikidata entity |
| `wikipedia_it_url` | string | URL of the Italian Wikipedia page |

#### Sources

- **ISTAT** — official Italian administrative data (CC BY 4.0)
- **Wikidata** — entity identifiers and labels (CC0)
- **Wikipedia** — links only

---

### `italian-lemma-car-brand.json`

A JSON object mapping Italian lemmas (automobile brand names) to their Wikipedia associations.

```json
{
  "Ferrari": [
    {
      "definition_it": "marchio automobilistico",
      "definition_it_source": "https://github.com/filippofilip95/car-logos-dataset/blob/master/logos/data.json",
      "wikipedia_source": "https://dbpedia.org/sparql",
      "wikipedia_url": "https://it.wikipedia.org/wiki/Ferrari",
      "wikipedia_it": "https://it.wikipedia.org/wiki/Ferrari",
      "wikipedia_en": "https://en.wikipedia.org/wiki/Ferrari"
    }
  ],
  "Fiat": [
    {
      "definition_it": "marchio automobilistico",
      "definition_it_source": "https://github.com/filippofilip95/car-logos-dataset/blob/master/logos/data.json",
      "wikipedia_source": "https://dbpedia.org/sparql",
      "wikipedia_url": "https://it.wikipedia.org/wiki/FIAT",
      "wikipedia_it": "https://it.wikipedia.org/wiki/FIAT",
      "wikipedia_en": "https://en.wikipedia.org/wiki/Fiat"
    }
  ]
}
```

The root object contains one key per lemma. Each lemma maps to an array of association objects with these fields:

| field | type | description |
| --- | --- | --- |
| `definition_it` | string | Italian definition of the lemma |
| `definition_it_source` | string | Source dataset the lemma list is drawn from |
| `wikipedia_source` | string | Endpoint used to resolve Wikipedia links |
| `wikipedia_url` | string \| null | Best available Wikipedia URL (Italian if present, otherwise English) |
| `wikipedia_it` | string \| null | Italian Wikipedia URL, if available |
| `wikipedia_en` | string \| null | English Wikipedia URL, if available |

#### Lemma source

The lemmas are drawn from [**car-logos-dataset**](https://github.com/filippofilip95/car-logos-dataset) by filippofilip95, an open dataset of automobile brand logos. Wikipedia links are resolved via [DBpedia SPARQL](https://dbpedia.org/sparql) across multiple categories (car brands, truck and bus manufacturers, defunct manufacturers, EV manufacturers, and coachbuilders).

---

### `italian-lemma-chemical-symbols.json`

A JSON object mapping chemical element symbols to their Italian definitions and Wikipedia links, sourced from Wikidata.

```json
{
  "Ac": {
    "definition_it": "Ac - Elemento chimico con numero atomico 89",
    "wikipedia_it": "https://it.wikipedia.org/wiki/Attinio",
    "wikipedia_en": "https://en.wikipedia.org/wiki/Actinium"
  },
  "Ag": {
    "definition_it": "elemento chimico con numero atomico 47",
    "wikipedia_it": "https://it.wikipedia.org/wiki/Argento",
    "wikipedia_en": "https://en.wikipedia.org/wiki/Silver"
  },
  "Al": {
    "definition_it": "Al - Elemento chimico con numero atomico 13",
    "wikipedia_it": "https://it.wikipedia.org/wiki/Alluminio",
    "wikipedia_en": "https://en.wikipedia.org/wiki/Aluminium"
  }
}
```

The root object contains one key per chemical symbol. Each symbol maps to an object with these fields:

| field | type | description |
| --- | --- | --- |
| `definition_it` | string | Italian description of the element (from Wikidata) |
| `wikipedia_it` | string \| null | Italian Wikipedia URL, if available |
| `wikipedia_en` | string \| null | English Wikipedia URL, if available |

#### Lemma source

Data is sourced from [Wikidata](https://www.wikidata.org/) via SPARQL, querying all entities classified as chemical elements (`wdt:P31 wd:Q11344`) and retrieving their symbol (`wdt:P246`), Italian description, and Wikipedia links.

---

## License

This repository is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). You are free to use, share, and adapt it for any purpose, provided you give appropriate credit and distribute any derivative work under the same license.

Individual datasets incorporate data from third-party sources with their own terms:

- `italian-lemma-emoji.json` — lemma list derived from [italian-wordnet-definitions](https://github.com/linkingtechnologies/italian-wordnet-definitions) (CC BY-SA 4.0), which inherits attribution requirements from IWN-OMW (CNR-ILC) and MultiWordNet (FBK). See that repository for the full attribution chain.
- `italian-lemma-numerals.json` — original data, no additional attribution required.
- `italian-lemma-license-plate-administrative-unit.json` — enriched with [ISTAT](https://www.istat.it/) administrative data (CC BY 4.0) and [Wikidata](https://www.wikidata.org/) (CC0).
- `italian-lemma-car-brand.json` — lemma list derived from [car-logos-dataset](https://github.com/filippofilip95/car-logos-dataset) by filippofilip95. Wikipedia links resolved via [DBpedia](https://dbpedia.org/) (CC BY-SA 3.0).
- `italian-lemma-chemical-symbols.json` — data sourced from [Wikidata](https://www.wikidata.org/) (CC0).