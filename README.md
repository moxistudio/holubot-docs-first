# HoluBot — the Bot with Boundaries

> A governance & dispatch layer for AI Agent ecosystems.  
> Route, gate, audit, and control — so your agents stay powerful without going rogue.

---

**The problem is real.** AI agents are more capable than ever — and more dangerous. 36% of skills on agent marketplaces contain security flaws. 43% of MCP servers have command injection vulnerabilities. Production databases have been deleted. Credentials have been leaked in plaintext. Agents have downloaded and executed malware from GitHub Issues. These aren't hypotheticals — they happened in 2025.

**HoluBot's thesis:** The problem with AI agents isn't intelligence — it's governance. HoluBot is a lightweight **control plane** that sits in front of any agent backend. It handles intent routing, trust gating, memory governance, and auditable execution — while staying permanently thin (a few hundred lines of Python, enforced by CI).

---

## Quick Start

1. Read the whitepaper for the governance model: [`docs/WHITEPAPER_ZH.md`](docs/WHITEPAPER_ZH.md)
2. Check the public agent contract: [`docs/AGENT_SPEC.md`](docs/AGENT_SPEC.md)
3. Copy the minimal agent template and adapt it to your workflow: [`examples/standup_agent/agent.yaml`](examples/standup_agent/agent.yaml)
4. View governance flow demo (image): [`docs/demo/governance_flow_30s.svg`](docs/demo/governance_flow_30s.svg)

![Governance flow demo](docs/demo/governance_flow_30s.svg)

---

## How It Works

```
┌─────────────────────────────────────────────────┐
│              User Touchpoints                    │
│     Telegram · Discord · Feishu · (more)         │
└───────────────────┬─────────────────────────────┘
                    │
┌───────────────────▼─────────────────────────────┐
│                                                   │
│        HoluBot · Control Plane                    │
│        (200–500 lines of Python)                  │
│                                                   │
│   • Intent classification → route or reply        │
│   • Trust gating (auto / confirm / always_confirm)│
│   • Shared long-term memory (governed, audited)   │
│   • Approval interception before risky actions    │
│   • Append-only audit log for every operation     │
│   • Health checks across all backends & channels  │
│                                                   │
└───────────────────┬─────────────────────────────┘
                    │
            AgentAdapter (pluggable)
                    │
      ┌─────────────┼──────────────┐
      ▼             ▼              ▼
  ┌────────┐  ┌─────────┐  ┌───────────┐
  │ Weekly  │  │ Content │  │   Code    │  ... any new agent
  │ Report  │  │ Writer  │  │  Helper   │      without changing
  │ Agent   │  │ Agent   │  │  Agent    │      the control plane
  └────────┘  └─────────┘  └───────────┘
```

The control plane **never gets fat**. No matter how many agents, skills, or MCP servers you add, the frontend stays at a few hundred lines. If it grows, something is wrong.

---

## Why HoluBot

| | Typical agent frameworks | HoluBot |
|---|---|---|
| **Trust model** | Full autonomy by default | Graduated trust — `auto` / `confirm` / `always_confirm` |
| **Cost** | Loads everything every message (~13k tokens for "good morning") | Lightweight frontend answers 80% of messages directly (~100 tokens) |
| **Security** | Open skill marketplace (36% have flaws) | Three-layer import audit; no open marketplace |
| **Failure mode** | Silent degradation ("AI just got dumber") | All anomalies surfaced to user — never swallowed silently |
| **Architecture** | Monolithic — one process does everything | Control plane + pluggable backends — isolated failure domains |
| **Backend lock-in** | Tied to one framework | AgentAdapter abstraction — swap backends without touching the frontend |

---

## Ecosystem Position

HoluBot is **not** another agent framework. It complements them.

- **With OpenClaw / CoPaw:** Put HoluBot in front as a governance layer — get approval gates, cost control, and audit logs while keeping full execution power.
- **With any CLI agent (Claude Code, Qwen Code, etc.):** HoluBot routes tasks to them via the AgentAdapter interface.
- **Standalone:** Use the built-in Skill engine for structured workflows that don't need a heavyweight backend.

## What HoluBot Is Not

- Not an autonomous "do-anything" agent that executes risky actions silently.
- Not an open skill marketplace with unreviewed third-party imports.
- Not a replacement for your preferred execution backend; it is the governance layer in front.

---

## Agent Specification

Every custom agent is defined by a single `agent.yaml`:

```yaml
# Minimal example — a standup assistant in 10 lines
meta:
  name: "Standup Helper"
  id: "standup"

trigger:
  keywords: ["standup", "daily sync", "what's the plan"]

steps:
  - id: "ask"
    action: "llm_call"
    prompt: |
      You are a standup assistant. Ask the user:
      1. What did you do yesterday?
      2. What's the plan for today?
      3. Any blockers?
      Summarize their answers into a concise standup note.
```

All other fields (personality, trust level, model, executor) use sensible defaults. See [`examples/`](examples/) for more.

Full spec reference: [`docs/AGENT_SPEC.md`](docs/AGENT_SPEC.md) *(coming soon)*

---

## Project Status

> **Stage: docs-first open-source preview**

This repository currently contains architecture documentation, the agent contract specification, and examples. Runnable code is being stabilized and will be released incrementally.

| What's here now | What's coming next |
|---|---|
| ✅ Sanitized whitepaper ([中文](docs/WHITEPAPER_ZH.md)) | 🔜 Core gateway code (~500 lines) |
| ✅ Agent YAML spec + examples | 🔜 Token cost benchmark (real data) |
| ✅ Architecture & design principles | 🔜 Three-layer security audit engine |
| ✅ Roadmap | 🔜 Docker one-liner setup |

**Star this repo** to follow progress. First runnable release is targeted for the coming weeks.

---

## Design Principles

1. **The frontend never gets fat.** A few hundred lines, CI-enforced. Routing and governance only.
2. **Skill-driven, not model-dependent.** Structured SOPs tell the agent *what to do step by step*, so even cheap models deliver consistent results.
3. **Trust is earned, not assumed.** New workflows require confirmation. After 10 successful runs, the *user* (not the AI) may upgrade trust level.
4. **No silent failures.** Backend down? Model degraded? Token expired? The user always knows.

---

## Background

HoluBot grew out of real frustration with running AI agents in production. The whitepaper documents specific incidents, cost analysis, and architectural decisions in detail:

📄 **[Read the Whitepaper (中文)](docs/WHITEPAPER_ZH.md)**

---

## Contributing

This project is in early stage. Feedback, ideas, and discussions are very welcome — please open an [Issue](https://github.com/moxistudio/holubot-docs-first/issues) or start a [Discussion](https://github.com/moxistudio/holubot-docs-first/discussions).

Code contributions will be accepted once the core codebase is published.

---

## License

[MIT](LICENSE)

---

<p align="center">
  <i>Lightweight is the method. Governance is the value.</i>
</p>
