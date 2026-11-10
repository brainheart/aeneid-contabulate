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

## English lookup and glosses

For readers without Latin, a lookup box above the term field finds Latin words by English meaning and inserts them as search terms; the word views add English and Dictionary form columns.

- The data is English Wiktionary (CC BY-SA 3.0 / GFDL) as published by kaikki.org. `source_text/lexicon/wiktionary-extract.json` is the part of that 1.25 GB dictionary this text needs, cut by `kaikki_extract.py` in the contabulate-instances skill and pinned by SHA-256 in `scripts/glossary.py`.
- `scripts/glossary.py` writes `docs/data/glossary.json` during `python3 scripts/build_data.py`. A dictionary cannot disambiguate a spelling in context, so each written form is filed under its likeliest dictionary word and shared spellings are counted (`amb`).
- It is display-only: nothing in it is searched or counted, and the page works without it. `docs/js/glossary.js` is shared verbatim with the other non-English Contabulate instances.
