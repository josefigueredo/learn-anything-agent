# ROADMAP — {{DOMAIN_NAME}} Mastery

Overview of all phases with exit criteria. Move to the next phase only when criteria are met, not by calendar.

{{FOR each phase}}
## Phase {{PHASE_N}} — {{PHASE_N_NAME}} (Months {{MONTH_RANGE}})

**Goal**: {{PHASE_N_GOAL}}

**Duration**: ~{{PHASE_DURATION_MONTHS}} months ({{PHASE_DURATION_DAYS}} days total)

{{IF TRACK_ENABLED}}
**{{TRACK_PRIMARY_NAME}}**:
- [ ] {{PRIMARY_EXIT_CRITERION_1}}
- [ ] {{PRIMARY_EXIT_CRITERION_2}}
- [ ] {{PRIMARY_EXIT_CRITERION_3}}

**{{TRACK_SECONDARY_NAME}}**:
- [ ] {{SECONDARY_EXIT_CRITERION_1}}
- [ ] {{SECONDARY_EXIT_CRITERION_2}}
{{ELSE}}
**Exit criteria**:
- [ ] {{EXIT_CRITERION_1}}
- [ ] {{EXIT_CRITERION_2}}
- [ ] {{EXIT_CRITERION_3}}
- [ ] {{EXIT_CRITERION_4}}
{{/IF}}

{{END FOR}}

---

## Phase Summary

| Phase | Name | Months | Focus | Primary Gate |
|-------|------|--------|-------|-------------|
{{FOR each phase}}
| {{N}} | {{PHASE_NAME}} | {{RANGE}} | {{FOCUS}} | {{PRIMARY_GATE}} |
{{END FOR}}

## Progression Principles

Phase progression is **competence-based, not calendar-based**. If you reach the end of a phase but haven't met exit criteria, extend the phase. If you meet criteria early, move on.

Difficulty escalates through: {{DIFFICULTY_ESCALATION_METHODS}}

## Difficulty Ramp (Planned Intensity)

```
Difficulty
   5 |                                              ████
   4 |                                   ████  ████
   3 |                         ████  ████
   2 |             ████  ████
   1 |   ████ ████
   0 |___|_____|_____|_____|_____|_____|_____|_____|_____|
       M1    M2    M3    M4    M5    M6    M7    M8    M9+
       │     │     │     │     │     │     │     │     │
       P1    P1    P2    P2    P3    P3    P4    P4    P5
```

*(Replace with actual ramp for your plan — difficulty starts at 1, escalates through phases, peaks near the end. Generator produces this chart based on phase count and plan length.)*

## Milestone Markers

- **Day 0**: Calibration (baseline artifact)
- **Day 50**: First celebration check-in
- **Day 100**: Quarter-plus — compare to baseline
- **Day 200**: Halfway+ — major retrospective
- **Day {{FINAL_DAY}}**: Graduation

Every 4 weeks: Checkpoint Day (honest 4-dimension audit)
Every 2 weeks from Week 3: Spaced Repetition review session
