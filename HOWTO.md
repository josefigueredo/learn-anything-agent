# HOWTO — Using the Learn Anything Framework

Complete guide to every feature, workflow, and file. Read top-to-bottom for first use, or jump to the section you need.

---

## Table of Contents

1. [Quick Start (5 min)](#quick-start)
2. [Full Setup Workflow](#full-setup-workflow)
3. [Daily Workflow](#daily-workflow)
4. [Weekly Workflow](#weekly-workflow)
5. [Monthly Workflow](#monthly-workflow)
6. [Phase Transitions](#phase-transitions)
7. [The 10 Built-in Systems](#the-10-built-in-systems)
7a. [Execution Modes (anti-perfectionism)](#execution-modes-anti-perfectionism)
8. [Calibration Day (Day 0)](#calibration-day-day-0)
9. [Checkpoint Days (every 4 weeks)](#checkpoint-days)
10. [Doubt Log](#doubt-log)
11. [Portfolio / Artifact Index](#portfolio)
12. [State JSON](#state-json)
13. [Teacher vs Coach Mode](#teacher-vs-coach-mode)
14. [Adaptive Difficulty](#adaptive-difficulty)
15. [Spaced Repetition](#spaced-repetition)
16. [Pause & Resume](#pause--resume)
17. [Emergency Simplification](#emergency-simplification)
18. [Plateau Detection](#plateau-detection)
19. [File Index](#file-index)
20. [Troubleshooting](#troubleshooting)

---

## Quick Start

**Goal**: Generate a personalized learning plan in 30-40 minutes.

```
1. Open Claude (or any LLM with this folder available).
2. Say: "Interview me using SETUP_INTERVIEW.md to build my learning plan."
3. Answer ~36 questions across 9 sections.
4. Say: "Now run GENERATOR_PROMPT.md to generate my full plan."
5. Open plans/01_*/01_*/01_*/DAY.md and start Session 1.
```

That's it. The framework handles everything else.

---

## Full Setup Workflow

### Step 1 — Run the Interview

Open `SETUP_INTERVIEW.md`. The AI asks you through 9 sections:

| Section | Topic | Time |
|---------|-------|------|
| A | Domain & Identity | ~3 min |
| B | Current Level & Prerequisites | ~3 min |
| C | Tools & Equipment | ~4 min |
| D | Schedule & Constraints | ~5 min |
| E | Parallel Tracks (optional) | ~3 min |
| F | References & North Stars | ~4 min |
| G | Milestones & Artifacts | ~4 min |
| H | Learning Style (incl. Teacher/Coach mode) | ~3 min |
| I | Difficulty & Progression | ~5 min |

**Tip**: Be specific. "I want to get good at music" produces a vague plan. "I want to perform a dawless song with SP-404 + MicroFreak in 12 months" produces a plan you can actually follow.

### Step 2 — Review & Validate

After the interview, the AI shows a validation summary:
- Are all placeholders filled?
- Does schedule math work (hours/day = sessions × duration / 60)?
- Do phases fit within the plan length?

Fix any inconsistencies before generating.

### Step 3 — Generate

Say: "Run GENERATOR_PROMPT.md now."

The AI generates in stages (see [Generator Stages](#generator-stages) below):
1. CLAUDE.md (your system prompt)
2. ROADMAP.md (phase-gated progression)
3. KANBAN.md (all epics upfront, Month 1 assigned)
4. LEARNING_HISTORY.md (empty, fills as you go)
5. PORTFOLIO.md (artifact index, fills as you produce)
6. state.json (machine-readable progress)
7. Calibration Day 0 (baseline)
8. Month 1 MONTH.md
9. For each Week 1-4: WEEK.md + DAY.md files (fully populated sessions)
10. Future months as MONTH.md stubs

### Step 4 — Verify Output

Quick checks:
- `ls plans/` — see folder structure
- Open any DAY.md — session instructions should be CONCRETE (not "learn X", but "press Y, observe Z")
- Open CLAUDE.md — no `{{...}}` placeholders remaining
- Open ROADMAP.md — phases with checklists

### Step 5 — Day 0 Calibration

Before Day 1, do the Calibration Day (see [Calibration Day](#calibration-day-day-0)). This creates your baseline artifact — proof of where you started.

### Step 6 — Start Day 1

Open `plans/01_.../01_.../01_.../DAY.md` and execute Session 1. Go.

---

## Daily Workflow

Every day:

```
1. Open the current day's DAY.md
2. Read Today's Goal + Background (30 sec)
3. Skim Resources (1 min)
4. For each session:
   - Read Objective
   - Execute "Do this" steps in order
   - Fill Capture section with what you noticed
5. After last session:
   - Fill Final Result, Artifact Path
   - Note Tomorrow Hook (already written — confirm it matches reality)
   - Add any unanswered questions to the Doubt Log
6. Update state.json (or let the AI do it next time you check in)
7. Move the task in KANBAN.md from IN PROGRESS → DONE
```

### If a day runs long
- Don't skip Capture — it's the actual learning
- Compress later sessions rather than delete them
- If you're 20+ min over, stop. Flag it in tomorrow's retro check.

### If a day feels too easy
- Add it to this week's retrospective under difficulty rating
- Consider a stretch goal tomorrow

### If a day feels impossible
- Stop. Go back one day. Re-read that capture.
- If still stuck, use the Doubt Log. Mark the session as INCOMPLETE.
- Emergency Simplification may trigger this week (see below)

---

## Weekly Workflow

Every Friday (or your last scheduled day):

```
1. Open this week's WEEK.md
2. Fill the Retrospective section:
   - What went well
   - What was harder than expected
   - Skill progress (any level-ups?)
   - Plateau check (stuck on anything 2+ weeks?)
   - Difficulty rating (1-5) — BE HONEST
   - Doubt Log review: are any questions still unanswered?
3. Update state.json (streak, completion rate, rating)
4. Take 5 min to rest/celebrate — you finished a week!
```

### The difficulty rating drives next week:
- **1-2** (too easy): next week adds constraints, stretch goals, or tightens time
- **3** (just right): maintain pace
- **4-5** (too hard): next week reduces scope, adds a review day, lowers quality bar

### The doubt log review:
- For each unanswered question: assign it to a future session OR link to an external resource
- Unanswered doubts that persist 2+ weeks → schedule a dedicated session to resolve

---

## Monthly Workflow

Every 4 weeks (end of month):

```
1. Open MONTH.md
2. Fill Monthly Review:
   - What went well / hard
   - Plateau check (any skill stuck 2+ months?)
   - Adaptive difficulty decision
   - Artifacts produced count
   - Streak
   - Milestones hit
3. Update Skill Level Check table (start vs end)
4. Update CLAUDE.md's master Skill Levels table
5. Run a Checkpoint Day (see below)
6. Ask the AI: "Generate next month." It runs rolling generation.
```

---

## Phase Transitions

When a phase ends (check ROADMAP.md exit criteria):

```
1. For each exit criterion: confirm met (Y/N) + evidence
2. If ALL met → move on
3. If SOME unmet:
   a. Extend phase by 1-2 weeks (adjust next month's scope), OR
   b. Move on but flag unmet criteria for revisit later
4. Log the decision in LEARNING_HISTORY.md
5. Ask AI: "Start Phase N+1" — it checks exit criteria + adapts
```

---

## The 10 Built-in Systems

Every plan has these systems baked in:

| # | System | Where | What it does |
|---|--------|-------|-------------|
| 1 | 4-session template (or 1-3) | DAY.md | Learn → Reinforce → Apply → Output |
| 2 | Artifact-per-day | DAY.md | Forces tangible output, not just time spent |
| 3 | Tomorrow Hooks | DAY.md | Chains days together, no context thrash |
| 4 | Weekly Retro | WEEK.md | Feedback loop, difficulty rating |
| 5 | Monthly Review | MONTH.md | Skill audit, plateau check, adaptation |
| 6 | Phase Gates | ROADMAP.md | Competence-based progression |
| 7 | Spaced Repetition | WEEK.md (Week 3+) | Review old skills periodically |
| 8 | Plateau Detection | Retros | Flag if stuck 2+ weeks or quality stagnates |
| 9 | Emergency Simplification | Rules | Falling-behind protocol |
| 10 | Milestone Celebrations | Day 50/100/200/etc | Intentional reflection + momentum |

Plus **5 enhancements** (what this doc adds):

| # | Enhancement | Where |
|---|-------------|-------|
| 11 | Calibration Day (Day 0) | Special pre-Day-1 session |
| 12 | Checkpoint Days (every 4 weeks) | Audit day in each month |
| 13 | Doubt Log | DAY + WEEK |
| 14 | Portfolio / Artifact Index | PORTFOLIO.md |
| 15 | State JSON | state.json |
| 16 | Teacher vs Coach Mode | Session depth toggle |
| 17 | Pause & Resume Protocol | CLAUDE.md rules |
| 18 | Difficulty Ramp Graph | ROADMAP.md |
| 19 | Smart Task IDs | GENERATOR rules |
| 20 | Prompt-Chained Generation | GENERATOR stages |
| 21 | Execution Modes (anti-perfectionism) | DAY.md header + CLAUDE.md |

---

## Execution Modes (anti-perfectionism)

The framework enforces strict separation between three mental states. Every DAY.md declares exactly one mode, and the rules for that mode apply for the whole session.

| Mode | Goal | Allowed | Forbidden |
|------|------|---------|-----------|
| **PRACTICE** | Muscle memory, workflow fluency | Repetition, defaults, rough output | Tweaking quality, swapping inputs |
| **CREATION** | Finish an end-to-end artifact | Using locked inputs, shipping | Replacing the initial choice mid-session |
| **REFINE** | Polish ONE element | Iteration, A/B, targeted fixes | Building a full artifact, scope creep |

### Why this exists

Without mode separation, learners hit a common failure loop:

> choose input → output looks rough → try to fix → skill not there yet → switch tool → repeat

The modes prevent this by declaring *before* the session starts what kind of work is happening. Quality is only judged in REFINE sessions — everywhere else, completion is the only success criterion.

### Core rules (when strict mode is ON — Interview Section H)

- **First acceptable = final.** In CREATION, the first workable input is locked for the session. No hunting for a better one.
- **Rough is success.** PRACTICE and CREATION artifacts can be ugly and still count.
- **No tool escaping.** If the tool feels limiting, log it in the Doubt Log and finish anyway. Don't switch tools to escape.
- **Safe starter set.** Pick 2-3 defaults per phase (template, reference, kit, dataset, palette) and reuse them. Configured in Interview Section H Q35.
- **Frustration protocol.** Want to restart? Don't. Finish the session and log *what I wanted to change / why I couldn't / what I learned anyway*.

### Cross-domain examples

| Domain | PRACTICE day | CREATION day | REFINE day |
|--------|--------------|--------------|------------|
| Music production | "SP-404 sampling workflow" | "Finish 16-bar lofi loop" | "Improve kick drum with EQ + saturation" |
| Programming | "Learn Python list comprehensions" | "Ship a CLI script that parses a CSV" | "Refactor one function for readability" |
| Language (Spanish) | "Drill 20 irregular verbs" | "Write a 1-paragraph journal entry" | "Revise yesterday's entry with native-speaker phrasing" |
| Visual art | "30 thumbnail sketches" | "Finish one value study, single session" | "Glaze the shadows on last week's piece" |

### Mode assignment cheat sheet

- Week 1 of any phase → mostly PRACTICE
- Genre / production / end-to-end days → CREATION
- Days explicitly about mixing/editing/debugging/revising ONE thing → REFINE
- Review / retrospective / theory days → PRACTICE

When ambiguous: default PRACTICE in Phase 1, CREATION in Phase 2+.

### Opting out

If Interview Section H Q34 answered "no", modes are still declared on each DAY but treated as guidance rather than hard constraint. First-acceptable-is-final and Scope Lock become recommendations, not rules.

---

## Calibration Day (Day 0)

**Purpose**: Baseline artifact. Proof of where you started.

**When**: Before Day 1. Takes ~1 hour.

**What you do**:
1. With your tools, produce whatever you can RIGHT NOW — 30 sec video, 1 paragraph of code, a quick sketch, 30 sec of playing
2. Save it as `plans/00_calibration/artifact.{ext}`
3. Fill `plans/00_calibration/CALIBRATION.md`:
   - What you produced
   - What it took
   - How you felt
   - What you believe you'll be able to do in 6 months / end of plan

**Why it matters**:
- At Day 50/100/200/end, you play this back-to-back with a new artifact
- Growth becomes UNDENIABLE (not just "I feel better")
- Motivation fuel when you hit plateaus

**Template**: `TEMPLATE_CALIBRATION.md`

---

## Checkpoint Days

**Purpose**: Honest audit every 4 weeks. Surfaces gaps the weekly retro hides.

**When**: Last day of each month. Takes 1 hour.

**What you do**:
1. Open `plans/XX_month/CHECKPOINT.md` (generated with the month)
2. Audit 4 dimensions:
   - **Time**: did you actually do sessions, or just check them off?
   - **Quality**: play your week 1 artifact vs week 4 — real improvement?
   - **Depth**: can you EXPLAIN what you learned, or just execute?
   - **Honesty**: which skill level ratings are inflated?
3. Score each dimension 1-5
4. If any is ≤ 2: flag for immediate action
5. Decide ONE thing to change next month

**Why it matters**: Weekly retros capture vibes. Monthly checkpoints capture reality.

**Template**: `TEMPLATE_CHECKPOINT.md`

---

## Doubt Log

**Purpose**: Turn confusion into curriculum.

**How it works**:
- Every DAY.md has a Doubt Log section at the bottom
- When a session ends and something is unclear, write the question
- Don't skip — unanswered questions compound into knowledge gaps
- Weekly retro reviews all doubts from the week
- Each doubt gets: (a) answered now, (b) scheduled for later, (c) linked to resource, (d) flagged as persistent (triggers dedicated session)

**Example entries**:
- "Why does the filter squeal at 80% resonance?"
- "When do I use `await` vs `.then()`?"
- "What's the difference between imperfect and preterite in Spanish?"

**Where**: TEMPLATE_DAY.md + TEMPLATE_WEEK.md retrospective

---

## Portfolio

**Purpose**: Living index of every artifact you produce.

**Structure**: `plans/PORTFOLIO.md`

```
| Day | Phase | Domain | Artifact | Path | Quality /5 | Notes |
|-----|-------|--------|----------|------|-----------|-------|
```

**Rules**:
- Updated automatically when DAY.md Final section is filled
- Each entry links back to the DAY.md where it was made
- Sortable by phase/quality/domain
- At milestones, you can filter "show me my top 10"

**Template**: `TEMPLATE_PORTFOLIO.md`

---

## State JSON

**Purpose**: Machine-readable progress for dashboards, reminders, analytics.

**Structure**: `plans/state.json`

```json
{
  "plan_start": "2026-04-14",
  "current_day": 47,
  "current_phase": 2,
  "current_month": 2,
  "streak": 12,
  "completion_rate": 0.94,
  "artifacts_produced": 45,
  "skill_levels": {...},
  "plateau_flags": [],
  "last_updated": "2026-05-31"
}
```

**Rules**:
- Updated at the end of each day
- Read by future dashboards, third-party tools, analytics
- NOT a replacement for markdown — it's a MIRROR

**Template**: `TEMPLATE_STATE_JSON.md`

---

## Teacher vs Coach Mode

**Purpose**: Match the session depth to your learning style.

**Set during interview (Section H)**:

| Mode | Session 1 Style |
|------|----------------|
| **Teacher** | Deep explanation of concepts before action. More theory, more "why". |
| **Coach** | Brief context, jump to action. Less explanation, more doing. |

**Switch mid-plan**: Update CLAUDE.md's Learning Style field. Next generated DAYs adapt.

**Hybrid**: Some learners want Teacher for Week 1 of each phase, Coach the rest. Set in interview.

---

## Adaptive Difficulty

**Purpose**: Plan adjusts to YOU, not the other way around.

**Trigger**: Weekly retrospective difficulty rating (1-5)

| Rating | Next Week Adjustment |
|--------|---------------------|
| 1 | Add 2 stretch goals, tighten time, add constraint |
| 2 | Add 1 stretch goal |
| 3 | Maintain — plan as written |
| 4 | Reduce subtasks by 1-2 per day |
| 5 | Reduce scope, add review day, lower quality bar temporarily |

Average difficulty across 4 weeks drives monthly adjustment (MONTH.md review).

---

## Spaced Repetition

**Purpose**: Keep old skills alive as you learn new ones.

**How**: Starting Week 3, one session per week is a REVIEW of a skill from 4+ weeks ago.

**Rules**:
- REVIEW sessions use the original topic with current-week context
- Rate: is the skill still fluent?
- If not: schedule a refresh week

Marked in WEEK.md table with status "REVIEW".

---

## Pause & Resume

**Purpose**: Life happens. Don't let a disruption become abandonment.

**Pause protocol**:
1. Mark current day as PAUSED in DAY.md
2. Update state.json: `{"status": "paused", "paused_at": "YYYY-MM-DD", "reason": "..."}`
3. Write 1-3 lines in LEARNING_HISTORY.md about why
4. Walk away guilt-free

**Resume protocol** (within 2 weeks):
1. Re-read last 3 days' DAY.md
2. Do NOT make up missed days — resume from current day
3. Mark paused days as SKIPPED
4. Optionally: add a "re-entry" session to re-warm up

**Resume protocol** (2+ weeks paused):
1. Ask AI: "I paused for X weeks. Help me re-plan."
2. AI may: (a) repeat last completed week, (b) shift roadmap forward, (c) trigger Emergency Simplification for next week

---

## Emergency Simplification

**Purpose**: Falling behind 3+ days protocol.

**Trigger**: Missed 3+ scheduled sessions in a week.

**Protocol**:
1. Skip all flex days for current week
2. Compress remaining days (combine subtasks from 2 days → 1)
3. Reduce to minimum 2 sessions/day (drop Reinforce)
4. Focus on Apply + Output only for familiar topics
5. Resume normal pace next week
6. DO NOT skip retrospective — diagnose root cause

---

## Plateau Detection

**Purpose**: Catch stagnation early.

**Signals** (any 2+ in 3 weeks triggers plateau response):
- Same "what was hard" noted 3 weeks
- Artifact quality feels stagnant
- Motivation drops below 3/5
- Skill level hasn't moved in 2 months

**Response**:
- Switch approach (tutorial → project, solo → partner, structured → experimental)
- Find new resource / different teacher
- Deliberately easy week to rebuild confidence
- Ask for peer feedback

---

## File Index

| File | Purpose | Frequency of use |
|------|---------|------------------|
| `README.md` | Landing page | Once |
| `HOWTO.md` | This guide | Reference anytime |
| `SETUP_INTERVIEW.md` | Interview script | Once at setup |
| `GENERATOR_PROMPT.md` | Meta-prompt for plan generation | Once at setup + monthly |
| `TEMPLATE_CLAUDE.md` | System prompt template | Filled once |
| `TEMPLATE_ROADMAP.md` | Roadmap template | Filled once |
| `TEMPLATE_MONTH.md` | Month template | Filled per month |
| `TEMPLATE_WEEK.md` | Week template | Filled per week |
| `TEMPLATE_DAY.md` | Day template | Filled per day |
| `TEMPLATE_KANBAN.md` | Kanban template | Filled once, updated continuously |
| `TEMPLATE_PORTFOLIO.md` | Artifact index | Updated per day |
| `TEMPLATE_STATE_JSON.md` | Machine state schema | Updated per day |
| `TEMPLATE_CALIBRATION.md` | Day 0 baseline | Filled once |
| `TEMPLATE_CHECKPOINT.md` | 4-week audit | Filled per month |
| `EXAMPLES.md` | Sample plans | Reference only |

---

## Generator Stages

The GENERATOR_PROMPT.md runs in sequential stages to avoid token limits:

| Stage | What | Token budget |
|-------|------|-------------|
| 1 | CLAUDE.md + ROADMAP.md + KANBAN (structure) | Small |
| 2 | Calibration Day + state.json + PORTFOLIO skeleton | Small |
| 3 | Month 1 MONTH.md + Week 1 WEEK.md + Week 1 DAY files | Large |
| 4 | Week 2 WEEK.md + Week 2 DAY files | Large |
| 5 | Week 3 WEEK.md + Week 3 DAY files (first REVIEW day) | Large |
| 6 | Week 4 WEEK.md + Week 4 DAY files + CHECKPOINT | Large |
| 7 | Future months as MONTH.md stubs | Small |

Each stage produces intermediate output. Learner can pause generation between stages.

---

## Troubleshooting

### "My DAY.md sessions are vague"
The generator didn't fully populate. Ask AI: "Re-generate Day X with concrete step-by-step instructions referencing my tools."

### "I'm falling behind"
Read [Emergency Simplification](#emergency-simplification). Don't abandon — adjust.

### "Skill levels feel inflated"
Use [Checkpoint Day](#checkpoint-days) honesty audit. Rate harshly.

### "I don't know what to do on flex days"
Flex days are optional. If you don't have time, skip guilt-free. If you do, repeat a scheduled day or free-practice.

### "Doubt log is getting long"
Good. Triage in weekly retro: answer now (30 sec each), schedule (future session), link to resource, or flag as persistent.

### "Plan is too long / too short"
Check CLAUDE.md phase count and plan length. Ask AI: "Adjust plan length to N months" — it recalibrates scope.

### "I want to switch tools mid-plan"
Update CLAUDE.md's Tools section. Ask AI: "I'm switching from X to Y. Adjust next month's generation." Past artifacts stay in Portfolio.

### "I want to pause for vacation"
See [Pause & Resume](#pause--resume).

### "A phase exit criterion is impossible"
Flag in ROADMAP.md with strikethrough + note. Move on. Update CLAUDE.md. Imperfect plans beat abandoned ones.

### "I finished the plan early"
Congrats. Options:
- Continue Phase 5 deeper (catalog, advanced projects)
- Start a new plan with this as prerequisite
- Shift to teaching others (strongest retention)

---

## Meta: How This Framework Works

The framework solves 5 problems that plague learning plans:

1. **Vague tasks** → S1-S4 forces concrete steps
2. **No feedback** → Weekly retro + difficulty rating
3. **No adaptation** → Adaptive difficulty + plateau detection
4. **No proof of growth** → Calibration + Portfolio + artifacts
5. **Abandonment** → Pause/Resume + Emergency Simplification

You don't need discipline for a broken plan. You need a plan that fits.
