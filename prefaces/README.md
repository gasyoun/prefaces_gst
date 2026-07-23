# GST front matter — Goldstücker's *A Dictionary, Sanskrit and English*

OCR + translation of the **front matter** (title pages, dedication, preliminary remarks, corrections/additions) of:

> **Theodor Goldstücker**, *A Dictionary, Sanskrit and English, extended and improved from the second edition of the Dictionary of Professor H. H. Wilson, with his sanction and concurrence; together with a Supplement, Grammatical Appendices and an Index, serving as an English-Sanskrit Vocabulary.* Berlin: A. Asher and Co.; London: David Nutt. 1856–1860 (Vol. I, Parts 1–4).

Source scans (Cologne csldoc build):
[gstpref.html](https://sanskrit-lexicon.uni-koeln.de/scans/csldev/csldoc/build/dictionaries/prefaces/gstpref.html)

The dictionary itself in the Cologne corpus: [csl-orig `v02/gst`](https://github.com/sanskrit-lexicon/csl-orig/tree/master/v02/gst).

## Source language

The front matter is **English** throughout. Therefore the per-page base file `gstprefNN.md` is already the English edition (no separate `.en.md`); only a Russian translation `gstprefNN.ru.md` is provided. Personal names and bibliographic work-titles are kept verbatim in the source; in the Russian files personal names are Cyrillicised (Goldstücker → Гольдштюкер, Wilson → Уилсон, Asher → Ашер, Aufrecht → Ауфрехт, Cassal → Кассаль), publisher imprints kept in the Latin original.

The two **Corrections** pages (`gstpref05`, `gstpref06`) are dense errata lists of `Page / line / read / add / take off` entries with many small Devanāgarī affix fragments; these were transcribed against the dictionary's own digitization in [`csl-orig/v02/gst/gst.txt`](https://github.com/sanskrit-lexicon/csl-orig/tree/master/v02/gst) (sections `CORRECTIONS AND ADDITIONS.` and `CORRECTIONS.`), whose SLP1 codes give the exact Devanāgarī. Editorial running prose is translated in the `.ru` files; page/line references, Devanāgarī, abbreviation keys (`sam. aff.`, `kṛt aff.`, `taddh. aff.`, `Tatpur.`, `Bahuvr.`) and corrected English dictionary text are kept verbatim.

The tiny digitizer running header/footer stamps added to every scan were omitted (not part of the original).

## File conventions

| suffix | meaning |
|---|---|
| `gstprefNN.md` | source page, faithful English transcription |
| `gstprefNN.ru.md` | Russian translation |
| `gstpref_all.en.md` | consolidated English edition, all pages + TOC |
| `gstpref_all.ru.md` | consolidated Russian edition, all pages + TOC |
| `build_combined.py` | reproducible builder for the `*_all.*` files (`DICT=gst python build_combined.py`) |
| `scans/` | downloaded native-resolution PNG scans |

## Consolidated editions

| Edition | File |
|---|---|
| English (source) | [gstpref_all.en.md](gstpref_all.en.md) |
| Russian | [gstpref_all.ru.md](gstpref_all.ru.md) |
| Builder script | [build_combined.py](build_combined.py) |

## Contents

| NN | Section | Vol. | Source (EN) | Russian |
|---|---|---|---|---|
| 01 | Title (Vol. I) | 1 | [gstpref01.md](gstpref01.md) | [ru](gstpref01.ru.md) |
| 02 | Dedication (to H. H. Wilson) | 1 | [gstpref02.md](gstpref02.md) | [ru](gstpref02.ru.md) |
| 03 | Preliminary Remarks, 1 | 1 | [gstpref03.md](gstpref03.md) | [ru](gstpref03.ru.md) |
| 04 | Preliminary Remarks, 2 | 1 | [gstpref04.md](gstpref04.md) | [ru](gstpref04.ru.md) |
| 05 | Corrections and Additions | 1 | [gstpref05.md](gstpref05.md) | [ru](gstpref05.ru.md) |
| 06 | Corrections | 1 | [gstpref06.md](gstpref06.md) | [ru](gstpref06.ru.md) |
| 07 | Title, Vol. I Part 3 (अपतल्क — अभिचेद्य) | 1 | [gstpref07.md](gstpref07.md) | [ru](gstpref07.ru.md) |
| 08 | Title, Vol. I Part 4 (अभिज — अभ्याहित) | 1 | [gstpref08.md](gstpref08.md) | [ru](gstpref08.ru.md) |

## Signatures / dates found

- **Preliminary Remarks** signed: *University College, London, June, the 30th, 1856. TH. GOLDSTÜCKER.* ([gstpref04.md](gstpref04.md))
- Title page Vol. I: **MDCCCLVI** (1856).
- Title page Vol. I Part 3: **MDCCCLVIII (November)** (1858).
- Title page Vol. I Part 4: **MDCCCLX (May)** (1860).

<details>
<summary><strong>OCR run notes (2026-06-22)</strong> — cost, timing, technical lessons</summary>

Produced by the `/cologne-preface-ocr` skill (vision OCR + translation), **resumed run** — a prior attempt had stalled on the dense corrigenda page (`gstpref05`) after writing pages 01–04 and downloading all 8 scans. Process retrospective, not part of the deliverable.

**Resumed from disk.** Already present: 8 scans in `scans/`, `gstpref01–04.md`, sub-page HTML + index. Missing and produced this run: source pages `gstpref05–08.md`, all 8 `*.ru.md`, both `*_all.*`, `build_combined.py`, this README.

**Cost.** Synchronous single-thread (no subagents per retry rules). Main thread ≈ 90–110 k tokens, dominated by ~16 native-resolution crop reads (4 overview thumbnails + the two Corrections pages split into L/R bands + the two Part-3/4 Devanāgarī range tiles). No agent deaths.

**Technical lessons (reusable):**
1. The two **Corrections** pages are full-width single-column errata, not two-column — crop horizontal bands and split each into L/R native-res halves; bands must overlap so lines clipped at a band edge are recoverable from the neighbour.
2. The dictionary's **own digitization** (`csl-orig/v02/gst/gst.txt`) already contains both Corrections sections in SLP1 — cross-checking against it resolves every tiny Devanāgarī affix fragment (`ङीष्`, `घञ्`, `अजगन्धि`, …) far faster and more reliably than zooming each conjunct. This is the key speed-up for errata pages.
3. The Part-3 / Part-4 title pages differ from the Vol. I title only in the `VOL. I. PART n.` line, the Devanāgarī headword range, and the imprint year/month — read just the range tile, reuse the rest.

</details>

---

**Home-repo decision needed.** GST currently has no dedicated dictionary repo cloned locally (source lives only inside [`csl-orig/v02/gst`](https://github.com/sanskrit-lexicon/csl-orig/tree/master/v02/gst)). This `prefaces_gst/` working directory is **not** a git repo and was **not** committed. A maintainer decision is required on where these files should live (e.g. a new `sanskrit-lexicon/GST` repo's `prefaces/`, or a `prefaces/` folder inside another GST-owning repo) before committing and adding the repo-root index entry per the skill's Phase 6b.
