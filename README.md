<img width="1280" height="320" src="./assets/banner.html.png" alt="Banner for the waypoint repository, an agentic engineering workflow, showing the project name with brain, puzzle, robot and lightning emojis on a blueprint-like dark gradient background">

<div align="center">

An opinionated **workflow for agentic engineering**.  
Guides you and your agents from problem discovery to production-ready code.

</div>

---

## 🚀 Getting Started

Install using the [Vercel Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add m-borgmann/waypoint --skill '*'
```

Or manually copy the skills from this repository into your agent's `skills` directory.

> [!IMPORTANT]
> When installing with the CLI, make sure to enable every agent you plan to use. *waypoint* works with all agents that support the [Agent Skills](https://agentskills.io/home) format, but the experience may differ.

## ✨ Why waypoint?

*waypoint* was made for the **agentic engineer** who wants to stay involved throughout the development cycle. It is not designed for unsupervised vibe coding — a human is expected at every action. It borrows the discipline of established software engineering practices while embracing the speed and leverage that modern language models provide.

With just a handful of user-invoked skills, the workflow is lightweight to adopt while remaining thorough where it matters. Rather than telling the model *how to think*, it tells it *what to produce*. Each skill has a well-defined output, making the workflow predictable, composable, and easy to review. Every meaningful decision stays with a human.

## 🧭 The Workflow

*waypoint* is organized around **actions**. An action is a discrete unit of work that produces an artifact.

> **Core actions** are the default progression. Each produces an artifact that later core actions consume:

1. `waypoint-align` clarifies requirements and user intent.
    - Produces `align.md`
2. `waypoint-plan` designs an implementation approach against the existing codebase.
    - Produces `plan.md`
3. `waypoint-build` executes tasks one at a time, verifying after each.
    - Produces `build.md`
4. `waypoint-review` runs a living findings loop until no open blocking issues remain.
    - Produces `review.md`

> **Optional actions** sit outside that core progression. Invoke them when you want; they are not required to progress through the four core actions:

- `waypoint-ship` generates changelog, commit message options, and PR description.
  - Produces `ship.md`

> **Utility actions** are shared helpers used by other actions:

- `waypoint-artifact` creates, validates, and keeps workflow artifacts in sync.

The `/waypoint` skill serves as an entry point. It classifies each request as **Progress** (next core action), **Revision** (update existing change and it's artifacts), or **Optional**, then routes accordingly.

> [!NOTE]
> All skills follow the [Agent Skills](https://agentskills.io/home) format. Agents that support the `disable-model-invocation: true` extension start the workflow deliberately, not opportunistically.

You may tune the skills to match your team's conventions and preferences.

## 🌟 Best Practices

Either directly invoke a specific action and pass the issue key alongside any additional information you like:

```
/waypoint-align ABC-123 but ignore the last comment by john doe
```

Or simply invoke the router and let it automatically determine the correct action:

```
/waypoint ABC-123
```

```
/waypoint ABC-123 make the primary button blue
```

> [!IMPORTANT]
> Start each action in a **new chat** with a fresh context window to achieve the best results. *waypoint* uses existing artifacts for the context it needs, so no handoff is required.

## 🛠️ Recommended Tooling

*waypoint* works best alongside tools that give agents access to real project context:

| Tool | Purpose |
| ---- | ------- |
| [Atlassian MCP](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/) | Issue and ticket retrieval |
| [Figma MCP](https://developers.figma.com/docs/figma-mcp-server/) | Design context and design-to-code |
| [GitHub MCP](https://github.com/github/github-mcp-server) | Pull requests, checks, and repository context |
| Browser | End-to-end UI self-verification |

## 📚 Artifacts

All workflow outputs make up the contract between actions and between agents. They are stored in the project workspace:

```
.waypoint/{slug}/{action}.md
```

- `{slug}` — derived from the issue key (e.g. `ABC-123`)
- `{action}` — `align`, `plan`, `build`, `review`, `ship`, or another action key
- There is one living file for each action
- Follow-ups and revisions keep affected artifacts in sync with the newest agreed state

> [!NOTE]
> Add `.waypoint/` to your project's `.gitignore` if you do not want artifacts in version control.

## 💫 Roadmap

- [ ] Coming Soon

## 💡 Acknowledgments

*waypoint* draws inspiration from practitioners and research across agentic software engineering:

- Addy Osmani, Shubham Saboo, and Sokratis Kartakis: [The New SDLC With Vibe Coding](https://www.kaggle.com/whitepaper-the-new-SDLC-with-vibe-coding)
- Thariq Shihipar, Anthropic Technical Staff: [The new rules of context engineering](https://claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models)
- Matt Pocock: [Skills For Real Engineers](https://github.com/mattpocock/skills)
- Code Rabbit: [What we got wrong about code review](https://web.archive.org/web/20260629194535/https://www.coderabbit.ai/blog/what-we-got-wrong-about-code-review)

---

<div align="center">

Made with ❤️ by [Magnus Borgmann](https://github.com/m-borgmann)

</div>
