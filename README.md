# Solomon Islands: law history in git

The law of Solomon Islands as a git history: one file per section, one commit per version on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every line; `git log` lists every change to a section; picking a date gives the text this record holds for that day.

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is the national law of Solomon Islands, which global-law reads at `solomon-islands/national/acts/`.

**What is in it now:** the Constitution of Solomon Islands as made, the Schedule to the Solomon Islands Independence Order 1978 (S.I. 1978/783), in its one version, in force from independence on 7 July 1978: the Preamble, 145 sections and Schedules 1 to 3. Beside it are 47 treaty actions of Solomon Islands (signatures, ratifications, accessions, successions and one acceptance) on 37 multilateral treaties deposited with the UN Secretary-General, without treaty text, and legal-system facts from Wikidata. The Constitution's later amendments, and every other Solomon Islands law, are not here yet. [`constitution/README.md`](constitution/README.md) lists every provision; [`data/laws.csv`](data/laws.csv) lists the law or treaty action behind each version.

Each provision is one file in `constitution/`: `sec-006.md` is section 6, protection from slavery and forced labour; `preamble.md` is the Preamble and `schedule-3.md` Schedule 3, the application of laws. Each treaty is one file in `un-treaties/`, named by its UN Treaty Collection reference (`untc-iv-11.md` is the Convention on the Rights of the Child).

The text is in English, the official language. legislation.gov.uk holds the Order only as an image-only scan, so the words were read by optical character recognition (OCR) and misreadings found were corrected by hand; no full proofread against the scan has been done, so some may remain.

## Questions as git commands

| Question | Command |
| --- | --- |
| Every change to section 6 of the Constitution | `git log -p --word-diff -- constitution/sec-006.md` |
| Which law wrote each line of section 6? | `git blame constitution/sec-006.md` |
| Every version of section 6, with the day each took effect | `git log --format="%h %(trailers:key=In-force,valueonly,separator=) %an" -- constitution/sec-006.md` |
| Section 6 on 1 January 1980 | `python tools/on.py 1980-01-01 constitution sec-006` |

**Outside git**, we also host this record publicly, for free:

- **[Ask Claude about Solomon Islands law](https://global-law.lexifina.com/v1/try_claude?country=solomon-islands)**: opens Claude with a first question ready.
- **[Ask ChatGPT](https://global-law.lexifina.com/v1/try_chatgpt?country=solomon-islands)**: the same question in ChatGPT.
- **[Call the API in your browser](https://global-law.lexifina.com/v1/search_law?query=forced+labour&jurisdictions=solomon-islands)**: a search of Solomon Islands law for "forced labour", returned as JSON. See the [documentation here](https://lexifina.com/api/global-law).

Both assistants read the record through the free Global law connector (MCP, `https://global-law.lexifina.com/mcp`); the first time, the chat gives you the link that adds it. Ask in English.

**Host it yourself easily.** All it takes is git and Python, and the tools run on your machine:

```sh
git clone --depth 1 https://github.com/lexifina/global-law && cd global-law
python3 tools/countries.py add solomon-islands/national/acts
python3 tools/law.py show 1980-01-01 solomon-islands/national/acts/constitution/sec-006.md
```

Opened in Claude Code, Cursor, VS Code or Codex, the clone also starts a local MCP server with the same tools ([MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md)).

## Dates

Each commit is dated at noon, Pacific/Guadalcanal, on the day the version took effect, and carries it in its `In-force:` trailer:

- the Constitution's one version is dated 7 July 1978, the appointed day on which it came into effect (Order, sections 2(1) and 4(1)); its `Enacted:` trailer gives the day the Order was made (31 May 1978) and `Published:` 8 June 1978;
- each treaty action is dated by the day the UN Treaty Collection gives for it, from 1981 to 2026;
- the legal-system facts are dated 30 October 2026, the day they were retrieved, because Wikidata gives only a year for the state's inception.

The Constitution's version is credited to the Order that made it (`S.I. 1978/783`), and tagged `constitution/1978-07-07` and `law/si-1978-783`; each treaty action is credited to itself (`Accession: …`), except the earliest, a 1981 succession, which opens the treaty record as its oldest version available, credited to the publisher.

## How it is checked

- `tools/check_repo.py` reads every version back from git on the day it took effect, and on the day before, and compares it, file by file, with the corpus it was built from (its sha256 is in [`data/corpus.sha256`](data/corpus.sha256)); every commit's trailers must parse.
- `tools/build.py` writes the history from that corpus in one pass, and the same corpus always gives the same commit hashes. [`REPRODUCE.md`](REPRODUCE.md) gives the builder's hashes and the OCR corrections made by hand; it does not yet record a check run or a second build.
- History is append-only: no merge commits, no rewriting, no commit dated in the future.

## What it does not show

- **Amendments.** The Constitution has been amended since 1978; no amendment is applied, so this is not the text in force today.
- **Any other Solomon Islands law.** No Act of Parliament, subsidiary legislation or court decision is here yet; the consolidated legislation is published only on sites this record does not use.
- **Headings.** The marginal notes (section headings), the chapter and part headings and the arrangement of sections are left out; footnotes are kept at the end of their section.
- **The Order itself.** Only its Schedule, the Constitution, is here, not the Order's own sections 1 to 14.
- **Every treaty.** The treaty actions come from a selected set of UN Treaty Collection status pages, and no treaty text is copied.

## Sources

| Source | Kind | Past versions | Notes |
| --- | --- | --- | --- |
| [legislation.gov.uk](https://www.legislation.gov.uk/uksi/1978/783/made) (The National Archives) | UK statutory instrument, as made: the Solomon Islands Independence Order 1978 | no, only as made | The Constitution is the Schedule to the Order; an image-only scan, read by OCR |
| [UN Treaty Collection](https://treaties.un.org/) | Status of multilateral treaties deposited with the UN Secretary-General | each action on its own day | Facts only: the treaty, the action and its date |
| [Wikidata](https://www.wikidata.org/wiki/Q685) | Legal-system facts | no, as retrieved on 30 October 2026 | Form of government, institutions, official languages |

## Licence

See [`LICENSE`](LICENSE). The text is taken from legislation.gov.uk and contains public sector information licensed under the Open Government Licence v3.0; the facts come from Wikidata (CC0 1.0) and the UN Treaty Collection, with no treaty text reproduced. Lexifina's own contributions (the history, commit messages, tables and tools) are dedicated to the public domain under CC0 1.0.

No AI model wrote or translated legal text; the text was read from the scan by OCR (Tesseract). The scripts were written by an AI model, which also made the hand corrections of OCR misreadings that [`REPRODUCE.md`](REPRODUCE.md) describes.

## More

From [lexifina/global-law](https://github.com/lexifina/global-law):

- [FEATURES.md](https://github.com/lexifina/global-law/blob/main/FEATURES.md): every feature, and what every corpus must support (`git blame`, `law.py`, the MCP tools)
- [FAQ.md](https://github.com/lexifina/global-law/blob/main/FAQ.md): questions and answers · [CONTRIBUTING.md](https://github.com/lexifina/global-law/blob/main/CONTRIBUTING.md): proposing changes · [MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md): the MCP server · [REPRODUCE.md](https://github.com/lexifina/global-law/blob/main/REPRODUCE.md): how it was built · [CHANGELOG.md](https://github.com/lexifina/global-law/blob/main/CHANGELOG.md)
- [FRESHNESS.md](https://github.com/lexifina/global-law/blob/main/FRESHNESS.md): how current each corpus is · [Monitoring](https://github.com/lexifina/global-law/tree/main/monitoring): whether updates are running · [WATCHING.md](https://github.com/lexifina/global-law/blob/main/WATCHING.md): how each official source is watched for changes
- [performance/](https://github.com/lexifina/global-law/tree/main/performance): how fast the tools are, measured
- [visualisations/](https://github.com/lexifina/global-law/tree/main/visualisations): charts and bridges across the world's law
- [Vulnerabilities](https://github.com/lexifina/global-law/tree/main/vulnerabilities): mistakes in legislation as published
