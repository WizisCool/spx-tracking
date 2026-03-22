# SPX Express Tracking

[中文说明](./README.zh-CN.md)

Tiny SPX Express tracking utility for the command line, with an OpenClaw skill included.

It queries the public SPX Malaysia endpoint directly and returns either structured JSON, a readable tracking report, or a compact one-line summary.

## Quick Start

### CLI

Recommended for local use:

```bash
./run CNMY000XXXXXX --format summary
```

The `run` wrapper bootstraps a local virtual environment, installs dependencies if needed, and executes the tracker.

### OpenClaw Skill

Install from ClawHub:

```bash
clawhub install spx-tracking
```

ClawHub:

- https://clawhub.ai/WizisCool/spx-tracking

## Manual Usage

```bash
pip install -r requirements.txt
python skills/spx-tracking/scripts/spx_tracking.py <tracking_number> [--format json|text|summary]
```

## Examples

```bash
# Quick one-line status
./run CNMY000XXXXXX --format summary

# Full readable report
./run CNMY000XXXXXX --format text

# Structured JSON for piping or automation
./run CNMY000XXXXXX --format json
```

## Output Formats

| Format | Description |
|---|---|
| `json` | Full structured output |
| `text` | Human-readable report with timeline and route details |
| `summary` | Single-line status for quick checks |

## Arguments

| Argument | Description |
|---|---|
| `tracking_number` | SPX tracking number such as `CNMY...` or `SPXMY...` |
| `--format` | `json`, `text`, or `summary` |
| `--cookie` | Optional browser cookie for fallback authenticated requests |
| `--timeout` | Request timeout in seconds (default: `15`) |

## OpenClaw Skill Layout

This repository also includes the skill source under:

```text
skills/spx-tracking/
```

If you prefer a manual setup, you can copy that directory into your local OpenClaw skills directory.

The skill uses the same Python tracker included in this repository.

## Notes

- No API key is required.
- No login is required in normal cases.
- The `--cookie` flag is optional and only useful when the public endpoint rejects the request.

## Dependencies

| Dependency | Required | Note |
|---|---|---|
| `python3` | Yes | Must be available on PATH |
| `requests` | Yes | Installed via `requirements.txt` |

## License

MIT
