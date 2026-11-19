# BICROSS Navigator

Bilingual New Testament manuscripts, parsed and word-aligned, built with [Hexapla](https://github.com/rbturnbull/hexapla).

## Layout

- `bicross-navigator-config.yaml`: the theme, the manuscripts and the alignments between them.
- `theme/`: logo, Bootstrap variables (`variables.scss`), the about page (`about.md`) and the images it shows
  (`assets/`, such as the ERC logo).
- One folder per codex, holding its TEI transcriptions, CoNLL-U parses (mcparser) and alignment links (mcaligner).

Everything about a manuscript (its language, name, shelfmark, GA/VL/Trismegistos numbers, date, description,
transcribers and licence) is in the TEI header of its transcription. The site licence (CC BY-NC-SA 4.0) covers the
parses and alignments, and any transcription whose TEI header does not give its own licence.

## Building

```bash
pip install git+https://github.com/rbturnbull/hexapla
hexapla validate bicross-navigator-config.yaml
hexapla build bicross-navigator-config.yaml --output site
python -m http.server 8989 --directory site
```

Pushing to `main` builds and publishes the site with GitHub Pages (`.github/workflows/pages.yml`).
