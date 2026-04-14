# MONTH {{MONTH_N}} — {{MONTH_THEME}}

**Phase**: {{PHASE_N}} — {{PHASE_N_NAME}}
**Dates**: {{START_DATE}} to {{END_DATE}} ({{WEEKS}} weeks, {{DAYS_PER_WEEK}} days/week = {{TOTAL_SESSIONS}} sessions)

## Goals
1. {{MONTH_GOAL_1}}
2. {{MONTH_GOAL_2}}
3. {{MONTH_GOAL_3}}

## Weekly Breakdown

| Week | Focus | Epic | Days |
|------|-------|------|------|
{{FOR each week}}
| W{{N}} | {{WEEK_FOCUS}} | {{EPIC_NAME}} | D{{DAY_RANGE}} |
{{END FOR}}

## End-of-Month Milestones
- [ ] {{MILESTONE_1}}
- [ ] {{MILESTONE_2}}
- [ ] {{MILESTONE_3}}
- [ ] {{MILESTONE_4}}
- [ ] {{MILESTONE_5}}

{{IF CELEBRATION_THIS_MONTH}}
## 🎉 Celebration Check
This month contains **Day {{CELEBRATION_DAY}}** — a milestone celebration. Plan a reflection session on that day.
{{/IF}}

{{IF SPACED_REP_THIS_MONTH}}
## Spaced Repetition This Month
- Week {{N}}, Day {{M}}: Review {{TOPIC}} from Week {{ORIG_WEEK}}
- (additional review sessions if applicable)
{{/IF}}

## Skill Level Check (fill at month end)

| Domain | Start | End | Notes |
|--------|-------|-----|-------|
{{FOR each domain}}
| {{DOMAIN_NAME}} | {{START_LEVEL}} | | |
{{END FOR}}

## Monthly Review (fill at month end)

**What went well**:

**What was hard**:

**Plateau check** — any skill stuck on the same level for 2+ months?

**Adaptive difficulty** — should I increase or decrease intensity? Which direction and why:

**Artifacts produced this month** (count): ___

**Streak** — longest consecutive days completed: ___

**Milestones hit**:

**What to change for Month {{NEXT_MONTH_N}}**:
