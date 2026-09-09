# Contact Import — Instructions

**Sub-account: the OLD one.** Everything below happens there.

Steps 1–3 must be finished before you import anything in step 4.

---

## Step 1 — Apply the snapshot

Apply the snapshot from the new sub-account to the old sub-account.

Message me when it's done.

---

## Step 2 — Turn off the workflows that came with the snapshot

**Do this immediately after step 1, before anything else.**

Automation → Workflows. For every workflow that arrived with the snapshot, switch it off, or
confirm it is **not** triggered by any of these:

- Contact Created
- Contact Changed / Updated
- Tag Added
- Opportunity Status or Stage Changed
- Form Submitted, Birthday, or any list-based trigger

We import about 15,000 contacts in step 4. If these workflows are live they will send emails
and text messages to real athletes and clients as the contacts load. That cannot be undone.

---

## Step 3 — Confirm two things came across

The custom fields and the pipeline stages already exist in the new sub-account, so the
snapshot should bring them both. Just confirm:

1. **Custom fields** (Settings → Custom Fields) — the fields from the new sub-account are there.
2. **Pipeline stages** (Settings → Pipelines) — the stages from the new sub-account are there.

`1_REFERENCE_STAGENAMES_FIELDS.csv` lists everything the import expects — the 23 field
labels and the 6 stage names. The rows marked *"confirm it arrived"* are the ones that
weren't in the old sub-account before the snapshot, so those are worth checking first.

Reply to confirm both, then go ahead with step 4.

If a field or stage is missing, or you see two pipelines with similar names, stop and tell me
before importing.

---

## Step 4 — Import the Updated file

`2_UPDATE_import_2026-09-08.csv` — 6,952 contacts.

- Match by **Contact Id**
- **Update existing contacts only — do NOT create**
- Map `Contact Id` as **text**
- `Pipeline Stage` maps in the opportunity/pipeline section, not as a custom field
- If a field name in the CRM reads slightly differently from the column name, map it to the
  matching field and tell me which ones

Every Contact Id has been checked against your export, so all 6,952 should match. If any
don't, send me the number before continuing.

---

## Step 5 — Import the New file

`3_NEW_import_2026-09-08.csv` — 8,319 contacts.

- **Create new contacts**
- Duplicate checking **ON**
- Contact Id is blank on purpose — GHL assigns them
- Same field mapping as step 4

---

## Step 6 — 5 manual fixes

`4_MANUAL_MERGES_AND_FIXES.csv` — 4 merges and 1 stage change, done by hand. Merges cannot be
undone, so check each pair first.

---

## Do not import

`DO_NOT_IMPORT_name_duplicates.csv` — 28 contacts I'm still checking. Reference only.

---

## Files

| File | What it is |
|---|---|
| `1_REFERENCE_STAGENAMES_FIELDS.csv` | Step 3 — fields and stages to confirm |
| `2_UPDATE_import_2026-09-08.csv` | Step 4 — import, 6,952 rows |
| `3_NEW_import_2026-09-08.csv` | Step 5 — import, 8,319 rows |
| `4_MANUAL_MERGES_AND_FIXES.csv` | Step 6 — 5 manual fixes |
| `DO_NOT_IMPORT_name_duplicates.csv` | Do not import — 28 rows |
