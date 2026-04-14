# DAY {{DAY_N}} — {{DAY_TOPIC}}

**Date**: {{DATE}} ({{WEEKDAY}})
**Track**: {{TRACK_NAME}}
**Domain**: {{DOMAIN_AREA}}
**Task**: {{TASK_ID}}
**Expected Output**: {{ARTIFACT_DESCRIPTION}}

{{IF CROSS_TRACK}}
**Cross-Track Note**: This day mirrors {{OTHER_TRACK_NAME}} Day {{OTHER_DAY_N}} — {{CONNECTION_DESCRIPTION}}
{{/IF}}

{{IF REVIEW_DAY}}
**⟲ Review Day**: Revisits {{ORIGINAL_TOPIC}} from Day {{ORIGINAL_DAY_N}} ({{WEEKS_AGO}} weeks ago).
{{/IF}}

## Today's Goal
{{SPECIFIC_GOAL_1_2_SENTENCES}}

## Background
{{WHY_THIS_MATTERS — 2-3 sentences connecting today's topic to the epic, phase goal, and primary goal. Reference the learner's motivation when relevant.}}

## Resources
- {{RESOURCE_1}}
- {{RESOURCE_2}}

---

{{SESSION BLOCKS — include based on SCHED_SESSIONS_PER_DAY}}

{{IF SESSIONS == 1}}
### Focus ({{SESSION_DURATION}} min)
**Objective**: {{COMBINED_OBJECTIVE}}
**Do this**:
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}
4. {{STEP_4}}
5. {{STEP_5}}
6. {{STEP_6}}

**Capture**: {{WHAT_TO_WRITE_DOWN}}
{{/IF}}

{{IF SESSIONS == 2}}
### S1 - Learn ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_UNDERSTAND}}
**Do this**:
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}
4. {{STEP_4}}

**Capture**: {{NOTES_TO_TAKE}}

### S2 - Apply ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_BUILD}}
**Do this**:
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}
4. {{STEP_4}}

**Capture**: {{FINAL_RESULT + ARTIFACT_PATH + TOMORROW_HOOK}}
{{/IF}}

{{IF SESSIONS == 3}}
### S1 - Learn ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_UNDERSTAND}}
**Do this**:
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}
4. {{STEP_4}}

**Capture**: {{NOTES_TO_TAKE}}

### S2 - Apply ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_BUILD}}
**Do this**:
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}
4. {{STEP_4}}

**Capture**: {{WHAT_WAS_BUILT}}

### S3 - Output ({{SESSION_DURATION}} min)
**Objective**: {{PRODUCE_ARTIFACT}}
**Do this**:
1. {{FINALIZE_STEP_1}}
2. {{FINALIZE_STEP_2}}
3. {{QUALITY_CHECK}}

**Capture**: {{FINAL_RESULT + ARTIFACT_PATH + TOMORROW_HOOK}}
{{/IF}}

{{IF SESSIONS == 4}}
### S1 - Learn ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_UNDERSTAND_BY_END}}
**Do this**:
1. {{STEP_1_SPECIFIC}}
2. {{STEP_2_SPECIFIC}}
3. {{STEP_3_SPECIFIC}}
4. {{STEP_4_SPECIFIC}}
5. {{STEP_5_SPECIFIC}}

**Capture**: {{WHAT_TO_WRITE_DOWN}}

### S2 - Reinforce ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_SOLIDIFY}}
**Do this**:
1. {{PRACTICE_EXERCISE_1}}
2. {{PRACTICE_EXERCISE_2}}
3. {{VARIATION_TO_TRY}}
4. {{VARIATION_TO_TRY}}

**Capture**: {{WHAT_IMPROVED + WHAT_IS_STILL_UNCLEAR}}

### S3 - Apply ({{SESSION_DURATION}} min)
**Objective**: {{WHAT_TO_BUILD_OR_CREATE}}
**Do this**:
1. {{CREATIVE_TASK_STEP_1}}
2. {{CREATIVE_TASK_STEP_2}}
3. {{CREATIVE_TASK_STEP_3}}
4. {{CONSTRAINT_TO_KEEP_FOCUSED}}

**Capture**: {{WHAT_WAS_BUILT + ISSUES_ENCOUNTERED}}

### S4 - Output ({{SESSION_DURATION}} min)
**Objective**: {{PRODUCE_THE_ARTIFACT}}
**Do this**:
1. {{FINALIZE_STEP_1}}
2. {{FINALIZE_STEP_2}}
3. {{QUALITY_CHECK}}
4. {{SAVE_AND_LOCATE_ARTIFACT}}

**Capture**:
- Final result: [describe what was produced]
- Artifact path: [where it lives]
- What worked: [what felt natural]
- What failed: [what was hard or wrong]
- Tomorrow hook: {{WHAT_TOMORROW_BUILDS_ON}}
{{/IF}}

---

## Progress Log

{{FOR EACH SESSION}}
### {{SESSION_LABEL}}
Recall: 
Notes: 
Insight: 
{{END FOR}}

### Final
Final result: 
Artifact path: 
Quality rating (1-5): 
What worked: 
What failed: 
Tomorrow hook: 

## Doubt Log

Questions you couldn't answer today. Reviewed in the weekly retrospective.

- [ ] Q: {{unanswered question 1}}
- [ ] Q: {{unanswered question 2}}

(Leave blank if none. Most days have at least one — writing "none" often means you didn't notice.)

{{IF CELEBRATION_DAY}}
---

## 🎉 Celebration Milestone — Day {{DAY_N}}

You've completed {{DAY_N}} days.

**Look back**:
- Play / read / run / view your artifact from Day 1
- Play / read / run / view today's artifact
- Hear / see the distance traveled

**Reflect**:
- What's the single biggest thing that's changed?
- What are you most proud of?
- What do you wish Day-1-you had known?

**Continue**:
- {{DAYS_REMAINING}} days remain in the plan
- Next milestone: Day {{NEXT_MILESTONE}}
{{/IF}}
