# TEMPLATE_STATE_JSON — Machine-Readable Progress

A JSON file at `plans/state.json` that mirrors the markdown progress in a structured format. Enables dashboards, reminders, analytics, and third-party integrations.

## Schema

```json
{
  "meta": {
    "plan_version": "1.0",
    "framework_version": "learn-anything-1.0",
    "domain": "{{DOMAIN_NAME}}",
    "learner_name": "{{LEARNER_NAME}}",
    "created": "YYYY-MM-DD",
    "last_updated": "YYYY-MM-DDTHH:MM:SSZ"
  },

  "config": {
    "total_months": 12,
    "days_per_week": 5,
    "sessions_per_day": 4,
    "session_duration_min": 15,
    "flex_days": ["Thu", "Fri"],
    "off_days": ["Sat", "Sun"],
    "tracks": ["primary", "secondary"],
    "track_mode": "mirror",
    "teaching_mode": "coach"
  },

  "progress": {
    "status": "active",
    "current_day": 47,
    "current_week": 10,
    "current_month": 3,
    "current_phase": 2,
    "phase_name": "Genre Craft",
    "phase_progress_pct": 25,
    "total_days_completed": 45,
    "total_days_skipped": 2,
    "total_days_planned": 350,
    "completion_rate": 0.94,
    "streak_current": 12,
    "streak_longest": 18,
    "last_session_date": "YYYY-MM-DD",
    "pause": null
  },

  "artifacts": {
    "total_produced": 45,
    "by_phase": {"1": 20, "2": 25},
    "by_domain": {"primary": 30, "secondary": 15},
    "top_quality": [
      {"day": 25, "name": "...", "rating": 5, "path": "..."}
    ]
  },

  "skill_levels": {
    "primary_tool": {"start": "Beginner", "current": "Intermediate", "target": "Advanced"},
    "secondary_tool": {"start": "Not started", "current": "Beginner", "target": "Intermediate"}
  },

  "retrospectives": {
    "avg_difficulty_last_4_weeks": 3.2,
    "plateau_flags": [],
    "last_retro_date": "YYYY-MM-DD"
  },

  "milestones": {
    "day_50": {"reached": false, "date": null},
    "day_100": {"reached": false, "date": null},
    "day_200": {"reached": false, "date": null},
    "day_final": {"reached": false, "date": null},
    "custom": []
  },

  "doubt_log": {
    "open_count": 3,
    "resolved_count": 12,
    "persistent_flags": []
  },

  "adaptive_adjustments": [
    {"date": "YYYY-MM-DD", "reason": "...", "adjustment": "..."}
  ]
}
```

## Update Rules (for the AI)

**After each DAY.md Final is filled**:
- Increment `progress.total_days_completed`
- Update `progress.current_day`, `current_week`, `current_month`, `current_phase`
- Update `progress.streak_current` (reset to 0 if yesterday skipped, else increment)
- Update `progress.last_session_date`
- Increment `artifacts.total_produced`, update `by_phase` and `by_domain`
- Recompute `progress.completion_rate` = `(completed + skipped) / planned_so_far`

**After each WEEK.md retrospective**:
- Update `retrospectives.avg_difficulty_last_4_weeks` (rolling avg)
- Append to `plateau_flags` if plateau detected
- Update `doubt_log.open_count` / `resolved_count`

**After each MONTH.md review**:
- Update `skill_levels.*.current`
- Append to `adaptive_adjustments` if difficulty changed

**On pause**: set `status: "paused"`, set `pause` object, freeze streak
**On resume**: set `status: "active"`, clear `pause`, add adjustment log
**On milestone hit**: set `milestones.day_XXX.reached: true` + date

## Usage

- **Humans**: ignore this file. Read markdown.
- **Dashboards**: read state.json for charts (completion rate, streak, skill levels over time)
- **Reminders**: read `progress.last_session_date` to detect overdue sessions
- **Analytics**: read `retrospectives`, `artifacts`, `adaptive_adjustments` for patterns
- **Backup**: fastest way to verify plan integrity after crashes/resumes
