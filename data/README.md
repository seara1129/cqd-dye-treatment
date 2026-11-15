# all-readings.csv: column guide

`all-readings.csv` holds the 216 colorimeter readings from the methylene blue (MB) experiment: MB dye + hydrogen peroxide (H₂O₂) + carbon quantum dots (CQDs) under UV light. One row is one reading. The file is UTF-8 with a byte-order mark (BOM). It has 13 columns and a header row.

## Columns

| Column | Meaning | Units / format | Values seen |
|---|---|---|---|
| Session | Lesson session the reading was taken in | Text | `Lessons 4-5` (156 rows), `Lesson 6` (42), `Lesson 7` (18) |
| Date (colorimeter clock) | Date stamped by the colorimeter's own clock | `YYYY-MM-DD` | `2026-10-13` (156), `2026-10-14` (42), `2026-10-15` (18) |
| Run | Run number within the session | Whole number | `Lessons 4-5`: 1 to 16. `Lesson 6`: 1 to 7. `Lesson 7`: 1 to 3. The numbers restart each session. |
| Sample | Label of the solution measured | Text | 25 labels (see Codes) |
| Trial | Trial group the reading belongs to | Text | 10 values (see Codes) |
| Stage | Point in the procedure when it was read | Text | 6 values (see Codes) |
| Time (s) | Time of the reading within its run | Seconds | 0 to 23 |
| A 450 nm (violet) | Absorbance on the 450 nm channel | Absorbance (no unit) | 0 to 2.952 |
| A 500 nm (blue) | Absorbance on the 500 nm channel | Absorbance (no unit) | 0.0006051 to 1.399 |
| A 550 nm (green) | Absorbance on the 550 nm channel | Absorbance (no unit) | 0.008 to 0.941 |
| A 570 nm (yellow) | Absorbance on the 570 nm channel | Absorbance (no unit) | 0.007 to 0.934 |
| A 600 nm (orange) | Absorbance on the 600 nm channel | Absorbance (no unit) | 0.007 to 1.255 |
| A 650 nm (red) | Absorbance on the 650 nm channel | Absorbance (no unit) | 0.016 to 1.264 |

No cell is blank.

## Codes

### Trial

- `A: H2O2 only (control)` (18 rows): MB + 3% H₂O₂ with no CQD. The site calls this the H₂O₂-only control, trial A.
- `B: Plain CQD amount` (32): 1, 2 and 3 mL of plain CQD with MB + 3% H₂O₂. The site lists these as trials B1 to B3.
- `C: 6% H2O2 + CQD` (45): MB + 6% H₂O₂ + 1 mL CQD, three repeats. The site calls this trial C.
- `D: N-CQD` (35): MB + 3% H₂O₂ + 1 mL nitrogen-doped CQD (N-CQD), three beakers. The site says trial D is the same three beakers read before and after 30 min UV.
- `E: N-CQD amount` (18): 1, 2 and 3 mL N-CQD, read before H₂O₂ + UV.
- `Calibration` (21): MB standards and the 10 ppm stock. The rows are labelled in Sample. Not documented on the site beyond the 10 ppm stock reading used as the starting value.
- `Check` (21): all rows are `6% H2O2 only`. The site shows a "6% H₂O₂ on its own, check reading" graph.
- `Duplicate` (5): `Repeat reading of control 1 (same cuvette)`. Not documented on the site.
- `Discarded` (7): `Discarded reading`. Not documented on the site why they were discarded.
- `Unknown` (14): `Unlabelled run`. Not documented on the site.

### Stage

- `After 30 min UV` (123 rows): read after 30 minutes under the UV torch. The site describes the 30-minute UV step.
- `Before UV` (12): read before the UV step. The site's trial D has before and after readings.
- `Before H2O2 + UV` (18): read before H₂O₂ and UV were applied (trial E; the site says "before H₂O₂ + UV").
- `Reference` (49): used for the calibration, check and unlabelled Lesson 6 rows. Not documented on the site.
- `Discarded` (7): the same rows as Trial `Discarded`. Not documented on the site.
- `Unknown` (7): the stage was not recorded. Not documented on the site.

### Sample

- MB standards and stock: `MB standard 40 ppm` (8 rows), `MB standard 60 ppm` (7), `MB stock 10 ppm (starting solution)` (6). The site states the dye is 10 ppm methylene blue.
- Controls: `MB + 3% H2O2, no CQD (control 1)`, `(control 2)`, `(control 3)` (6 rows each).
- Plain CQD amounts: `MB + 3% H2O2 + 1 mL CQD` (7), `+ 2 mL CQD` (13), `+ 3 mL CQD` (12).
- 6% H₂O₂ + CQD: `MB + 6% H2O2 + 1 mL CQD (rep 1)` (24), `(rep 2)` (11), `(rep 3)` (10).
- N-CQD trial D: `MB + 3% H2O2 + 1 mL N-CQD (rep 1)` (2), `(rep 2)` (4), `(rep 3)` (6), and `(N doped 1)` (7), `(N doped 2)` (10), `(N doped 3)` (6). Not documented on the site: why the same beakers carry both "rep" and "N doped" labels.
- N-CQD amounts, trial E: `MB + 1 mL N-CQD`, `MB + 2 mL N-CQD`, `MB + 3 mL N-CQD` (6 rows each).
- Other: `6% H2O2 only` (21), `Repeat reading of control 1 (same cuvette)` (5), `Discarded reading` (7), `Unlabelled run` (14). See Trial above.

### Session

- `Lessons 4-5`, `Lesson 6`, `Lesson 7`: lesson names only. Which trial was done in which lesson is not stated on the site, but the CSV shows trials A, B, C, Calibration, Check, Duplicate, Discarded and some Unknown in `Lessons 4-5`, trial D in `Lesson 6` and trial E in `Lesson 7`.

## Notes

- The colorimeter reads six colour channels from 450 to 650 nm. Methylene blue shows up best on the 650 nm (red) channel, closest to its 664 nm peak.
- Absorbance above A = 2 lets less than 1% of light through. Readings that high are unreliable. In this file only the 450 nm column goes above 2 (31 rows, all in trials D and E). The other five channels stay below 1.4.
- The "Date (colorimeter clock)" column is the device's clock, not a lab-book date. It agrees with the site for trial C (13 Oct), trial D (14 Oct) and trial E (15 Oct). It disagrees for trials A and B: the site gives 12 Oct, but the clock says 2026-10-13 for every `Lessons 4-5` row.
- Each run holds several readings taken in consecutive seconds (see `Time (s)`).
