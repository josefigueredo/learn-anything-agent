# Setup Interview

The AI agent (Claude) runs this interview to gather everything needed to generate your personalized learning plan. Answers fill placeholders in `TEMPLATE_CLAUDE.md` and the other templates.

**To the AI**: Ask questions ONE SECTION AT A TIME. Wait for answers. Probe with follow-ups if the answer is vague. Validate at the end. When all sections are complete, summarize the answers and ask: "Ready to generate your plan?" before running `GENERATOR_PROMPT.md`.

**To the learner**: Be specific. Vague answers produce vague plans. If you don't know an answer, say so — the AI can suggest defaults.

---

## Section A — Domain & Identity

Maps to: CLAUDE.md role declaration, Context > Goals, Priority.

1. **What skill do you want to learn?** (one sentence)
   → `{{DOMAIN_NAME}}`, `{{DOMAIN_DESCRIPTION}}`

2. **In one sentence, describe where you want to be at the end of this plan.**
   → `{{GOAL_PRIMARY}}`

3. **Are there 2-3 secondary goals or sub-goals?**
   → `{{GOAL_SECONDARY_1}}`, `{{GOAL_SECONDARY_2}}`, `{{GOAL_SECONDARY_3}}`

4. **What's your motivation? Why now?**
   → `{{LEARNER_MOTIVATION}}` (used in DAY Background sections)

**Validation**: Primary goal must be specific and measurable ("play a complete dawless song" ✓, "get good at music" ✗).

---

## Section B — Current Level & Prerequisites

Maps to: Skill Levels table, prerequisite skipping.

5. **Rate your current ability**: Complete beginner / Some exposure / Can do basics / Intermediate / Advanced
   → `{{SKILL_STARTING_LEVEL}}`

6. **Have you tried learning this before? What happened?**
   → `{{LEARNER_HISTORY}}` (used to avoid past failure modes)

7. **What related skills do you already have?**
   → `{{LEARNER_PREREQUISITES}}` (used to skip basics you already know)

8. **Is there anything you specifically do NOT want to cover?**
   → `{{LEARNER_EXCLUSIONS}}` (e.g., "no music theory", "no vim basics")

**Validation**: If "Advanced" is chosen but starting from scratch makes no sense, probe for what they actually need.

---

## Section C — Tools & Equipment

Maps to: Context > Tools, Setup description, task ID prefixes.

9. **What tools / instruments / software / equipment do you have or plan to get?** (list them)
   → `{{TOOL_LIST}}`

10. **Which is your primary tool?** (the one you'll spend the most time with)
    → `{{TOOL_PRIMARY}}`

11. **Describe your setup — how do tools connect or relate to each other?**
    → `{{SETUP_DESCRIPTION}}`

12. **Are there tools you plan to add later?**
    → `{{TOOL_FUTURE}}` (incorporated into later phases)

**Validation**: At least 1 tool required. Probe if the learner hasn't thought about this.

---

## Section D — Schedule & Constraints

Maps to: Constraints, Weekly Schedule table.

13. **How many hours per day can you dedicate?** (0.5 - 4)
    → `{{CONSTRAINT_HOURS_PER_DAY}}`

14. **How many days per week?** (1-7)
    → `{{CONSTRAINT_DAYS_PER_WEEK}}`

15. **Which days of the week are ON vs OFF?** (Mon-Sun)
    → `{{SCHED_ON_DAYS}}`, `{{SCHED_OFF_DAYS}}`

16. **How many sessions per day?** (1-4, each is a focused block)
    → `{{SCHED_SESSIONS_PER_DAY}}`

17. **How long should each session be?** (10-30 min)
    → `{{SCHED_SESSION_DURATION_MIN}}`

18. **Do you want flex days?** (optional days for catch-up, not scheduled strictly)
    → `{{SCHED_FLEX_DAYS}}` (Y/N + which days)

19. **How long is your total plan?** (1-12 months)
    → `{{CONSTRAINT_PLAN_LENGTH_MONTHS}}`

**Validation**:
- `hours/day = sessions/day × session_duration / 60` — must be consistent
- Total ON + flex days must fit within 7 days/week
- Plan length must accommodate phase count (at least 1 month per phase)

---

## Section E — Parallel Tracks (optional)

Maps to: Track definitions, schedule distribution, cross-domain transfer.

20. **Do you want parallel tracks?** (e.g., theory+practice, hardware+software, reading+speaking)
    → `{{TRACK_ENABLED}}` (Y/N)

*If YES, continue:*

21. **Name each track and describe its focus.**
    → `{{TRACK_PRIMARY_NAME}}`, `{{TRACK_SECONDARY_NAME}}`

22. **How should tracks be distributed across the week?** (e.g., "Mon-Wed primary, Thu-Fri secondary")
    → `{{SCHED_TRACK_DISTRIBUTION}}`

23. **Should tracks mirror each other (same topic, different tool) or be independent?**
    → `{{TRACK_RELATIONSHIP}}` (mirror / independent)

**Validation**: Track distribution days must equal total days/week. Mirror mode requires the same topic sequence.

---

## Section F — References & North Stars

Maps to: Domain References section.

24. **Who are your role models or inspirations in this skill?** (people, works, examples)
    → `{{REF_PEOPLE}}`

25. **Are there specific styles, genres, or approaches you want to focus on?**
    → `{{REF_STYLES}}` (list)

26. **For each style/approach, describe what 'good' looks like in 1-2 sentences.**
    → `{{REF_STYLE_1_DESCRIPTION}}`, `{{REF_STYLE_2_DESCRIPTION}}`, etc.

**Validation**: At least 1 reference. If none, probe: "Who do you want to sound/code/paint/play like?"

---

## Section G — Milestones & Artifacts

Maps to: Milestones, artifact definitions.

27. **What does a 'finished piece of work' look like in this domain?**
    → `{{ARTIFACT_DEFINITION}}` (e.g., "a complete song", "a working app", "a painting")

28. **What artifacts can you produce daily?** (small outputs that count as progress)
    → `{{ARTIFACT_DAILY}}` (e.g., "a code file", "a 4-bar loop", "a sentence in Spanish")

29. **What would a major milestone look like at month 3? Month 6? End of plan?**
    → `{{MILESTONE_3}}`, `{{MILESTONE_6}}`, `{{MILESTONE_FINAL}}`

**Validation**: Daily artifacts must be achievable in one day's session budget.

---

## Section H — Learning Style & Resources

Maps to: Resources section, community.

30. **Do you prefer learning from**: videos / books / docs / courses / hands-on exploration?
    → `{{LEARNER_RESOURCE_PREF}}`

31. **Do you have specific courses/books/resources you want to follow?**
    → `{{RESOURCE_LIST}}` (linked in DAY files)

32. **Do you want an accountability / community section?** (sharing progress, finding partners)
    → `{{COMMUNITY_ENABLED}}` (Y/N + platform preference)

33. **Teacher mode or Coach mode?**
    - **Teacher**: S1 (Learn) sessions have deeper explanations before action. More "why", more theory. Good for conceptually-heavy domains (languages, mathematics, theory-heavy subjects).
    - **Coach**: S1 sessions are brief context + jump to action. Less explanation, more doing. Good for skill-based domains where you learn by doing (music, art, sports, coding).
    - **Hybrid**: Teacher for Week 1 of each phase (intro the concepts), Coach the rest (execute).
    → `{{TEACHING_MODE}}` (teacher / coach / hybrid — default: hybrid)

**Validation**: If no resources provided, the generator uses its own suggestions per day. Teaching mode defaults to `hybrid` if unspecified.

34. **Do you struggle with perfectionism, tool-hopping, or restarting mid-task?** (Y/N)
    - If YES → `{{ANTI_PERFECTIONISM_STRICT}} = yes`. Execution Modes (PRACTICE / CREATION / REFINE) are enforced strictly: first-acceptable-is-final, no tool escaping, Scope Lock mandatory for CREATION days.
    - If NO → `{{ANTI_PERFECTIONISM_STRICT}} = no`. Modes are still declared on each DAY but treated as guidance rather than hard constraint.
    - Default if unsure: `yes` (strict mode helps more than it hurts).
    → `{{ANTI_PERFECTIONISM_STRICT}}`

35. **Name 2-3 "safe starter defaults" you'll reuse this phase instead of hunting each session.** (e.g., "starter Python template", "these 3 drum kits", "this reference palette", "this vocabulary list") — prevents mid-session decision paralysis. Can be filled later if unknown now.
    → `{{SAFE_STARTER_SET}}`

**Validation**: If strict mode = yes and safe starter set is empty, flag it — the generator will prompt the learner to pick before Day 1.

---

## Section I — Difficulty & Progression

Maps to: Roadmap, phases, exit criteria, difficulty curve.

33. **How many phases do you envision?** (3-6 recommended)
    → `{{PHASE_COUNT}}`

34. **Describe each phase in a sentence.** (go in order, beginner → advanced)
    → `{{PHASE_1_NAME}}`, `{{PHASE_1_GOAL}}`, `{{PHASE_2_NAME}}`, `{{PHASE_2_GOAL}}`, etc.

35. **For each phase, what must be true before moving on?** (2-5 concrete exit criteria per phase)
    → `{{PHASE_N_EXIT_CRITERIA}}`

36. **How should difficulty increase?** (tick all that apply)
    - [ ] Reduce time allowed (e.g., 30 min task → 10 min task)
    - [ ] Add constraints (limited tools, forced styles, blind attempts)
    - [ ] Increase scope (loop → song → album)
    - [ ] Raise quality bar ("it exists" → "it's recognizable" → "it's personal")
    → `{{DIFFICULTY_ESCALATION_METHODS}}`

**Validation**:
- Phase count must be at least 2 and at most 2 × plan_length_months
- Each phase must have at least 2 exit criteria
- Exit criteria must be concrete (measurable, observable)

---

## Validation Checklist (run at end)

Before generating, the AI verifies:

- [ ] Primary goal is specific and measurable
- [ ] At least 1 tool listed
- [ ] hours/day = sessions/day × session_duration / 60
- [ ] Total days/week matches schedule configuration
- [ ] Plan length accommodates phase count (1+ month per phase)
- [ ] At least 1 reference / role model
- [ ] At least 2 exit criteria per phase
- [ ] Difficulty escalation method selected
- [ ] If parallel tracks enabled: track distribution covers all ON days
- [ ] Daily artifact is achievable in session budget

## After the interview

The AI summarizes all answers in a single block and asks: **"Ready to generate your plan?"**

On confirmation, the AI runs `GENERATOR_PROMPT.md` to produce:
1. CLAUDE.md (your personalized system prompt)
2. ROADMAP.md
3. KANBAN.md with all epics
4. Month 1 fully populated (MONTH + WEEK + DAY files)
5. Future months as MONTH.md stubs (filled when you reach them)
