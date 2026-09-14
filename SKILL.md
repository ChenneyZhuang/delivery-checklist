---
name: delivery-checklist
description: |
  Run a pre-send checklist on any deliverable — spreadsheets, reports, data
  extracts — before it goes to a stakeholder or client. Covers trimming to
  the columns the recipient acts on, headers in the recipient's language,
  opening the actual file to verify row counts and dedup counts, logging
  sent batches, placing files in the agreed delivery directory, and keeping
  candidate counts separate from sendable counts. Use when preparing to send
  a spreadsheet, report, or data file to a stakeholder, handing off batch
  results, or double-checking numbers before an external email.
  触发词：交付核对 / 发送前检查 / 文件核对 / delivery check。
license: MIT
metadata:
  version: "0.2.0"
---

# Delivery Checklist: verify before you send

Run this checklist before any deliverable leaves your hands. A deliverable
carries your credibility: one wrong number in a client-facing file costs more
trust than ten correct ones earn back. The checks below take minutes; the
mistakes they catch take days.

## Rules

1. **Keep the sheet tight, headers in the recipient's language.** A
   deliverable gets read in one pass, so trim to the columns the recipient
   acts on — a workable default is six, and wider sheets get split into
   multiple files or cut down. International recipients read headers in
   their own language: translate the headers, not just the data.
2. **Open the real file.** The deliverable is the file on disk, and the only
   evidence about it comes from opening it: row count, deduplicated count,
   and a scan for placeholder residue (`TODO`, `XXX`, `[X]`, `test`,
   `N/A` where a value belongs). A file built by a script is verified by
   opening the output, not by trusting the script's exit code.
3. **Log every sent batch.** Record date, item count, and filename in the
   delivery ledger the moment a batch goes out. The ledger is the source of
   truth for "what did we already send", and it reports deduplicated totals:
   total rows sent across batches counts unique items, raw rows. Tally on
   the identifying pair the recipient would use — for entity lists, the
   name-and-location pair — and record that basis in the ledger, so counts
   reproduce when the file changes format.
4. **Use the agreed delivery directory.** Files go into the project's
   established delivery path with the established naming pattern. A new
   ad-hoc folder fragments the record of where deliverables live.
5. **Report candidate and sendable counts as different numbers.** Candidates
   enter a funnel; sendables pass its gates. A report that presents the
   candidate count as the sendable count overstates delivery by the entire
   gap between the two.
6. **Deduplicate in the file, reconcile across batches.** Duplicate rows
   inside one deliverable are a defect: resolve them in the file before it
   ships. The same entity appearing in two batches is normal funnel
   history: reconcile it in the ledger, where totals count unique items.
   An incremental deliverable additionally names its baseline and shows a
   verified overlap count against it — the delta claim stays a claim until
   the two lists are diffed.

## Steps

1. **Check the file shape.** Apply Rule 1: column count and header language.
   Done when: the sheet carries only the columns the recipient acts on, and
   every header is in the recipient's language.
2. **Open and verify.** Apply Rule 2: open the actual file, record row count
   and deduplicated count, and scan for placeholder residue.
   Done when: you can state the file's row count, its deduplicated count on
   the identifying basis Rule 3 names, and a clean placeholder scan, all
   from the opened file.
3. **Reconcile the numbers.** Compare the file's counts against the source
   data and the report text: the sendable count in the report equals the
   verified row count in the file, duplicate rows inside the file are
   resolved before shipping (Rule 6), and an incremental file is diffed
   against its stated baseline so the report's overlap claim is verified
   rather than repeated. Candidate counts appear only as candidate counts
   (Rule 5).
   Done when: every number in the report traces to the opened file, the
   overlap claim is verified by diff, and the candidate-vs-sendable
   distinction is explicit wherever both appear.
4. **Place and log.** Copy the file into the agreed delivery directory with
   the established naming pattern, then append to the ledger: date, item
   count (deduplicated), filename. When the deliverable has already gone
   out, run the same checks retrospectively: verify the shipped file and
   reconcile the ledger entry against what the file actually contains.
   Done when: the file exists in the delivery directory and the ledger has
   an accurate row for this batch.
5. **Final read.** Re-open the placed file once, as the recipient will, and
   confirm it opens cleanly with the expected content.
   Done when: the placed copy opens and matches the verified numbers.

## Done when

Every rule above has run against this specific deliverable, the numbers in
the accompanying report match the opened file, the file contains zero
duplicate rows on the identifying basis, the ledger records the batch, and
the file sits in the agreed directory having been opened once more as the
recipient will open it.
