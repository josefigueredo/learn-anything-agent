# WEEK {{WEEK_N}} — {{WEEK_FOCUS}}

**Month**: {{MONTH_N}} — {{MONTH_THEME}}
**Phase**: {{PHASE_N}} — {{PHASE_N_NAME}}
**Goal**: {{WEEK_GOAL}}

| Day | Track | Task | Subtasks | Output | Status |
|-----|-------|------|----------|--------|--------|
{{FOR each scheduled day}}
| D{{N}} | {{TRACK}} | {{TASK_ID}} {{TASK_NAME}} | {{SUBTASK_1}} • {{SUBTASK_2}} • {{SUBTASK_3}} | {{OUTPUT}} | {{STATUS: TODO / FLEX / REVIEW}} |
{{END FOR}}

{{IF REVIEW_WEEK}}
## Spaced Repetition
**Day {{N}}** is a REVIEW session — revisits {{ORIGINAL_TOPIC}} from Week {{ORIGINAL_WEEK}}. Goal: confirm the skill is still fluent and apply it with current-week context.
{{/IF}}

## Resources This Week
- {{RESOURCE_1}}
- {{RESOURCE_2}}

{{IF CROSS_TRACK_WEEK}}
## Cross-Track Connection
{{TRACK_PRIMARY}} days cover {{PRIMARY_TOPIC}}. {{TRACK_SECONDARY}} days mirror the same topic using {{SECONDARY_TOOL}}. Key synthesis: {{SYNTHESIS_NOTE}}.
{{/IF}}

## Retrospective (fill at week end)

**What went well**:

**What was harder than expected**:

**What to adjust next week**:

**Skill progress** (any domain leveled up?):

**Plateau check** — am I stuck on something for 2+ weeks? If yes, what:

**Difficulty rating (1-5)**: ___

> Rating 4-5 = too hard (next week: reduce scope, add review day)
> Rating 1-2 = too easy (next week: add constraints, stretch goals)
> Rating 3 = just right (maintain pace)

**Any days SKIPPED?** Which and why:

**Doubt Log review** (aggregate from each DAY.md this week):
For each open doubt, choose one: answer now / schedule session / link resource / flag persistent.
- Q: {{from Day X}} → Action: 
- Q: {{from Day Y}} → Action: 
- Q: {{from Day Z}} → Action: 

Persistent doubts (unresolved 2+ weeks) — schedule dedicated session next week:

**Adaptive adjustment for next week**:
