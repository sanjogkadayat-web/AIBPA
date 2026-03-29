Good call — let me look into what's available as pre-built skills you can grab, and then I'll restructure the plan around Cursor.Now I have a clear picture of the ecosystem. Here's your updated plan, fully Cursor-focused with demo kept separate from your project.

---

**Updated Presentation Outline (15 min) — no changes needed**

The presentation content stays the same as I outlined before. Just swap any Claude-specific references to also mention Cursor. When you show the folder structure slide, use `.cursor/skills/` instead of `.github/skills/`.

---

**Demo Plan — Cursor IDE, Standalone**

**Setup: Create a fresh demo project** — this stays entirely separate from your class project. Just make a new folder like `skills-demo/` with a couple of dummy files in it (a messy Python script, maybe a small Express app). This is your sandbox.

**Demo Flow — Three Acts**

**Act 1: Install a pre-built skill from Anthropic's official repo (2–3 min)**

The best "wow" skill to download and demo is the **frontend-design** skill from `github.com/anthropics/skills`. It's visually impressive and the classroom can immediately see the difference between asking Cursor to "build a landing page" *without* the skill versus *with* it. The before/after contrast is dramatic — without the skill you get generic Inter font, purple gradients, boring layout. With it, you get distinctive, opinionated design.

How to get it: clone or download from `github.com/anthropics/skills/tree/main/skills`. Copy the `frontend-design` folder into your demo project at `.cursor/skills/frontend-design/`. In Cursor, you can also import skills directly from GitHub via Settings → Rules → Add Rule → Remote Rule (GitHub) and paste the repo URL.

Demo it by typing into Cursor Agent: *"Build me a landing page for a coffee subscription service."* Let the class watch the agent load the skill and produce something genuinely good-looking.

**Act 2: Show the anatomy — open the SKILL.md live (2 min)**

After the "wow moment," open the `frontend-design/SKILL.md` in the editor. Walk through the YAML frontmatter (name, description) and the body (design thinking process, aesthetics guidelines). Point out how the description field is what triggers automatic discovery — the agent reads it to decide when to use the skill.

**Act 3: Build a custom `/review` skill from scratch (3–5 min)**

This ties directly to your assigned topic. Create it live in front of the class:

1. Create `.cursor/skills/review/SKILL.md`
2. Write ~15 lines of frontmatter + instructions (review code for hardcoded secrets, missing error handling, style issues)
3. Optionally add a `references/style_guide.md` with 4–5 rules
4. Open your deliberately messy Python file, type into Cursor Agent: *"Review this code"*
5. Watch Cursor auto-discover the skill and produce a structured review

This shows the full lifecycle: create → discover → execute.

---

**Skills Worth Downloading for the Demo**

Here are the best picks, organized by where to get them:

**From Anthropic's Official Repo** (`github.com/anthropics/skills`): this is the gold standard, 102k stars. These skills are production-grade and well-structured, making them ideal references for a classroom.
- **frontend-design** — best for visual impact, the before/after is unmissable
- **docx** — shows the "execution layer" with bundled Python scripts for Word doc generation
- **pdf** — complex skill with scripts/, references/, and forms handling — great to show the full three-layer anatomy
- **internal-comms** — good non-coder example; shows how skills can standardize business writing with example templates in an `examples/` directory
- **brand-guidelines** — simple and elegant; shows how a skill can enforce visual identity

**From the Community** (for showing breadth/portability):
- **chrisboden/cursor-skills** on GitHub — a Cursor-specific starter template that includes a skill-creator skill and an MCP-based orchestrator. Good for showing the Cursor ecosystem specifically.
- **skillmatic-ai/awesome-agent-skills** on GitHub — a curated list with links to skills from Anthropic, OpenAI, Microsoft, Google, Vercel, Supabase, and Hugging Face. Good to flash on screen to show the ecosystem is huge.

**From Marketplaces** (to mention, not necessarily install):
- **skillsmp.com** — aggregates 500,000+ skills from GitHub with quality filtering
- **mdskills.ai** — a directory with one-click downloads and install guides per agent

---

**What a Great Demo Looks Like**

The best demo tells a story in three beats: *"Here's the problem"* (vibe coding gives inconsistent results), *"Here's the solution"* (install a skill), *"Here's how easy it is to make your own"* (build `/review` live). Specifically:

- Show the `/` slash command menu in Cursor after installing skills — the audience sees their names appear, proving discovery works
- Use the Cursor Agent chat (Cmd+I), not just tab completion — this shows the agentic behavior where the agent *decides* to load the skill based on your natural language prompt
- Cursor supports automatic skill discovery — agents apply skills when domain-specific knowledge and workflows are relevant, and you can also invoke a skill explicitly via the slash command menu
- Keep your demo files deliberately bad — the worse the input, the more impressive the skill's output

---

**Scratchpad updated:**

- **Platform:** Cursor IDE (stable channel supports skills natively now)
- **Demo project:** Standalone `skills-demo/` folder, separate from class project
- **Skills to download:** frontend-design + internal-comms + brand-guidelines from `anthropics/skills`; chrisboden/cursor-skills for Cursor-specific scaffolding
- **Custom skill to build live:** `/review` (code review)
- **Demo materials needed:** Messy Python file, the downloaded skills, Cursor with agent mode
- **Key sources:** `github.com/anthropics/skills`, `agentskills.io` (spec), `cursor.com/docs/skills`

Want me to draft the actual SKILL.md for the `/review` skill, or create the deliberately messy Python file for you?
