# aeneid-contabulate

Search Virgil's Aeneid in Latin by token, phrase, and regex across books and individual lines.

## Corpus

- Source: `source_text/phi0690.phi003.perseus-lat2.xml`
- Upstream: [PerseusDL/canonical-latinLit](https://github.com/PerseusDL/canonical-latinLit)
- Edition: J.B. Greenough (Boston: Ginn and Company, 1881)
- 12 books, 9,896 lines

## Build Data

```bash
python3 scripts/build_data.py
```

Outputs:

- `docs/data/plays.json` — books
- `docs/data/chunks.json` — lines
- `docs/data/tokens.json`, `tokens2.json`, `tokens3.json` — ngram indices
- `docs/lines/all_lines.json` — line text for search

## Run Locally

```bash
python3 -m http.server 8770 -d docs
```

Then open [http://localhost:8770](http://localhost:8770).

## Notes

- `docs/CNAME` is set to `aeneid.contabulate.org`.
- The frontend adapts the shared Contabulate UI for a Latin epic with book/line hierarchy.
