# ShipIt CI

A tiny payments app with an AI review check on its pipeline. Built live in Session 5 of the WCC AI Learning Series.

| Path | What it is |
| --- | --- |
| `.agents/skills/pr-review/SKILL.md` | The review rubric. One file, used by the CLI and by CI. |
| `scripts/review.py` | Runs the skill with the Antigravity SDK. Read-only, writes `findings.json`. |
| `scripts/render_comment.py` | Turns `findings.json` into one PR comment. No model. |
| `.github/workflows/ai-review.yml` | Gates, then the agent job, then the post job. |
| `.agents/skills/dependency-audit/SKILL.md` | Second skill: explains a `pip-audit` scan. |
| `.github/workflows/dependency-audit.yml` | Weekly scan that opens a draft PR and never merges. |

Run the gates locally:

```bash
python -m pip install -r requirements-dev.txt
ruff check . && python -m unittest discover -s tests && python scripts/secret_scan.py
```
