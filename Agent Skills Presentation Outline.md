
**SLIDE 0 — Title Slide**
- Title: "Agentic Skills: Prompts + Code + Recipes"
- Subtitle: "Group A Presentation"
- Team Name: Team JAS
- Members: Albina, Jack, Sanjog
- Date: April 8, 2026
- No speaking time allocated — on screen as people take their seats

---

**SLIDE 1 — The Problem: Vibe Coding (1 min)**
- Left side: screenshot or mock of someone pasting the same long prompt into an AI chat for the 5th time
- Right side: an agent that "just knows" how to do the task because it loaded a skill
- Talking point: "Every time you start a new chat, the AI forgets everything. You re-explain your formatting rules, your company standards, your preferences. This is vibe coding — it works once, but it doesn't scale."
- End with the thesis: "Agent Skills solve this by turning throwaway prompts into reusable, portable expertise."

---

**SLIDE 2 — What Are Agent Skills? (1.5 min)**
- Definition: Filesystem-based folders containing instructions, scripts, and resources that an agent loads dynamically
- Three key properties as visual icons or callouts: **Filesystem-based** (just folders and files, no API config), **Open standard** (works across Claude, Copilot, Cursor, Gemini CLI), **Persistent** (survives session resets, version-controlled with Git)
- Talking point: "Think of it as a recipe book for AI. The agent reads the recipe only when it needs it."

---

**SLIDE 3 — Capability vs. Expertise (1.5 min)**
- Visual analogy: A chef holding a knife (capability/tool via MCP) vs. a chef holding a recipe card (expertise/skill)
- Two-column comparison: MCP/Tools = "the plumbing" / "what the agent CAN do" (read a database, send an email, access filesystem) vs. Agent Skills = "the playbook" / "HOW the agent SHOULD do it" (deduplication rules, fiscal year boundaries, preferred chart styles)
- Talking point: "An agent might have the capability to query your sales database, but without a Data Analysis Skill, it doesn't know your company's specific column naming conventions or fiscal year boundaries."

---

**SLIDE 4 — Anatomy of a Skill: Overview (1.5 min)**
- Show the folder tree structure prominently:
  ```
  .cursor/skills/data-prep/
  ├── SKILL.md          ← Reasoning Layer (the brain)
  ├── scripts/
  │   └── clean.py      ← Execution Layer (the muscle)
  └── references/
      └── field_defs.md  ← Contextual Layer (the memory)
  ```
- Brief one-liner for each layer beneath the tree
- Talking point: "Every skill is a self-contained package with three layers. Let's look at each one."

---

**SLIDE 5 — The Reasoning Layer: SKILL.md (1 min)**
- Show a realistic snippet of YAML frontmatter (`name`, `description`) plus a few lines of the markdown body with XML tags like `<steps>` and `<guidelines>`
- Highlight that the `description` field is what triggers automatic discovery — the agent reads it to decide when to load the skill
- Talking point: "This is just structured natural language. A non-coder can write this. The description is the most important line — it's the agent's trigger."

---

**SLIDE 6 — The Execution + Contextual Layers (1 min)**
- Two-panel slide. Left panel: **scripts/** — example of a small `clean.py` snippet that deduplicates rows and normalizes date formats. Emphasize: "100% mathematical accuracy vs. LLM guessing. Also saves tokens because the agent runs existing code instead of generating it."
- Right panel: **references/** — example of `field_definitions.md` with a short glossary of standard column names. Emphasize: "Institutional memory. Loaded only when the agent needs it."
- Talking point: "The scripts give you determinism. The references give you organizational context. Together with the SKILL.md, you get a reliable mini-application."

---

**SLIDE 7 — Progressive Disclosure & Token Economics (1.5 min)**
- Diagram showing three tiers as expanding circles or a funnel:
  - **Level 1 — Discovery:** YAML frontmatter only. ~30–100 tokens per skill. Always in memory.
  - **Level 2 — Instructions:** Full SKILL.md body. ~5,000 tokens. Loaded when triggered.
  - **Level 3 — Resources:** Scripts, references, assets. Unlimited. Loaded on demand.
- Contrast with "monolithic prompting" where everything is stuffed into the system prompt at once
- Talking point: "This is why skills scale. An agent can be aware of 50 skills at the cost of only a few thousand tokens, then load the full instructions only when they're relevant."

---

**SLIDE 8 — Cross-Platform Portability (1.5 min)**
- Visual: Same skill folder icon with arrows pointing to 4–5 platform logos: Cursor, Claude Code, GitHub Copilot, Gemini CLI, VS Code
- Table or mapping:
  - Cursor → `.cursor/skills/`
  - Claude Code → `.claude/skills/`
  - GitHub Copilot → `.github/skills/`
  - Global/Personal → `~/.cursor/skills/` or `~/.claude/skills/`
- Talking point: "Write once, use everywhere. Same SKILL.md, same folder structure. The only thing that changes is the directory path. This prevents vendor lock-in."

---

**SLIDE 9 — Ecosystem & Sources (1.5 min)**
- Show where to find skills:
  - **Official:** `github.com/anthropics/skills` (102k+ stars, production-grade examples)
  - **Spec:** `agentskills.io` (the open standard documentation)
  - **Community:** Antigravity Awesome Skills (1,234+ skills), skillsmp.com (500k+ indexed), mdskills.ai
  - **Install methods:** Manual copy, `npx skills add`, Cursor Settings → Remote Rule (GitHub)
- Talking point: "You don't have to build everything from scratch. There's a massive ecosystem. Official skills from Anthropic, plus thousands from the community."

---

**SLIDE 10 — Security & Governance (1.5 min)**
- Three security concerns with icons:
  - **Prompt Injection:** A malicious CSV containing "Ignore all previous instructions" could override skill behavior
  - **Filesystem Access:** Skills can include scripts that touch the filesystem — a poisoned skill could exfiltrate data
  - **Unvetted Community Skills:** Not all skills on marketplaces are audited
- Three best practices:
  - **Sanitize inputs:** Treat all user-provided data as untrusted
  - **Human-in-the-loop (HITL):** For destructive operations (deleting files, deploying code), require user approval
  - **Review before install:** Always inspect SKILL.md and scripts before adding to your project
- Talking point: "Skills are powerful, which means they need governance. Treat them like any dependency — review before you trust."

---

**SLIDE 11 — Skills vs. Other Primitives: Deep Comparison (2 min)**

This is the taxonomy slide. Walk through each primitive individually, not just as a table row.

**Agent Skills**
- Analogy: A recipe or expert playbook
- What it does: Packages "how to" knowledge — instructions, scripts, reference docs — into a reusable folder the agent loads when semantically relevant
- Activation: Automatic. The agent reads the skill's description and decides on its own whether the current task matches. Can also be invoked manually via `/skill-name` slash command.
- Scope: Lives in the project repo or user's home directory. Version-controlled. Portable across platforms.
- Example: A "code-review" skill that tells the agent to check for hardcoded secrets, missing docstrings, and style violations every time someone says "review this code."

**Subagents**
- Analogy: A specialist worker you delegate a specific job to
- What it does: Spins up an independent agent with its own context window, tool access, and optionally its own model. Works in parallel and reports results back to the parent agent.
- Activation: Explicit delegation. The parent agent decides to spawn a subagent for a discrete subtask.
- Scope: Temporary. Exists only for the duration of the delegated task. Its context is isolated from the main conversation.
- Example: A main agent handling a data migration spawns a "SQL Safety Subagent" that independently validates every generated query before execution. Only the final pass/fail comes back to the main chat, saving thousands of tokens of intermediate reasoning.
- Key difference from skills: A subagent is a *worker* with its own workspace. A skill is *knowledge* that any worker can load. You can "skill" a subagent — give it a skill to follow while it works.

**Hooks**
- Analogy: A safety guardrail or tripwire
- What it does: Enforces constraints or triggers actions based on system events, not user prompts. Runs automatically when a specific condition is met.
- Activation: System events — e.g., before a file is saved, after code is generated, when a commit is about to happen.
- Scope: Always active. Not something the agent "chooses" to load — it fires based on predefined triggers.
- Example: A pre-commit hook that automatically scans generated code for API keys and blocks the commit if any are found. The agent doesn't decide to run this — it runs regardless.
- Key difference from skills: Skills are advisory ("here's how to do X well"). Hooks are mandatory ("this MUST happen before Y").

**MCP (Model Context Protocol)**
- Analogy: A data connector or power outlet
- What it does: Gives the agent the *capability* to interact with external systems — databases, APIs, file systems, SaaS tools. It's the plumbing.
- Activation: Tool invocation. The agent calls an MCP tool when it needs to read, write, or query something external.
- Scope: Persistent connection configured at the environment level. Available across all tasks in a session.
- Example: An MCP server connected to Salesforce lets the agent pull customer records. But the agent still needs a "Sales Reporting Skill" to know *which* fields to pull, *how* to format the report, and *what* fiscal year boundaries to use.
- Key difference from skills: MCP = what the agent *can* do. Skills = how the agent *should* do it. They are complementary, not competing.

**Summary comparison table** (keep on slide as a quick visual reference alongside the verbal walkthrough):

| Primitive | Analogy | Goal | Activation | Persistence |
|-----------|---------|------|------------|-------------|
| Agent Skill | Recipe/Expertise | How to perform a task | Semantic relevance / slash command | Permanent, version-controlled |
| Subagent | Specialist Worker | Workspace isolation | Explicit delegation | Temporary, per-task |
| Hook | Safety Guardrail | Enforcing constraints | System events | Always active |
| MCP | Data Connector | Accessing external data | Tool invocation | Session-level connection |

- Talking point: "These four primitives work together. MCP gives the agent hands. Skills give it expertise. Hooks keep it safe. Subagents let it delegate. A mature agentic system uses all four."

---

**SLIDE 12 — Key Takeaways (1 min)**
- Three takeaways, clean and bold:
  1. Agent Skills turn throwaway prompts into reusable, portable, version-controlled expertise
  2. The open standard works across Cursor, Claude Code, GitHub Copilot, Gemini CLI, and more — no vendor lock-in
  3. Anyone can author a skill — it's structured Markdown with optional scripts, not code-heavy infrastructure
- Talking point: "If you remember three things from this presentation, make it these."

---

**SLIDE 13 — Ending Slide**
- "Thank You — Now Let's See It in Action"
- Team JAS — Albina, Jack, Sanjog
- April 8, 2026

---

**Summary Table**

| Slide | Section | Time | Content Focus |
|-------|---------|------|---------------|
| 0 | Title | — | Team JAS, members, date |
| 1 | The Problem | 1 min | Vibe coding pain point + thesis |
| 2 | What Are Agent Skills | 1.5 min | Definition + 3 key properties |
| 3 | Capability vs. Expertise | 1.5 min | MCP vs. Skills analogy |
| 4 | Anatomy: Overview | 1.5 min | Folder tree structure |
| 5 | Anatomy: SKILL.md | 1 min | Frontmatter + markdown body |
| 6 | Anatomy: Scripts + References | 1 min | Execution + contextual layers |
| 7 | Progressive Disclosure | 1.5 min | Three-tier token economics |
| 8 | Cross-Platform Portability | 1.5 min | Directory paths per platform |
| 9 | Ecosystem & Sources | 1.5 min | Where to find/install skills |
| 10 | Security & Governance | 1.5 min | Risks + best practices |
| 11 | Skills vs. Other Primitives | 2 min | Deep comparison of all four |
| 12 | Key Takeaways | 1 min | Three things to remember |
| 13 | Ending | — | Thank you + transition to demo |
| **Total** | | **~15 min** | **14 slides** |

---

