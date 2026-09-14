# delivery-checklist 交付核对

Verify a deliverable before it ships — by opening the actual file, not by trusting the script that built it.

交付物发出之前做核对——打开真实文件验证，而不是相信生成它的脚本。

## Why / 为什么

A deliverable carries your credibility: one wrong number in a client-facing file costs more trust than ten correct ones earn back. Most shipped errors come from trusting the script that built the file instead of opening the file itself. The checks here take minutes; the mistakes they catch take days.

交付物承载你的信用：发给客户的一个错数字，比十个对的赚回来的还多。大多数发出的事故，源于"相信生成文件的脚本"而不是"打开文件本身"。这里的检查只要几分钟，它们抓住的错误要花几天。

## The checks / 五道检查

1. **Shape** — only the columns the recipient acts on; headers in the recipient's language.
2. **Open the real file** — row count, deduplicated count, placeholder scan (`TODO` / `XXX` / `[X]` / `test` / stray `N/A`).
3. **Reconcile** — every number in the accompanying report traces to the opened file; incremental files get diffed against their stated baseline, so "all new" becomes a verified fact instead of a claim.
4. **Place & log** — agreed delivery directory, agreed naming, ledger row (date, dedup count, filename).
5. **Final read** — re-open the placed copy exactly as the recipient will.

## The distinction that saves deliveries / 一条关键区分

**Duplicate rows inside one file are a defect; the same entity appearing in two batches is funnel history.** Fix the file, reconcile the ledger. Confusing the two either ships defects or deletes legitimate history.

**同一文件内的重复行 = 缺陷；同一实体出现在两个批次 = 漏斗常态。** 文件要去重，台账要记录。搞混两者，要么把缺陷发出去，要么把正常历史删掉。

## Worked example (synthetic numbers; method from a real audit)

An incremental two-sheet workbook claimed "all new vs the previous version". The checklist ran:

- opened both sheets: 240 rows and 5,100 rows
- dedup on the name+location key: 239 and 5,046 → **54 duplicate rows inside one sheet** — a defect to resolve before shipping
- diffed against the stated baseline: overlap = 0 → the "all new" claim verified (this time it was true)
- placeholder scan: clean

Without the diff, "all new" ships as a claim. Without the dedup, 54 defects ship as rows. The checklist catches both in minutes.

不做 diff，"全部新增"就只是一句声明；不去重，54 行缺陷就直接发出去了。这两件事，核对清单几分钟就能抓住。

## Honest limitations / 如实说明局限

- The dedup key (name+location for entity lists) is a heuristic; two genuinely different entities sharing a name+location will merge — spot-check merges before shipping.
- Ledger reconciliation assumes the ledger exists and is maintained; a broken ledger needs rebuilding first.

去重键（实体清单的 name+location）是启发式：同名同地的两家真不同实体会被合并——发出前抽查合并项。台账对账假设台账存在且被维护；坏的台账要先重建。

## Install / 安装

```bash
git clone https://github.com/ChenneyZhuang/delivery-checklist ~/.claude/skills/delivery-checklist
```

One SKILL.md; works on any spreadsheet the agent can open (xlsx / csv). MIT. v0.2.0 — live-tested on a real incremental deliverable.

单个 SKILL.md；agent 能打开的表格都适用。MIT 许可，v0.2.0，真实增量交付文件实测通过。
