# PORTFOLIO — {{DOMAIN_NAME}} Artifacts

Living index of every artifact produced across the plan. Updated automatically when a DAY.md Final section is filled.

## Summary

- **Total artifacts**: {{COUNT}}
- **Current phase**: {{PHASE_N}} — {{PHASE_NAME}}
- **Best artifact so far**: [{{BEST_ARTIFACT_NAME}}]({{BEST_ARTIFACT_LINK}})
- **Last updated**: {{DATE}}

## By Phase

### Phase {{N}} — {{PHASE_NAME}}
Total: {{PHASE_COUNT}} artifacts

| Day | Date | Domain | Artifact | Path | Quality /5 | Notes |
|-----|------|--------|----------|------|-----------|-------|
| D1 | YYYY-MM-DD | {{DOMAIN}} | [{{NAME}}](./plans/XX_XX/XX_XX/XX_XX/) | path | /5 | {{1-line note}} |
| ... | | | | | | |

{{Repeat per phase}}

## By Domain

### {{DOMAIN_A}}
- D1: [{{artifact}}](link) /5
- D5: [{{artifact}}](link) /5
- ...

{{Repeat per domain}}

## Top 10 (by quality)

1. [{{artifact}}](link) — Day X — /5
2. [{{artifact}}](link) — Day Y — /5
...

## Calibration vs Latest

**Day 0 Baseline**: [{{link to calibration artifact}}](./plans/00_calibration/)
**Most Recent**: [{{link to latest DAY artifact}}](...)

> Play/read/view these back-to-back to SEE your growth.

## Milestone Highlights

- **Day 50**: [{{artifact}}](link)
- **Day 100**: [{{artifact}}](link)
- **Day 200**: [{{artifact}}](link)
- **Final**: [{{artifact}}](link)

---

## Update Rules (for the AI)

When a DAY.md Final section is filled:
1. Append a row to the "By Phase" table for the current phase
2. Append to the "By Domain" section matching the DAY's track/domain
3. If quality rating ≥ 4: consider inserting into "Top 10" (drop lowest-rated if already 10)
4. Update Summary counts
5. Update "last_updated" timestamp
6. If this is a milestone day (50/100/200/final): add to Milestone Highlights

Keep chronological order in By Phase tables. Do NOT delete entries — only move. Update cross-references when paths change.
