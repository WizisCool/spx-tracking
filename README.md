# SPX Express Tracking

Query SPX Express (spx.com.my) shipment tracking from the command line.

## Install

```bash
pip install -r requirements.txt
```

## Usage

```bash
python scripts/spx_tracking.py <tracking_number> [--format json|text|summary]
```

| Flag | Description |
|---|---|
| `--format json` | Full structured JSON (default) |
| `--format text` | Human-readable report with timeline and geo route |
| `--format summary` | One-line status for quick replies |

## Examples

```bash
# One-line status
python scripts/spx_tracking.py CNMY000XXXXXX --format summary

# Full human-readable report
python scripts/spx_tracking.py CNMY000XXXXXX --format text

# Structured JSON (piped to other tools)
python scripts/spx_tracking.py CNMY000XXXXXX --format json
```

## Credential-Free

No login, no cookie, no API key required. The script queries SPX's public endpoint directly.

## OpenClaw Skill

This repo ships an OpenClaw skill at `skills/spx-tracking/SKILL.md`. Place the repo (or just the `skills/` directory) inside OpenClaw's workspace skills path.

### Install the Skill

```bash
# Option 1: Copy the whole repo
# Place repo at ~/.openclaw/workspace/skills/spx-tracking/  (or any configured workspace skills dir)

# Option 2: Copy only the skills directory into your workspace
cp -r skills/ ~/.openclaw/workspace/skills/
```

OpenClaw picks up workspace skills automatically. Start a new session to load the skill.

### Verify

```bash
openclaw skills list
openclaw skills check
```

### Dependencies

| Dependency | Required | Note |
|---|---|---|
| `python` | Yes | On PATH as `python` |
| `requests` | Yes | `pip install -r requirements.txt` |
