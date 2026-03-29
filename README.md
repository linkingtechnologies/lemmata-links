# lemmata-links

Curated datasets of Italian lemmas and their structured associations.

---

## Dataset

### `italian-lemma-emoji.json`

A JSON object mapping Italian lemmas to emoji associations.

```json
{
  "_meta": {
    "build_date": "2026-03-28T12:35:17.842880+00:00",
    "content_hash": "aa0f0a57ff9731984e7cc97973a12c8ab2bdd3311196e4b1a687e6f29c27ed5f"
  },
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

The root object contains a `_meta` key with build metadata, plus one key per lemma. Each lemma maps to an array of association objects with these fields:

| field | type | description |
|---|---|---|
| `char` | string | Emoji character(s) — single or multi-emoji combination |
| `g` | integer 1–5 | Guessability score |
| `gl` | string | Guessability label |
| `utf` | string | Unicode codepoint(s), space-separated (e.g. `U+1F355`) |
| `utf_compact` | string | Codepoint(s) without `U+` prefix, hyphen-separated (e.g. `1F355`) |

---

## Guessability levels

| `g` | `gl` | meaning |
|---|---|---|
| 5 | `obvious` | You see it and say the word instantly |
| 4 | `easy` | One or two seconds, no effort |
| 3 | `medium` | Requires a moment of reasoning |
| 2 | `hard` | Non-obvious association, needs context |
| 1 | `cryptic` | Rebus-style, solvable only by inference |

---

## Lemma source

The lemmas in this dataset are a curated subset drawn from [**italian-wordnet-definitions**](https://github.com/linkingtechnologies/italian-wordnet-definitions), an open-licensed JSON dataset mapping Italian lemmas to WordNet synsets with Italian and English definitions (CC BY-SA 4.0).

## Design principles

- **Guessability first** — an emoji is included only if a human can reasonably infer the lemma from it, with no external knowledge beyond common sense.
- **Minimalism** — at most 3 emoji per lemma, all useful.
- **Multi-emoji combinations** — pairs and triples are used only when they form a natural, readable rebus.

---

## Use cases

- Word-guessing and visual quiz games
- Visual lexicon research
- NLP and computational linguistics experiments
- Language learning tools
- Creative and generative applications

---

## License

Data is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). You are free to use, share, and adapt it for any purpose, provided you give appropriate credit and distribute any derivative work under the same license.

The lemma list is derived from [italian-wordnet-definitions](https://github.com/linkingtechnologies/italian-wordnet-definitions), which is itself CC BY-SA 4.0 and inherits attribution requirements from IWN-OMW (CNR-ILC) and MultiWordNet (FBK). See that repository for the full upstream attribution chain.
