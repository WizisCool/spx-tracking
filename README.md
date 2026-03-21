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

## Skill (for AI Agents)

This repo ships an OpenClaw skill at `SKILL.md` — it describes the script interface and trigger phrases so AI agents can invoke tracking correctly.

### Install the OpenClaw CLI

```bash
# Requires Node.js 22+
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

### Install the Skill

Copy the repo, then place `SKILL.md` inside a `./skills/` directory:

```bash
mkdir -p skills
cp SKILL.md skills/
```

OpenClaw picks up workspace skills from `./skills/` automatically on next session.

### Verify

```bash
openclaw skills info spx-tracking
openclaw skills check
```
