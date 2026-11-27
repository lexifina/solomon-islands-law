# Structure

| Folder | What it holds |
| --- | --- |
| `constitution/` | The Constitution of Solomon Islands (Schedule to S.I. 1978/783): as made, then as the Attorney-General reprints it; one file per section (`sec-006.md`, `sec-069a.md`) |
| `acts/<year>/<NNN>-<slug>/` | An Act of the National Parliament by its year and number, e.g. `acts/2023/012-legislation/`: as passed, then as in force in the Attorney-General's reprint; one file per section (`s-001.md`, `s-015-a.md` for section 15A), `schedule-N.md` for its schedules, `README.md` with its dates and section headings |
| `chapters/<NNN>-<slug>/` | An Act of the 1996 Revised Edition by its Chapter number, e.g. `chapters/026-penal-code/` (Cap. 26), as in force in the Attorney-General's reprint; same files |
| `un-treaties/` | Treaty actions of Solomon Islands (UN Treaty Collection), facts only |
| `legal-system/` | Legal-system facts (Wikidata) |

No folder holds more than 1,000 entries.

## Dates

Each version is one commit, dated 12:00 Pacific/Guadalcanal (UTC+11) on the day it took effect, which its `In-force:`
trailer repeats. For an Act, `In-force-basis:` says where that day comes from, always the Act itself:

- `assent`: the Act commences on assent, and the day of assent is printed on it;
- `stated`: the commencement section names the day (or the day it is deemed to have commenced);
- `cover`: the "Date of Commencement" printed on the Act.

- `reprint-endnotes`: the commencement day the Attorney-General's reprints give for the Act (endnotes, List of
  Legislation);
- `commencement-notice` / `gazette-index`: the day a commencement notice appointed, or the day the Act was published
  in the Gazette when it commences on publication, from the Attorney-General's Annual Index to the Gazette.

A reprint (Kind: consolidation) is the text "as in force at" the day on its cover. It is dated on that day when its
endnotes give it as the commencement day of one of the Acts listed there, or on 1 March 1996 for an Act reprinted
unchanged from the 1996 Revised Edition; any other reprint is held back. An Act whose commencement day no official
source gives is held back too. No date in this repository is the day we downloaded anything.
