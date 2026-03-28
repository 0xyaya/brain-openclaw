# brain-openclaw

OpenClaw plugin adapter for [brain](https://github.com/0xyaya/brain) — wires persistent agent memory into [OpenClaw](https://github.com/openclaw/openclaw).

## What this does

Registers the following into OpenClaw:

- **Native tools**: `brain_recall`, `brain_push`, `brain_explore`, `brain_get`, `brain_remove`
- **Flush cron**: processes `queue.jsonl` → graph every 30 minutes
- **Consolidation hooks**: `after_compaction` pushes a lightweight experience node

## Installation

```bash
git clone https://github.com/0xyaya/brain-openclaw ~/.openclaw/extensions/brain
cd ~/.openclaw/extensions/brain && npm install
```

Add to `openclaw.json`:
```json
{
  "plugins": {
    "brain": {
      "config": {
        "agentId": "your-agent-id",
        "corpusRoot": "~/corpus"
      }
    }
  }
}
```

Restart the OpenClaw gateway.

## Requirements

- [brain](https://github.com/0xyaya/brain) CLI installed and initialized
- OpenClaw gateway running

## License

MIT
