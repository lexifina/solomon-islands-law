# How this repository was made (Solomon Islands)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| legislation.gov.uk: The Solomon Islands Independence Order 1978 (as made), scanned PDF | <https://www.legislation.gov.uk/uksi/1978/783/pdfs/uksi_19780783_en.pdf> | 2026-10-30 | Open Government Licence v3.0 |
| Wikidata | <https://www.wikidata.org/wiki/Q685> | 2026-10-30 | CC0 1.0 |
| UN Treaty Collection (MTDSG status pages) | <https://treaties.un.org/> | 2026-10-29 | Facts only (treaty action, date, depositary); no text copied |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | The Constitution of Solomon Islands (Schedule to S.I. 1978/783), as made | 1 | 1978-07-07 to 1978-07-07 |
| `legal-system` | Solomon Islands: legal system facts (Wikidata) | 1 | 2026-10-30 to 2026-10-30 |
| `un-treaties` | Treaty actions of Solomon Islands on multilateral treaties deposited with the UN Secretary-General (UN Treaty Collection; no treaty text) | 34 | 1981-06-19 to 2026-08-27 |

The build made 48 commits:

| Commits | Kind |
| ---: | --- |
| 3 | first version of an act |
| 45 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 49 laws in the record.
- 82 tags.

## Dates

Each commit is dated at noon (Pacific/Guadalcanal) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: The Independence Order 1978, sections 2(1) and 4(1): the Constitution came into effect on the appointed day, 7 July 1978. https://www.legislation.gov.uk/uksi/1978/783/made

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `564175d90f9fd45f1a87b7d44194e44358a1232c05b71088dec651f93270a263` (539883 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3e59cb6f05eccb94a9ec14431a7f6781221e83ef`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

Not yet run for this build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- The text is the Constitution as made in 1978: the Schedule to S.I. 1978/783. Later amendments are not applied, because the source holds only the Order as made; the repository is therefore one version of the Constitution and is not the current Constitution.
- OCR. The scan has no text layer. It was read with Tesseract 5.4 (English, 300 dpi, page segmentation mode 3). Marginal notes (section headings) were left out because they could not be read reliably; chapter, part and sub-part headings and the arrangement of sections were left out.
- Spot checks against the page images found and corrected, by hand: misread words (for example "cscape", "cultuie", "pynishment", "thatters", "pond government"); "(b)" and "(h)" and "(j)" read as "(5)", "(6)", "(A)" and "(i)"; a few paragraph labels wrong or merged into the paragraph before; compound words broken at a line end (Governor-General, Attorney-General, Auditor-General); and stray speckle and quotation marks. Every word that occurs once was compared with a dictionary built from another OCR-free corpus; a full word-by-word proofread against the scan has not been done.
- Where the scan itself reads "to elect assemblies" (Preamble, "AGREE AND PLEDGE" (a)) the text follows the scan.
- The Independence Order's own sections 1 to 14 and its footnotes are not included; only the Constitution in the Schedule is built. Footnotes inside the Constitution (for example the Acts cited in sections 20 and 145) are kept at the end of the section they belong to.
- The Constitution is dated 7 July 1978, the appointed day on which it came into effect (Order, sections 2(1) and 4(1)); the Order was made on 31 May 1978. The single version is credited to S.I. 1978/783.
- Wikidata facts (CC0) form the "legal-system" act: one version at the retrieval date 2026-10-30, as the oldest version available, because Wikidata holds only a year for the inception.
- An earlier draft of this corpus was read from PacLII captures. It was dropped, because PacLII may not be used as a source; nothing in this build comes from it.
- UN Treaty Collection: 37 multilateral treaties deposited with the UN Secretary-General, with the state's signature, ratification, accession, succession, acceptance or approval dates. Facts only; one version per action date, with the first version credited to the action. Treaties outside the 78 status pages read are not listed.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code (Claude Sonnet 5.5) wrote the extraction code and made the hand corrections listed in decisions. The text itself was recovered by Tesseract OCR; no model wrote or summarised legal text.
