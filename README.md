# BDC Contact ID Remap — Import Package (2026-09-02)

Everything in this folder is what gets executed. Nothing else is needed.

## Files

| File | Rows | What it is |
|---|---|---|
| `BDC_ContactID_Remap_2026-09-02.xlsx` | — | Master workbook (all tabs, reference copy) |
| `..._MERGE.csv` | 334 | Worklist: merge these duplicates in the GHL UI |
| `..._DELETE.csv` | 1,540 | Worklist: delete these contacts in the GHL UI |
| `..._UPDATE.csv` | 7,852 | **Import file**: updates existing contacts (matched by Contact Id) |
| `..._NEW.csv` | 7,447 | **Import file**: creates new contacts (Contact Id column is blank on purpose) |

## Execute in this order — do not reorder

1. **MERGE** (UI, admin, desktop). Merge each Merge-In contact into its Master contact.
   Max 10 per merge; merges cannot be undone. `Reason Master Chosen` explains each pick.
2. **DELETE** (UI). Every row was verified twice (afternoon + fresh evening pull) to have
   zero conversation history and zero advanced opportunities.
3. **UPDATE** (CSV import). Configure the import to match/update by **Contact Id — update
   existing, never create**. Contact Id must map as text.
4. **NEW** (CSV import). Duplicate-checking ON. GHL assigns the ids.

## Pre-flight — must be green before step 3

- [ ] 5 stage renames in Settings → Pipelines:
      AC: `Discovery phase`→`Discovery Meeting`, `Paid`→`Contract Signed/Paid`
      BE: `Discovery phase`→`Discovery Meeting`, `Contract`→`Contract/Invoice Sent`
      JA Client: `Discovery phase`→`Discovery Meeting`
      MV Client: `Discovery phase`→`Discovery Meeting`
      (then `check_stages.py` in the folder above must print READY)
- [ ] Field labels exist in GHL exactly as the CSV headers read (Category, X Account,
      NIL Valuation, Class, etc.) — a mismatched label fails silently on every row (C-19)
- [ ] Assigned To names match real GHL users

## Two small manual touches (any time, non-blocking)

- Merge `f1jF996FZHMt1AVpU8Yk` + `bRNDS3nhlGTXhUbGh4Mc` (same person, adcochran77@gmail.com),
  set stage **Contacted**
- If the import slips more than a few days, re-run the freshness check before DELETE

Full audit trail: `REPORT.md` one folder up.
