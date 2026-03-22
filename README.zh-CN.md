# SPX Express 物流追踪

[English README](./README.md)

一个小巧、直接可用的 SPX Express 命令行追踪工具，并附带 OpenClaw skill。

它直接查询 SPX Malaysia 的公开接口，支持输出结构化 JSON、可读性更好的文本报告，或者适合快速查看的一行摘要。

## 快速开始

### CLI

本地使用推荐直接运行：

```bash
./run CNMY000XXXXXX --format summary
```

`run` 会自动创建本地虚拟环境、安装依赖，并执行追踪脚本。

### OpenClaw Skill

通过 ClawHub 安装：

```bash
clawhub install spx-tracking
```

ClawHub 页面：

- https://clawhub.ai/WizisCool/spx-tracking

## 手动使用

```bash
pip install -r requirements.txt
python skills/spx-tracking/scripts/spx_tracking.py <tracking_number> [--format json|text|summary]
```

## 示例

```bash
# 一行查看当前状态
./run CNMY000XXXXXX --format summary

# 查看完整可读报告
./run CNMY000XXXXXX --format text

# 输出结构化 JSON，便于脚本处理或二次集成
./run CNMY000XXXXXX --format json
```

## 输出格式

| 格式 | 说明 |
|---|---|
| `json` | 完整结构化输出 |
| `text` | 更适合阅读的物流报告，包含时间线与路线信息 |
| `summary` | 单行摘要，适合快速查看 |

## 参数

| 参数 | 说明 |
|---|---|
| `tracking_number` | SPX 单号，例如 `CNMY...` 或 `SPXMY...` |
| `--format` | `json`、`text` 或 `summary` |
| `--cookie` | 可选的浏览器 Cookie，用于公开接口失败时兜底 |
| `--timeout` | 请求超时时间，默认 `15` 秒 |

## OpenClaw Skill 目录

这个仓库也附带了 skill 源码，位于：

```text
skills/spx-tracking/
```

如果你更习惯手动方式，也可以把这个目录复制到本地 OpenClaw skills 目录中。

skill 调用的就是本仓库内置的同一个 Python 追踪脚本。

## 说明

- 不需要 API key。
- 正常情况下不需要登录。
- `--cookie` 是可选项，只有公开接口拒绝请求时才可能需要。

## 依赖

| 依赖 | 必需 | 说明 |
|---|---|---|
| `python3` | 是 | 需要在 PATH 中可用 |
| `requests` | 是 | 通过 `requirements.txt` 安装 |

## 许可

MIT
