# OPTION 1

**The `xlsx` (spreadsheet) skill** from Anthropic's official set is your best bet. Here's why it checks every box:

- **Relatable to non-coders** — everyone understands "clean up this messy data and give me a spreadsheet." It ties directly to the "Analytics for Non-Coders" theme in your research.
- **All three layers are visible** — it has a SKILL.md, scripts, and reference/template assets, so you can literally show the anatomy from Slide 4 in a real folder.
- **Tangible output** — you get an actual `.xlsx` file you can open on screen. Very satisfying for an audience.
- **Fast execution** — runs in seconds, no API keys or external services needed.

If you want a second skill to show briefly for contrast, the `docx` skill works well as a quick "and it also works for Word docs" moment.

---

## Suggested 10-Minute Demo Outline

**DEMO PART 1 — Setup & Anatomy Walkthrough (2 min)**

- Open Cursor with a project that already has the skill installed in `.cursor/skills/`
- Expand the folder tree in the sidebar — call back to Slide 4: "Here's that anatomy diagram, but for real"
- Open `SKILL.md` briefly — point out the YAML frontmatter (the discovery trigger) and a couple of key instructions
- Open one script file — "This is the muscle layer, deterministic code the agent will run instead of guessing"
- Don't linger — the goal is just to ground the audience in the real file structure

**DEMO PART 2 — The "Before" Baseline (1.5 min)**

- Show a messy CSV file (prepare this in advance): inconsistent date formats, duplicate rows, bad column headers, missing values
- Optionally, do a quick "vibe coding" attempt first — paste a raw prompt into Cursor chat *without* the skill active, show that the agent either asks too many clarifying questions or makes wrong assumptions about column names
- This callback to Slide 1 (the vibe coding problem) makes the skill demo land harder

**DEMO PART 3 — Trigger the Skill (3 min)**

- With the skill active, type a natural prompt like: *"Clean up this sales data CSV and give me a formatted spreadsheet with a summary sheet"*
- Let the audience watch the agent work in real time — narrate what's happening: "It's reading the SKILL.md now... it found the cleaning script... it's loading the field definitions from references..."
- Point out the progressive disclosure in action: "Notice it didn't load everything at startup — it pulled the references only when it needed them" (callback to Slide 7)

**DEMO PART 4 — Show the Output (1.5 min)**

- Open the generated `.xlsx` file on screen
- Walk through: clean headers, normalized dates, deduped rows, formatted summary sheet
- Compare side-by-side with the original messy CSV if time allows
- Emphasize: "A non-coder typed one sentence and got a production-quality spreadsheet"

**DEMO PART 5 — Portability Moment (1 min)**

- This is optional but powerful if you can pull it off: copy the same skill folder into `.github/skills/` or mention "this same folder works in Claude Code and Copilot with zero changes"
- Callback to Slide 8 — "Write once, use everywhere"

**DEMO PART 6 — Wrap-Up & Q&A Transition (1 min)**

- Recap what the audience just saw: "One folder, three layers, one natural language prompt, production-quality output"
- Transition to Q&A: "That's Agent Skills in action — what questions do you have?"

---

## Practical Prep Checklist

Here's what you'd want ready before the demo day:

1. **Messy CSV file** — create one with 50–100 rows, mixed date formats, duplicates, bad headers. Make it obviously messy so the audience can see the transformation.
2. **Cursor on the nightly channel** with skills enabled in settings.
3. **Skill pre-installed** in `.cursor/skills/` — test it end-to-end at least twice before presenting.
4. **Backup recording** — screen-record a successful run the night before in case of live demo gremlins.
