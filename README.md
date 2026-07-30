<img width="1280" height="320" src="./assets/banner.html.png" alt="waypoint repository banner">

<div align="center">

An opinionated **workflow for agentic engineering**.  
Guides you and your agents from problem discovery to production-ready code.

</div>

---

## 🚀 Getting Started

> **Note:** *waypoint* was tested most extensively with [Cursor](https://cursor.com). It also works with other agents that support the [Agent Skills](https://agentskills.io/home) format, but the experience may differ.

Install using the [Vercel Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add m-borgmann/waypoint
```

When installing for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), explicitly enable it in the CLI.

Or install the skills from this repository into your agent's skills directory.

## ✨ Why waypoint?

*waypoint* was built for the **agentic engineer** who wants to stay involved throughout the development cycle. It is not designed for unsupervised vibe coding, as it assumes a human is present at every action. This makes it intentionally closer to traditional software engineering. It borrows the discipline of established practices while embracing the speed and leverage that modern language models provide.

With just a handful of user-invoked skills, the workflow is lightweight to adopt while remaining thorough where it matters. Rather than telling the model *how to think*, *waypoint* tells it *what to produce*. Each skill has a well-defined output, making the workflow predictable, composable, and easy to review. Every meaningful decision stays with a human.

## 🧭 Workflow

*waypoint* is organized around **actions**. An action is a discrete unit of work that produces an artifact.

**Core actions** are the default progression. Each produces an artifact that later core actions consume:

1. `waypoint-align`: clarifies requirements and user intent. Produces an *Alignment Brief*.
2. `waypoint-plan`: designs an implementation approach against the existing codebase. Produces an *Implementation Plan*.
3. `waypoint-build`: executes tasks one at a time, verifying after each. Produces a *Build Log*.
4. `waypoint-review`: runs a living findings loop (full then incremental) until no open blocking issues remain. Produces *Review Findings*.

**Optional actions** sit outside that core progression. Invoke them when you want; they are not required to progress through the four core actions:

- `waypoint-ship`: generates changelog, commit message options, and PR description. Produces a *Release Package*.

**Utility actions** are shared helpers used by other actions:

- `waypoint-artifact`: creates, validates, and keeps workflow artifacts in sync.

The `waypoint` skill serves as an entry point. It classifies each request as **Progress** (advance to the next incomplete core action), **Revision** (change work that already has artifacts, including from a new chat), or **Optional** (explicitly requested optional action), then routes to the appropriate action.

All skills follow the [Agent Skills](https://agentskills.io/home) format. Certain action skills use `disable-model-invocation: true` which will only work in agents that support that extension (for example Cursor and Claude Code).

## 🌟 Best Practices

*waypoint* runs only when you explicitly ask for it. Ordinary requests without that context use the normal agent flow.

Start each action in a **new chat** with a fresh context window. Pass the issue or ticket identifier alongside any additional information you like.

```
/waypoint-align ABC-123 but ignore the last comment by john doe
```

Or invoke the router and let it determine the correct action automatically:

```
/waypoint ABC-123
/waypoint ABC-123 make the primary button blue
```

Actions and the router are **user-invocable only**, so the workflow starts deliberately, not opportunistically.

### Recommended Tooling

*waypoint* works best alongside tools that give agents access to real project context:

| Tool | Purpose |
| ---- | ------- |
| [Atlassian MCP](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/) | Issue and ticket retrieval |
| [Figma MCP](https://developers.figma.com/docs/figma-mcp-server/) | Design context and design-to-code |
| Browser | End-to-end UI self-verification (built into Cursor; otherwise use a Browser MCP) |
| [GitHub MCP](https://github.com/github/github-mcp-server) | Pull requests, checks, and repository context |

Optionally tune the skills to match your team's conventions such as branch naming, CI commands and review standards before fully adopting *waypoint* on a project.

## 📚 Artifacts

All workflow outputs are stored in the project workspace:

```
.waypoint/{slug}/{action}.md
```

- `{slug}` — derived from the issue key (e.g. `ABC-123`)
- `{action}` — `align`, `plan`, `build`, `review`, `ship`, or another action key
- One living file per action; if it already exists, it is updated in place
- Follow-ups and revisions keep every affected artifact in sync with the newest agreed state

Artifacts are the contract between actions and between agents.

Add `.waypoint/` to your project's `.gitignore` if you do not want artifacts in version control.

## 💫 Roadmap

- [ ] Coming Soon

## 💡 Acknowledgments

*waypoint* draws inspiration from practitioners and research across agentic software engineering:

- Addy Osmani, Shubham Saboo, and Sokratis Kartakis: [The New SDLC With Vibe Coding](https://www.kaggle.com/whitepaper-the-new-SDLC-with-vibe-coding)
- Matt Pocock: [Skills For Real Engineers](https://github.com/mattpocock/skills)
- Thariq Shihipar, Anthropic Technical Staff: [The new rules of context engineering](https://claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models)
- Code Rabbit: [Review Documentation](https://docs.coderabbit.ai/guides/code-review-overview)
