# Workout Plan Template Resource

A built-in, read-only workout plan template with a full preview of its sessions and exercises. All text fields are in
the request locale (`fa` or `en`).

```json
{
  "id": 1,
  "slug": "full-body-3x-beginner",
  "title": "تمام بدن — ۳ روز (مبتدی)",
  "description": "سه جلسهٔ تمام بدن در هفته ...",
  "level": "beginner",
  "location": "gym",
  "days_per_week": 3,
  "session_count": 3,
  "exercise_count": 16,
  "sessions": [
    {
      "day": "saturday",
      "title": "تمام بدن A",
      "description": null,
      "exercises": [
        {
          "exercise_id": 41,
          "exercise_title": "Goblet Squat",
          "exercise_translated_title": "اسکوات گابلت",
          "set_count": 3,
          "rep_count": 10,
          "rep_count_max": 12,
          "set_type": "straight",
          "drop_count": null,
          "drop_percent": null,
          "mini_set_count": null,
          "pause_seconds": null,
          "tempo": null,
          "rest_seconds": 90,
          "description": null,
          "group_ref": null,
          "group_type": null,
          "group_rest_seconds": null
        }
      ]
    }
  ]
}
```

## Template fields
| Field            | Type        | Description                                                                 |
|------------------|-------------|-----------------------------------------------------------------------------|
| `id`             | int         | Send as `workout_plan_template_id` to create a plan from this template.     |
| `slug`           | string      | Stable identifier, identical across environments (ids may differ).          |
| `title`          | string      | Localized title.                                                            |
| `description`    | string/null | Localized description.                                                      |
| `level`          | string      | `beginner`, `intermediate` or `advanced`.                                   |
| `location`       | string      | `gym` or `home` (`home` needs no gym equipment).                            |
| `days_per_week`  | int         | Training days per week; equals `session_count`.                             |
| `session_count`  | int         | Number of sessions.                                                         |
| `exercise_count` | int         | Exercises across all sessions.                                              |
| `sessions`       | array       | Sessions in week order (Saturday first), see below.                         |

## Session fields
| Field         | Type        | Description                                           |
|---------------|-------------|-------------------------------------------------------|
| `day`         | string      | `saturday` … `friday`.                                |
| `title`       | string      | Localized session title.                              |
| `description` | string/null | Localized session description.                        |
| `exercises`   | array       | Exercises in prescribed order, see below.             |

## Exercise fields
| Field                       | Type        | Description                                                                                         |
|-----------------------------|-------------|-----------------------------------------------------------------------------------------------------|
| `exercise_id`               | int         | Catalog exercise. Templates always use catalog exercises, never custom names.                       |
| `exercise_title`            | string      | Catalog title (English).                                                                            |
| `exercise_translated_title` | string      | Catalog title in the request locale (falls back to the English title until a translation exists).  |
| `set_count`                 | int         | Prescribed sets.                                                                                    |
| `rep_count`                 | int         | Reps, or the lower bound of a range.                                                                |
| `rep_count_max`             | int/null    | Upper bound of a rep range.                                                                         |
| `set_type`                  | string      | Set technique — same values and parameters as a [plan exercise](../workout-plans/sessions/exercises/workout_plan_exercise_resource.md). |
| `drop_count`, `drop_percent`         | int/null | `drop_set` parameters.                                                                 |
| `mini_set_count`, `pause_seconds`    | int/null | `rest_pause` / `cluster` parameters.                                                   |
| `tempo`                     | string/null | Four-character tempo, e.g. `3010`.                                                                  |
| `rest_seconds`              | int/null    | Rest after this exercise.                                                                           |
| `description`               | string/null | Localized coaching note.                                                                            |
| `group_ref`                 | string/null | Exercises of one session sharing a ref form one group (superset, circuit, …) in the copied plan.   |
| `group_type`                | string/null | `superset`, `tri_set`, `giant_set` or `circuit`; the same on every member of a group.               |
| `group_rest_seconds`        | int/null    | Rest after one full round of the group.                                                             |
