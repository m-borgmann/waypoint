<img width="1280" height="320" src="./assets/banner.html.png" alt="Banner for the waypoint repository, an agentic engineering methodology, showing the project name with brain, puzzle, robot and lightning emojis on a blueprint-like dark gradient background">

<div align="center">

An opinionated **methodology** for **agentic engineering**, intentionally tailored to be used with **Cursor**.

</div>

---

## 🚀 Getting Started

Install with Vercel’s [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add m-borgmann/waypoint --skill '*'
```

Or copy the skills from this repository into your agent’s `skills` directory.

## ✨ Why waypoint?

*waypoint* was made for the **agentic engineer** who wants to stay involved throughout the development cycle. It is not designed for unsupervised vibe coding. It borrows the discipline of established software engineering practices while embracing the speed and leverage that modern language models provide. Rather than telling the model *how to think*, it tells it *what to produce*.

## 🤖 Why Cursor?

This methodology was built around a particular philosophy:

> **AI should amplify the software engineer, not abstract the software engineer away from the code**

With Cursor, the agent operates in the same environment where an engineer already reads, writes and reviews code. An engineer can move fluidly between asking the agent to investigate something and inspecting the implementation themselves. The agent is doing the mechanical work, while the engineer remains responsible for understanding, directing, and reviewing it.

## 🌟 The methodology

1. **Spec**
   - Use the prompt provided below in a **new** chat
   - The agent clarifies requirements and writes `.waypoint/{slug}/spec.md`
   - You answer questions, review the spec, and approve it
2. **Plan**
   - Use the prompt provided below in a **new** chat
   - You review and approve the plan
3. **Build**
   - Use the prompt provided below in the **same** chat as the plan
   - The agent implements the requested changes
4. **Review**
   - Use the prompt provided below in a **new** chat
   - Another agent reviews the code. You decide which findings to fix
5. **Dispatch**
   - Use the prompt provided below in a **new** chat
   - The agent runs the relevant checks and offers three commit messages
   - You pick one of the commit messages after which the agent will push the changes

> [!TIP]
> You may tune the skills and prompts to match your team’s conventions and preferences.

### 💬 Prompts

Spec:

```text
/waypoint {slug}
```

Plan:

```text
Switch to plan mode and create an implementation plan for @.waypoint/{slug}/spec.md
```

Review:

```text
Critically review the changes in this branch. What can be improved, cleaned up or simplified?
```

```text
/code-review
```

> [!NOTE]
> Install the [CodeRabbit Cursor plugin](https://cursor.com/marketplace/coderabbit) and the [CodeRabbit CLI](https://docs.coderabbit.ai/cli/cursor-integration) for this to work.

```text
CodeRabbit reviewed this branch and produced the following findings: {findings}. Verify each finding against current code. Tell me what you think about them.
```

Dispatch:

```text
/dispatch
```

## 🛠️ Recommended tooling

| Tool | Purpose |
| ---- | ------- |
| [Cursor Plan](https://cursor.com/docs/agent/plan-mode) and Build | Planning and implementation |
| [Cursor Browser](https://cursor.com/docs/agent/tools/browser) | End-to-end UI verification |
| [CodeRabbit](https://cursor.com/marketplace/coderabbit) | External code review |
| [Atlassian MCP](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/) | Issue and ticket retrieval |
| [GitHub MCP](https://github.com/github/github-mcp-server) | Pull requests, checks, and repository context |

## 📚 Spec

Output of the waypoint skill and stored in the project workspace:

```text
.waypoint/{slug}/spec.md
```

The `{slug}` is derived from an issue key (e.g. `ABC-123`) and ticket information may be retrieved from an external source, such as Jira, using the appropriate MCP.

## 💫 Acknowledgments

*waypoint* draws inspiration from practitioners and research across agentic software engineering:

- Addy Osmani, Shubham Saboo, and Sokratis Kartakis: [The New SDLC With Vibe Coding](https://www.kaggle.com/whitepaper-the-new-SDLC-with-vibe-coding)
- Thariq Shihipar, Anthropic Technical Staff: [The new rules of context engineering](https://claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models)
- Harjot Gill, CEO of CodeRabbit: [Code is no longer the bottleneck. Understanding is.](https://www.coderabbit.ai/blog/code-is-no-longer-the-bottleneck-understanding-is)
- Matt Pocock: [Skills For Real Engineers](https://github.com/mattpocock/skills)

---

<div align="center">

Made with ❤️ by [Magnus Borgmann](https://github.com/m-borgmann)

</div>
