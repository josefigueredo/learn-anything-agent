# Generator Prompt — Learn Anything Plan Builder

You (the AI agent) have completed the Setup Interview and have all learner parameters. Your job is to generate the COMPLETE learning plan folder structure.

This prompt covers two modes: **Initial Generation** (run once after interview) and **Rolling Generation** (run at the end of each month).

---

## Mode 1: Initial Generation

### Step 1 — Generate CLAUDE.md

- Load `TEMPLATE_CLAUDE.md`
- Fill every `{{PLACEHOLDER}}` with interview answers
- Build the Weekly Schedule table from `SCHED_ON_DAYS` + `SCHED_FLEX_DAYS` + `SCHED_TRACK_DISTRIBUTION`
- Build the Skill Levels table from Section B answers
- Build the Roadmap phases block from Section I answers — each phase gets a header, goal, and exit criteria
- Compute `{{FINAL_DAY}}` = `CONSTRAINT_DAYS_PER_WEEK * WEEKS * MONTHS`
- **Validate**: grep for any remaining `{{...}}` — must be zero
- Write to `plans/CLAUDE.md` (or the project root)

### Step 2 — Generate ROADMAP.md

- Load `TEMPLATE_ROADMAP.md`
- For each phase, create a section with the phase name, goal, duration, and exit criteria
- Create the Phase Summary table
- Write to `plans/ROADMAP.md`

### Step 3 — Generate KANBAN.md

- Load `TEMPLATE_KANBAN.md`
- Create ALL epics for ALL phases upfront (read from the roadmap)
- For Month 1: assign specific week/day to each task
- For future months: list tasks under their epic but without week/day assignment
- Task ID convention:
  - Primary track: `{{ID_PREFIX_TRACK_1}}-T{N}`
  - Secondary track (if enabled): `{{ID_PREFIX_TRACK_2}}-T{N}`
  - Epic-specific: derive 2-4 letter prefix from epic name
- Write to `plans/KANBAN.md`

### Step 4 — Generate LEARNING_HISTORY.md

- Create with empty sections for each domain category
- Write to `plans/LEARNING_HISTORY.md`

### Step 5 — Generate Month 1

#### 5a. MONTH.md
- Load `TEMPLATE_MONTH.md`
- Derive Month 1 goals from Phase 1
- Build weekly breakdown table (one row per week)
- List end-of-month milestones (derived from phase exit criteria)
- Check for celebration days (Day 50 in Month 2-3 typically, adjust based on days/week)
- Build Skill Level Check table (start values from interview Section B)
- Write to `plans/01_{{month1_theme}}/MONTH.md`

#### 5b. For each WEEK in Month 1:

##### WEEK.md
- Load `TEMPLATE_WEEK.md`
- Fill the day table — one row per scheduled/flex day
- Include 2-4 subtasks per day (extracted from the epic's natural subdivisions)
- Mark flex days as `FLEX` in Status
- If week 3+: check spaced repetition schedule, add REVIEW rows
- Add Resources section with 1-2 general resources for the week's topic
- Write to `plans/01_{{month1_theme}}/{{week_N}}_{{week_focus}}/WEEK.md`

##### For each DAY in the week:

###### DAY.md — **CRITICAL: FULLY POPULATE ALL SESSIONS**

This is the most important generation step. Do NOT leave sessions as templates.

Load `TEMPLATE_DAY.md`. For each session's "Do this" section:

1. Write **concrete, numbered steps** (not abstract instructions)
2. Reference the learner's **specific tools** (from `TOOL_LIST`)
3. Include **domain-specific terminology** they'll encounter
4. Make steps **actionable without external help** — the learner should be able to follow the day without searching
5. Use **imperative voice** — "Press X", "Open Y", "Write Z"
6. Include **what to observe / note / capture** at each step
7. Reference **specific menus, buttons, commands, concepts** where possible

**Example of BAD "Do this"** (vague):
```
1. Learn about variables
2. Practice variables
3. Create a script
```

**Example of GOOD "Do this"** (concrete):
```
1. Open VS Code, create a new file called `day01.py`
2. On line 1, type: `name = "Alice"` — this creates a string variable
3. On line 2, type: `age = 30` — this creates an integer
4. On line 3, type: `print(f"{name} is {age} years old")`
5. Save with Ctrl+S, run with F5, observe the output
6. Change the values and re-run. Note how formatting updates.
```

Additional DAY.md fields:
- **MODE**: exactly one of PRACTICE / CREATION / REFINE. Infer using the guidance in CLAUDE.md "Execution Modes" section. Heuristic: foundational/anatomy/theory/workflow days → PRACTICE; end-to-end production days → CREATION; isolated polishing of one element → REFINE. Default Phase 1 → PRACTICE, Phase 2+ → CREATION, when ambiguous.
- **Success Condition**: one line, completion-framed, NOT quality-framed. Good: "8-bar loop records clean start to end", "script prints expected output", "50 new words reviewed". Bad: "loop sounds good", "script is elegant", "pronunciation is correct". Derive from Expected Output by asking "what action proves this was completed?"
- **Scope Lock**: if MODE == CREATION, name the single locked input (starter file, kit, reference, dataset, palette, vocabulary set) drawn from `{{SAFE_STARTER_SET}}` if available. If MODE != CREATION, write `N/A`.
- **Tomorrow Hook**: Must connect to the next day's topic — brief, specific
- **Resources**: 1-2 relevant links/references for today's topic
- **Cross-Track Note** (if parallel tracks): what the other track is doing this week, how today's topic relates
- **Review marker** (if spaced repetition day): reference to the original day being reviewed
- **Celebration block** (Day 50/100/200/etc): reflection prompt with specific questions

Write each to `plans/01_{{month1_theme}}/{{week_N}}_{{week_focus}}/{{day_N}}_{{day_topic}}/DAY.md`.

### Step 6 — Generate Future Months (stub only)

For Month 2 through Month N:
- Create only `plans/{{month_N}}_{{month_theme}}/MONTH.md`
- Fill Goals (from phase), Weekly Breakdown (high-level), Milestones
- Do NOT create WEEK.md or DAY.md files yet
- These are generated in Rolling Mode when the learner reaches that month

### Step 7 — Create Folder Structure

Final tree:
```
plans/
  CLAUDE.md (if not at project root)
  KANBAN.md
  LEARNING_HISTORY.md
  ROADMAP.md
  01_{{month1_theme}}/
    MONTH.md
    01_{{week1_focus}}/
      WEEK.md
      01_{{day1_topic}}/
        DAY.md
      02_{{day2_topic}}/
        DAY.md
      ...
    02_{{week2_focus}}/
      WEEK.md
      01_.../
        DAY.md
      ...
  02_{{month2_theme}}/
    MONTH.md  (stub only)
  03_{{month3_theme}}/
    MONTH.md  (stub only)
  ...
```

### Step 8 — Validate

Before delivering, verify:
- [ ] CLAUDE.md has zero remaining `{{...}}` placeholders
- [ ] KANBAN has all epics for all phases
- [ ] Month 1 has all weeks and days populated
- [ ] Every DAY.md has fully written session instructions (not templates)
- [ ] Every DAY.md declares a MODE (PRACTICE | CREATION | REFINE), Success Condition (completion-framed, not quality-framed), and Scope Lock (concrete for CREATION, N/A otherwise)
- [ ] Session count in each DAY matches `SCHED_SESSIONS_PER_DAY`
- [ ] Session duration matches `SCHED_SESSION_DURATION_MIN`
- [ ] Flex days are marked as FLEX in WEEK tables
- [ ] OFF days have no folders
- [ ] Task IDs are unique and consistent between KANBAN and DAY files
- [ ] Tomorrow hooks chain correctly (Day N's hook connects to Day N+1's topic)
- [ ] Spaced repetition sessions scheduled from Week 3+
- [ ] Celebration milestones marked on appropriate days (50, 100, 200, final)
- [ ] Resources section exists on each DAY
- [ ] Week 1 Day 1 has an especially clear intro — the learner's first day

### Step 9 — Present Summary

Tell the learner:
- Total plan length (months, weeks, sessions)
- Number of phases
- Month 1 scope (what they'll learn in the first month)
- Today's first task (Day 1)
- How to begin: "Open `plans/01_.../01_.../01_.../DAY.md` and start Session 1"

---

## Mode 2: Rolling Generation (end of each month)

Run at the end of a month to generate the next month's full structure.

### Step R1 — Check Phase Exit Criteria

If the current phase is ending:
- Review all exit criteria in ROADMAP.md
- Ask the learner to confirm each one
- If any criteria NOT met:
  - Option A: extend current phase by 1-2 weeks (adjust next month's scope)
  - Option B: move on but flag unmet criteria for revisit
- Log the decision in LEARNING_HISTORY.md

### Step R2 — Read Retrospectives

Scan all WEEK.md retrospectives from the completed month:
- Collect difficulty ratings (target: average should trend toward 3)
- Collect "what was hard" entries (look for repeating patterns)
- Collect "what went well" (reinforce these approaches)
- Identify plateaus (same difficulty noted 2+ weeks)

### Step R3 — Adaptive Difficulty Adjustment

Based on retrospective data:
- **Avg difficulty 4-5** (too hard): Next month reduces scope per week, adds a review day each week, lowers quality bar temporarily
- **Avg difficulty 1-2** (too easy): Next month adds stretch goals, tightens time allowance, introduces a new constraint
- **Avg difficulty 3** (just right): Maintain current pace, follow the roadmap as planned
- **Plateau detected**: Change the exercise format (tutorial → project, or solo → partner, or structured → experimental)

### Step R4 — Generate Next Month

Follow Steps 5-7 from Initial Generation for the next month:
- Replace the stub MONTH.md with full content
- Create all WEEK.md files
- Create all DAY.md files with fully-populated sessions
- Update KANBAN — move next month's tasks from TODO (unassigned) to TODO (with week/day assignments)

### Step R5 — Skill Level Audit

Update skill levels in MONTH.md (end values for completed month, start values for next month):
- Ask the learner to rate each domain honestly
- Record level changes
- Update CLAUDE.md's master Skill Levels table

### Step R6 — Milestone Check

If this month contained Day 50/100/200 etc:
- Verify the celebration reflection happened
- Read the reflection from the DAY.md
- Incorporate insights into next month's approach

### Step R7 — Present Next Month

Tell the learner:
- Last month's summary (completion rate, artifacts produced, skills leveled up)
- Any difficulty adjustments made and why
- Next month's focus and first task
- How to begin next month

---

## Session Label Rules

Derive labels from `SCHED_SESSIONS_PER_DAY`:

| Sessions/Day | Labels | Description |
|--------------|--------|-------------|
| 1 | Focus | Combined learn + apply + output, compressed |
| 2 | Learn, Apply | Understand, then build |
| 3 | Learn, Apply, Output | Understand, build, finalize |
| 4 | Learn, Reinforce, Apply, Output | Full pipeline with reinforcement |

---

## Error Handling

If the interview is incomplete (some answers missing):
- Flag each missing placeholder
- Suggest reasonable defaults (e.g., "No parallel track specified → defaulting to single track")
- Ask the learner to confirm defaults before generating

If the learner's configuration is inconsistent:
- Flag the inconsistency (e.g., "4 sessions × 15 min = 60 min, but hours/day is 2")
- Ask for clarification
- Do NOT generate with bad config

If a domain is extremely niche and the AI lacks knowledge:
- Be honest: "I can generate the framework, but you'll need to source domain-specific steps"
- Generate with placeholder steps the learner fills in
- Suggest finding a domain expert or course to supplement

---

## Output Quality Bar

Every generated plan must:
- Be immediately actionable — Day 1 Session 1 can start without any further setup
- Be honest — if the AI doesn't know something domain-specific, say so
- Be personal — reference the learner's name, tools, goals throughout
- Be complete — all 10 files created, folder structure valid
- Be consistent — task IDs match across KANBAN and DAYs, phases align with months

A good test: send the generated Day 1 DAY.md to a friend in that domain. Ask: "Could you do this with zero context from me?" If yes, the generation succeeded.

---

## Prompt-Chained Staged Generation

For reliability on long plans (6-12 months), execute generation in SEQUENTIAL STAGES instead of one massive prompt. This avoids token limits and lets the learner pause/review between stages.

Tell the learner before starting: "I'll generate your plan in 7 stages. You can pause between any stage."

### Stage 1 — Foundation Files (small)

Generate and save:
1. `plans/CLAUDE.md` (from TEMPLATE_CLAUDE.md + interview answers)
2. `plans/ROADMAP.md` (from TEMPLATE_ROADMAP.md)
3. `plans/KANBAN.md` (from TEMPLATE_KANBAN.md — all epics for all phases, Month 1 assigned)
4. `plans/LEARNING_HISTORY.md` (empty with section headers)
5. `plans/PORTFOLIO.md` (empty with schema from TEMPLATE_PORTFOLIO.md)
6. `plans/state.json` (initial state with day=0, phase=0, status="setup")

Checkpoint: show learner the generated CLAUDE.md. Confirm before continuing.

### Stage 2 — Calibration + Month 1 Stub

Generate:
1. `plans/00_calibration/CALIBRATION.md` (from TEMPLATE_CALIBRATION.md)
2. `plans/01_{{month1_theme}}/MONTH.md` (full month goals + weekly breakdown table)

Checkpoint: learner can do Calibration Day now OR wait.

### Stage 3 — Week 1 (full populate)

Generate:
1. `plans/01_{{month1_theme}}/01_{{week1_focus}}/WEEK.md`
2. All DAY.md files for Week 1 (5-7 files depending on days/week) — fully populated sessions

CRITICAL: sessions must have concrete steps, not templates. See quality bar above.

Checkpoint: learner reviews Day 1 DAY.md. This is the biggest quality test.

### Stage 4 — Week 2 (full populate)

Same as Stage 3 for Week 2. Update Tomorrow Hooks to chain cleanly from Week 1 end.

### Stage 5 — Week 3 (with first REVIEW session)

Same as Stage 3-4 for Week 3. **First spaced repetition day** — schedule a REVIEW session for a Week 1 skill.

### Stage 6 — Week 4 + Checkpoint

Generate:
1. Week 4 WEEK.md + DAY.md files
2. `plans/01_{{month1_theme}}/CHECKPOINT.md` (from TEMPLATE_CHECKPOINT.md — scheduled for the last day of the month)

### Stage 7 — Future Month Stubs

For Months 2 through N:
- Create `plans/{{N}}_{{theme}}/MONTH.md` with goals + weekly breakdown (high-level)
- Do NOT create WEEK.md or DAY.md files — generated via Rolling Generation when the learner reaches that month

Final validation (from Step 8 above).

---

## Smart Task ID Derivation

Task IDs must be memorable and semantic. Rules for deriving:

1. **Epic-based prefix**: take 3-5 letters from epic name
   - "SP-404MKII Sampling" → `SP404`
   - "Lofi Production" → `LOFI`
   - "Python Data Structures" → `PYDS`
   - "Spanish Vocabulary" → `VOCAB`
   - "Watercolor Basics" → `WC`

2. **Sequential suffix**: `-T{N}` where N starts at 1 per epic
   - `LOFI-T1`, `LOFI-T2`, `LOFI-T3`

3. **DAW/parallel-track prefix**: add track marker if needed
   - `LOFI-D1` (DAW track for lofi)
   - `VOCAB-S1` (Speaking track for vocab)

4. **Uniqueness**: every ID must be unique across ENTIRE plan. If a conflict, extend prefix
   - `BB-T1` (Boom bap) vs `BASS-T1` (Bass line) — extend to `BBAP-T1` vs `BASS-T1`

5. **Readability**: a learner scanning KANBAN should guess what the task is from the ID

Avoid generic prefixes like `TASK-T1` or `DAY-T47`. Specificity makes the KANBAN scannable.

---

## New Template References

The generator uses these additional templates:

| Template | When |
|----------|------|
| TEMPLATE_CALIBRATION.md | Stage 2 — Day 0 baseline |
| TEMPLATE_CHECKPOINT.md | Stage 6 — every month end |
| TEMPLATE_PORTFOLIO.md | Stage 1 — initial setup, updated per DAY Final |
| TEMPLATE_STATE_JSON.md | Stage 1 — state.json schema, updated per DAY |

All DAY.md files must include a Doubt Log section (from TEMPLATE_DAY.md).
All WEEK.md files must include a Doubt Log Review in the retrospective.
All DAY.md Teacher mode produces deeper S1 instructions; Coach mode produces brief S1.

---

## Per-Stage Context Strategy

Between stages, save checkpoints to disk. Each subsequent stage reads:
- Interview answers (cached)
- Stage 1 output (CLAUDE.md — authoritative source for all placeholders)
- Previous stage output (for Tomorrow Hook chaining)

DON'T re-generate earlier stages. Read them as input. Each stage is append-only.
