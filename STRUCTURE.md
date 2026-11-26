# Structure

| Folder | What it holds |
| --- | --- |
| `constitution/` | The Constitution of Solomon Islands as made (Schedule to S.I. 1978/783), one file per section (`sec-006.md`) |
| `acts/<year>/<NNN>-<slug>/` | An Act of the National Parliament as passed, by its year and number, e.g. `acts/2023/012-legislation/`; one file per section (`s-001.md`, `s-015-a.md` for section 15A), `schedule.md` for its schedule, `README.md` with its dates and section headings |
| `un-treaties/` | Treaty actions of Solomon Islands (UN Treaty Collection), facts only |
| `legal-system/` | Legal-system facts (Wikidata) |

No folder holds more than 1,000 entries.

## Dates

Each version is one commit, dated 12:00 Pacific/Guadalcanal (UTC+11) on the day it took effect, which its `In-force:`
trailer repeats. For an Act, `In-force-basis:` says where that day comes from, always the Act itself:

- `assent`: the Act commences on assent, and the day of assent is printed on it;
- `stated`: the commencement section names the day (or the day it is deemed to have commenced);
- `cover`: the "Date of Commencement" printed on the Act.

An Act that commences on the day it is published in the Gazette, or on a day the Minister appoints by notice, is held
back until that day can be read from an official source. No date in this repository is the day we downloaded anything.
