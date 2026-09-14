# delivery-checklist 交付核对

Verify a deliverable before it ships — by opening the actual file, not by trusting the script that built it.

交付物发出之前做核对——打开真实文件验证，而不是相信生成它的脚本。

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

## Install / 安装

```bash
git clone https://github.com/ChenneyZhuang/delivery-checklist ~/.claude/skills/delivery-checklist
```

One SKILL.md; works on any spreadsheet the agent can open (xlsx / csv). MIT. v0.2.0 — live-tested on a real incremental deliverable.

单个 SKILL.md；agent 能打开的表格都适用。MIT 许可，v0.2.0，真实增量交付文件实测通过。
