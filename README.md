# Solomon Islands: law history in git

The law of Solomon Islands as a git history: one file per provision, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

The Constitution of Solomon Islands as made in 1978: the Schedule to the Solomon Islands Independence Order 1978 (S.I. 1978/783), in English, the official language. It is a first build, not the current Constitution: later amendments are not applied. Beside it are two fact-only acts: legal-system facts from Wikidata (CC0) and the treaty actions of Solomon Islands from the UN Treaty Collection.

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | The Constitution of Solomon Islands (Schedule to S.I. 1978/783), as made: Preamble, sections 1 to 145 and Schedules 1 to 3 | 1 | As made, in effect 7 July 1978. Later amendments are not applied. |
| `legal-system/` | Legal system facts from Wikidata | 1 | Facts as of 30 October 2026 |
| `un-treaties/` | Treaty actions of Solomon Islands: signature, ratification, accession (UN Treaty Collection; no treaty text) | 34 | Each action on its own date |

## Source

Constitution text: [legislation.gov.uk](https://www.legislation.gov.uk/uksi/1978/783/made), The National Archives: *The Solomon Islands Independence Order 1978* (S.I. 1978/783), as made, under the Open Government Licence v3.0. Retrieved 30 October 2026.

**The text was recovered by optical character recognition (OCR).** legislation.gov.uk holds this Order only as an image-only scan (82 pages, no text layer), so the words in `constitution/` were read from the scan with Tesseract 5.4 (English), then checked: unfamiliar words were compared with the scan, and sample pages were compared with the page images. A number of misreadings were corrected by hand (listed in `REPRODUCE.md`, under decisions), but a full word-by-word proofread has not been done, so some misreadings may remain. Where the text matters, read the scan at the source link above.

Facts: Wikidata (https://www.wikidata.org/wiki/Q685, CC0 1.0) and the UN Treaty Collection (https://treaties.un.org/; facts only, no treaty text), retrieved 30 October 2026.

## Dates

The Constitution has one version, dated **7 July 1978**, the appointed day on which it came into effect (Order, sections 2(1) and 4(1)); the Order itself was made on 31 May 1978. The commit is credited to S.I. 1978/783. `legal-system` is dated by the retrieval date (30 October 2026) as the oldest version available, because Wikidata holds only a year for the state's inception; `un-treaties` is dated by the day of each treaty action.

## How it is checked

Every version is read back from git on the day it took effect and on the day before (`tools/check_repo.py`) and must match `corpus.json`; results are in `REPRODUCE.md`.

## What "author" means

The author of a commit is the law (or, for facts, the retrieval or the treaty action) that made the change, with an e-mail address that cannot exist (`<law key>@legislation.gov.uk.invalid`). The committer is always Lexifina.

## Limits

- Not complete and not current. Missing: every amendment since 1978 (the Constitution has been amended several times), the Independence Order's own sections 1 to 14, the marginal notes (section headings), the arrangement of sections, and the chapter and part headings. Footnotes inside the Constitution are kept at the end of the section they belong to.
- The text is OCR output and may contain misreadings; where the scan reads oddly it is followed as printed (for example "to elect assemblies" in the Preamble).
- Treaties come from the status pages of a selected set of UN Treaty Collection treaties, not every treaty.
- Solomon Islands' own consolidated legislation is not here: it is published only on sites we do not use or cannot reach.
