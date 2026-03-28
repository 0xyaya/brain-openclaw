# brain-openclaw

Gives your [OpenClaw](https://github.com/openclaw/openclaw) agents persistent memory via [brain](https://github.com/0xyaya/brain).

```
Agent: brain_recall "what did we decide about the database?"
→ SQLite is safer than Kuzu for concurrent writes [decision]
→ migration to SQLite planned but not yet scheduled [open]
```

---

## Install

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
        "agentId": "myagent",
        "corpusRoot": "~/corpus"
      }
    }
  }
}
```

Restart the gateway. Your agent now has `brain_recall`, `brain_push`, `brain_explore`, `brain_get`, and `brain_remove` in its tool list.

---

## What your agent gets

| Tool | What it does |
|------|-------------|
| `brain_recall` | Semantic + graph search over memory |
| `brain_push` | Queue a knowledge or experience node |
| `brain_explore` | Traverse graph neighborhood of an entity |
| `brain_get` | Fetch a full node by ID |
| `brain_remove` | Delete a node — MEMORY.md self-heals |

The plugin also wires a 30-minute flush cron and an `after_compaction` hook that records each session compaction as an experience node.

---

## Requirements

- [brain](https://github.com/0xyaya/brain) installed and initialized (`brain init --agent myagent`)
- OpenClaw gateway running

---

MIT
