# KANBAN

## IN PROGRESS

## TODO

{{FOR each EPIC}}
### EPIC: {{EPIC_NAME}} ({{MONTH_ASSIGNMENT}}, {{WEEK_RANGE}})
{{FOR each TASK}}
- [ ] {{TASK_ID}} {{TASK_DESCRIPTION}} ({{WEEK_DAY_ASSIGNMENT}})
{{END FOR}}

{{END FOR}}

## DONE

---

## Task ID Convention

Prefix derives from the epic or track/tool. Examples:
- `{{ID_PREFIX_TRACK_1}}-T1` (primary track tasks)
- `{{ID_PREFIX_TRACK_2}}-T1` (secondary track tasks, if enabled)
- Specific epic prefixes: `{{EPIC_PREFIX}}-T{{N}}`

Task IDs must be unique across the entire plan.

## Status Indicators

- `[ ]` = TODO (in TODO section)
- `[x]` = DONE (moved to DONE section when completed)
- Flag in DAY.md as in progress → add to IN PROGRESS section during active day
- Flex days stay as TODO until completed or SKIPPED (marked with strikethrough if skipped)

## Update Rules

- Update KANBAN immediately when a DAY.md status changes
- Move tasks from TODO → IN PROGRESS when started
- Move to DONE when DAY.md Final section is filled
- Never delete tasks — mark SKIPPED if abandoned
- New epics added when generating future months
