# Learn Anything — AI-Powered Personalized Learning System

A framework that uses an AI agent (Claude) as a Scrum Master to generate a complete, phase-gated, daily-session learning plan for ANY skill — programming, languages, art, music, sports, cooking, mathematics, or anything else that requires deliberate practice over time.

## What this is

This folder contains templates and prompts that let an AI agent generate a fully-populated learning plan customized to YOUR goals, tools, schedule, and current skill level. The output is a folder of Markdown files — a ROADMAP, monthly plans, weekly schedules, and daily session instructions — that you follow day by day.

The system is derived from a proven 12-month music production learning plan (350 sessions, 50 weeks, 12 months) but generalized to work for any skill domain.

## How it works

1. **Run the Setup Interview** — Open `SETUP_INTERVIEW.md` and have Claude ask you the questions in order. Your answers fill in the placeholders of the templates. About 30-40 minutes.

2. **Generate your CLAUDE.md** — Claude fills `TEMPLATE_CLAUDE.md` with your interview answers, producing your personalized system prompt.

3. **Run the Generator** — Point Claude at `GENERATOR_PROMPT.md` to generate your full plan: ROADMAP, KANBAN, Month 1 MONTH/WEEK/DAY files with fully-populated session instructions.

4. **Open any DAY.md and start learning** — Each day has 1-4 sessions with step-by-step instructions. Track progress in the file. The AI agent manages ongoing planning, retrospectives, and next-month generation.

## What you get

- **CLAUDE.md** — your personalized system prompt (the AI's role + rules for your plan)
- **ROADMAP.md** — phase-gated progression with exit criteria
- **KANBAN.md** — all tasks across all phases, single source of truth
- **MONTH.md** files — monthly goals, weekly breakdown, skill audits
- **WEEK.md** files — 7-column tables with day-level tasks and subtasks
- **DAY.md** files — fully-populated session instructions (not blank templates)
- **Built-in systems**: weekly retrospectives, monthly skill audits, phase gating, adaptive difficulty, spaced repetition, plateau detection, emergency simplification, milestone celebrations

## Supported configurations

| Setting | Range | Notes |
|---------|-------|-------|
| Plan length | 1-12 months | Typical: 3-12 |
| Days per week | 1-7 | Mix scheduled + flex days |
| Sessions per day | 1-4 | 4 = full Learn/Reinforce/Apply/Output |
| Session duration | 10-30 min | 15 min default |
| Parallel tracks | 0-2 | E.g., theory+practice, hardware+software |
| Domains | Any | Music, code, language, art, sport, craft, etc. |

## Quick start

```bash
# 1. Copy the templates into your project
cp -r learn-anything/ ./my-learning-project/

# 2. Start the interview conversation with Claude
# Open SETUP_INTERVIEW.md and ask Claude:
# "Interview me using this document to build my learning plan."

# 3. After the interview, ask Claude to run the generator:
# "Now use GENERATOR_PROMPT.md to generate my full learning plan."
```

## File index

| File | Purpose |
|------|---------|
| `README.md` | This file — how to use the system |
| `HOWTO.md` | Comprehensive how-to (every feature, workflow, troubleshooting) |
| `SETUP_INTERVIEW.md` | The interview script (~37 questions in 9 sections) |
| `GENERATOR_PROMPT.md` | Meta-prompt for the AI to generate your full plan (7 staged prompts) |
| `TEMPLATE_CLAUDE.md` | The main system prompt template |
| `TEMPLATE_ROADMAP.md` | Roadmap template with difficulty ramp graph |
| `TEMPLATE_MONTH.md` | Monthly plan template |
| `TEMPLATE_WEEK.md` | Weekly schedule template with Doubt Log review |
| `TEMPLATE_DAY.md` | Daily session template (1-4 sessions) with Doubt Log |
| `TEMPLATE_KANBAN.md` | Kanban board template |
| `TEMPLATE_PORTFOLIO.md` | Living artifact index template |
| `TEMPLATE_STATE_JSON.md` | Machine-readable progress schema |
| `TEMPLATE_CALIBRATION.md` | Day 0 baseline template (proof of starting level) |
| `TEMPLATE_CHECKPOINT.md` | 4-week honest audit template |
| `EXAMPLES.md` | 3 examples: Python, Spanish, Watercolor |

## Design principles

1. **Every session is actionable** — no vague "learn X" instructions, always concrete steps
2. **Every day produces an artifact** — proof of learning, not just time spent
3. **Phase gates replace calendar gates** — you graduate when criteria are met
4. **Retrospectives are required** — weekly + monthly feedback loops
5. **Adaptive difficulty** — the plan adjusts based on your retrospective ratings
6. **Tomorrow hooks** — every day connects to the next; no context thrash
7. **Domain-agnostic** — the framework applies to any skill that requires practice

## Credits

Derived from the 12-month music production learning system at `../plans/`. That system proved the pattern works when taken seriously: 350 daily sessions turning a beginner into a battle-ready producer. This folder extracts the pattern for any learner, any skill.
