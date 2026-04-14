# Examples

Three examples showing how the templates fill in for different domains. Each shows the CLAUDE.md Context section + a sample DAY.md structure.

---

## Example 1 — Learning Python Programming

**Config**: 4 months, 1 hour/day, 5 days/week, 4 sessions, no parallel tracks

### CLAUDE.md Context
```
### Domain
Python programming — scripting, data handling, and simple applications

### Tools
- Python 3.11+, VS Code, pip, Git
- Primary: Python interpreter + VS Code

### Goals
1. Build a command-line tool I'd actually use (e.g., file organizer, habit tracker)
2. Secondary: understand OOP, work with APIs, handle data with pandas

### Priority
- Master Python syntax and data structures first
- Build toward a finishable personal project
- Develop debugging and reading-docs skills
```

### Phase Structure (4 phases)
1. **Syntax & Data Structures** (M1) — variables, types, control flow, lists/dicts
2. **Functions & OOP** (M2) — functions, modules, classes, inheritance
3. **Libraries & APIs** (M3) — stdlib, pip, requests, pandas, json
4. **Projects** (M4) — build and polish the personal tool

### Sample DAY.md (Month 1, Week 1, Day 1)
```
# DAY 1 — Variables and Types

**Task**: PY-T1
**Expected Output**: 1 Python file using 5+ variable types

## Today's Goal
Write your first Python script using variables. By the end, you can declare
int, float, str, bool, and list types and print them.

## S1 - Learn (15 min)
Do this:
1. Open VS Code, create `day01.py`
2. Read the Python docs section on basic types (link in resources)
3. Type `x = 5` — print(type(x)). Try floats, strings, bools, lists.
4. Use `input()` to capture a value; note it's always a string.
...

## S2 - Reinforce (15 min)
Do this:
1. Create 5 variables of different types
2. Print each with its type
3. Try converting: int("5"), str(5), float("3.14")
4. What happens with int("hello")? Note the error.
...

## S3 - Apply (15 min)
Do this:
1. Write a script that asks for your name, age, and hobbies (comma-separated)
2. Store each appropriately (str, int, list)
3. Print a summary sentence
...

## S4 - Output (15 min)
Finalize the script, save as `01_intro.py`, commit to Git.
```

### Task ID Convention
- `PY-T{N}` for Python core tasks
- `PROJ-T{N}` for project milestones

---

## Example 2 — Learning Spanish

**Config**: 6 months, 45 min/day, 6 days/week, 3 sessions, 2 parallel tracks (Speaking + Reading)

### CLAUDE.md Context
```
### Domain
Conversational Spanish (Latin American, Argentina focus)

### Tools
- Anki, HelloTalk, SpanishPod101, a physical notebook
- Primary: Speaking practice with native speakers

### Goals
1. Hold a 10-minute conversation with a native speaker by end of plan
2. Secondary: Read a novel in Spanish, watch Argentinian films without subtitles

### Weekly Schedule
| Day | Track | Focus |
|-----|-------|-------|
| Mon | Speaking | Vocabulary + pronunciation |
| Tue | Speaking | Grammar + conversation practice |
| Wed | Speaking | Free conversation with partner |
| Thu | Reading | Short texts + vocabulary |
| Fri | Reading | Grammar analysis + translation |
| Sat | Reading | Full article / chapter |
| Sun | OFF | OFF |
```

### Phase Structure (4 phases)
1. **Foundations** (M1) — 500 most common words, basic grammar
2. **Daily Life** (M2) — present tense mastery, everyday conversations
3. **Past & Future** (M3-4) — verb tenses, longer conversations
4. **Fluency** (M5-6) — subjunctive, idioms, full conversations

### Sample DAY.md (Week 5, Day 4 — Reading Track)
```
# DAY 25 — Reading: First Short Story

**Track**: Reading
**Task**: READ-T12
**Expected Output**: 1 short story read + vocabulary list

**Cross-Track Note**: Mirrors Speaking Day 22 (past tense) — practice recognizing
preterite vs imperfect in reading that you're learning to produce in speaking.

## S1 - Learn (15 min)
1. Open "El Libro de Arena" by Borges (first paragraph)
2. Read aloud — don't look up words yet
3. Circle 10 unknown words
4. Write each in Anki with context sentence
...
```

### Task ID Convention
- `SPEAK-T{N}` for speaking track
- `READ-T{N}` for reading track

---

## Example 3 — Learning Watercolor Painting

**Config**: 3 months, 30 min/day, 4 days/week, 2 sessions, no parallel tracks

### CLAUDE.md Context
```
### Domain
Watercolor painting — landscapes, florals, urban sketching

### Tools
- Set of 12 watercolor paints, 3 brushes (round sizes 4/8/12), cold-press paper, pencil
- Primary: paints + paper

### Goals
1. Produce a finished watercolor landscape I'd hang on a wall by end of plan
2. Secondary: learn color theory, master wet-on-wet and dry-brush techniques

### Weekly Schedule
| Day | Track | Focus |
|-----|-------|-------|
| Tue | Painting | Technique practice |
| Wed | Painting | Subject study |
| Thu | Painting | FLEX — study or sketch |
| Sat | Painting | Full painting attempt |
```

### Phase Structure (3 phases)
1. **Foundations** (M1) — color mixing, wet-on-wet, dry brush, washes
2. **Subjects** (M2) — trees, water, skies, simple florals
3. **Compositions** (M3) — full landscapes, refining style

### Sample DAY.md (Month 1, Week 1, Day 1)
```
# DAY 1 — First Washes

**Task**: WC-T1
**Expected Output**: 1 page of color washes

## S1 - Learn (15 min)
1. Set up your paper — tape edges to a board
2. Wet the paper with clean water using the large brush
3. Mix ultramarine blue + water on your palette
4. Brush a wash across the top — watch the water carry the pigment
...

## S2 - Apply (15 min)
1. On a new section, do 3 washes: very wet, medium, almost dry
2. Compare the results — label each
3. Take a photo for your progress log
...
```

### Task ID Convention
- `WC-T{N}` for watercolor core tasks
- `SUBJ-T{N}` for subject-specific practice

---

## Pattern Observations Across Examples

| Aspect | Python | Spanish | Watercolor |
|--------|--------|---------|------------|
| Sessions/day | 4 | 3 | 2 |
| Days/week | 5 | 6 | 4 |
| Duration | 4 months | 6 months | 3 months |
| Tracks | 1 | 2 (mirror) | 1 |
| Primary output | Code file | Conversation / vocab | Painting |
| Artifact cadence | Git commits | Notebook pages + audio | Scanned/photographed works |

The **framework is identical** across all three. Only the content changes.

## Built-in Features Active in All Examples

Each example automatically gets the full framework:

| Feature | Python | Spanish | Watercolor |
|---------|--------|---------|------------|
| Calibration Day 0 | Baseline code snippet | Recorded 1-min speaking | First raw painting |
| Checkpoint Days (every 4 wks) | 4-dimension audit | 4-dimension audit | 4-dimension audit |
| Doubt Log | Per DAY + weekly review | Per DAY + weekly review | Per DAY + weekly review |
| Portfolio | Code samples indexed | Recordings indexed | Paintings indexed |
| State JSON | Day/streak/skills | Same | Same |
| Teacher/Coach mode | Coach (doing > theory) | Teacher (grammar) | Coach (practice-heavy) |
| Spaced Repetition | Review concepts W3+ | Review vocab W3+ | Revisit techniques W3+ |
| Adaptive Difficulty | 1-5 rating → next week | Same | Same |
| Pause/Resume | Protocol available | Same | Same |

This is the power of the generalized framework: one system, any skill.
