# SPX Express Tracking

Query SPX Express (spx.com.my) shipment tracking from the command line.

## Quick Start

```bash
# Auto-creates venv, installs deps, runs the script
./run CNMY000XXXXXX --format summary
```

Or manually:

```bash
pip install -r requirements.txt
python skills/spx-tracking/scripts/spx_tracking.py <tracking_number> [--format json|text|summary]
```

## Arguments

| Argument | Description |
|---|---|
| `tracking_number` | SPX tracking number (CNMY..., SPXMY...) |
| `--format json` | Full structured JSON (default) |
| `--format text` | Human-readable report with timeline and geo route |
| `--format summary` | One-line status for quick replies |
| `--cookie` | Browser cookie for authenticated requests (optional, sensitive) |
| `--timeout` | Request timeout in seconds (default: 15) |

## Examples

```bash
# One-line status
./run CNMY000XXXXXX --format summary

# Full human-readable report
./run CNMY000XXXXXX --format text

# Structured JSON (piped to other tools)
./run CNMY000XXXXXX --format json
```

## Credential-Free

No login, no cookie, no API key required. The script queries SPX's public endpoint directly. The `--cookie` flag is optional and only needed if the public endpoint returns errors.

## OpenClaw Skill

This repo ships an OpenClaw skill. Install via ClawHub:

```bash
clawhub install spx-tracking
```

Or manually — place the repo at `~/.openclaw/workspace/skills/spx-tracking/`:

```bash
git clone https://github.com/WizisCool/spx-tracking.git ~/.openclaw/workspace/skills/spx-tracking/
```

Start a new OpenClaw session to load the skill.

### Verify

```bash
openclaw skills list
openclaw skills check
```

## Dependencies

| Dependency | Required | Note |
|---|---|---|
| `python3` | Yes | On PATH as `python3` |
| `requests` | Yes | `pip install -r requirements.txt` (auto-handled by `run` script) |

## License

MIT
