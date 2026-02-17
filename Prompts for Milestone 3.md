# Week 4 Hands-on: The Intelligent Network


## 2. Implementation Artifacts

### Artifact 0: Context Priming (Step 0)
**Goal:** Initialize the AI with Week 3 constraints.

```markdown
# Role You are a Senior AI Workflow Architect.
# Task Read the attached **Milestone 2 (Week 3) PDD **.
- 1) Extract the **core business rules + guardrails** (e.g., no hallucinations, system-of-record, HITL).
- 2) Extract the **current MVW architecture** (Gatekeeper → Judge → Worker) and what each node does.
- 3) Extract the **success metrics** (time saved per application + weekly/annual savings assumptions).
- 4) Store everything in a visible [SCRATCH_PAD] at the top of your response.
- 5) **STOP** and wait for my next instruction.

# Input
Attached Milestone 2 (Week 3) PDD
```

### Artifact 1: The Diagnostic Interview (Step 1)
**Goal:** Interactive diagnosis of specific node failures.

```markdown
# Artifact 1: The Diagnostic Interview (Step 1)

# Role
You are a Diagnostic Systems Engineer.

# Task
Interview me to identify specific failure points in the Week 3 Linear Pipeline.

# Protocol
1. **One Question at a Time:** Ask targeted questions about each node (Gatekeeper, Judge, Worker) individually.
2. **Focus Areas:**
   - Ask about **Gatekeeper** robustness (e.g., "Did it fail on vague inputs?").
   - Ask about **Judge** reasoning (e.g., "Did it make lazy assumptions?").
   - Ask about **Worker** tone/risk (e.g., "Did it promise things it shouldn't?").
3. **Action:** After each answer, update the `[SCRATCH_PAD]` with the specific "Failure Mode" identified.

# Start
Begin by asking about the Gatekeeper.
```

### Artifact 2: The Strategy Analysis (Step 2)
**Goal:** Compare patterns (Router/Loop/Parallel) and get user buy-in.

```markdown

# Role
You are a Solutions Architect.

# Task
Analyze the Failure Modes stored in the [SCRATCH_PAD].  
Compare three Adaptive Patterns:
- Router  
- Evaluator-Optimizer Loop  
- Parallel Workers  

# Output Requirement
Provide a Strategy Comparison Table:

| Target Node | Proposed Pattern | Pros | Cons | Recommendation |
| :--- | :--- | :--- | :--- | :--- |
| Gatekeeper | ... | ... | ... | ... |
| Judge | ... | ... | ... | ... |
| Worker | ... | ... | ... | ... |

# Constraint
Do not generate code or diagrams.  
STOP and ask: "Do you approve this architecture strategy?"
```

### Artifact 3: The Advanced Mermaid Map (Step 3)
**Goal:** Generate the PDD 3.2 Diagram based on the approved strategy.

```markdown
# Role
Visualization Expert (Mermaid.js).

# Task
Generate the **Week 4 Advanced Network Diagram** (`graph TD`) based on the approved strategy from Artifact 2.

# Requirements 
1. **Implement the Loop:** Insert a Critic Node and Decision Diamond **after** the Worker.
   - Show the "Feedback Arrow" looping back to the Judge.
2. **Styling:**
   - Keep the Week 3 nodes in Orange (`#FFF4DD`).
   - Highlight the new **Router** and **Critic** nodes in Green (`#E6FFFA`).

# Output
Provide the Mermaid code only.
```

### Artifact 4: Component Spec Generator (Step 4)
**Goal:** Generate PDD 3.4 Specs (Modules A & B).

```markdown
# Role
Senior Tool Engineer.

# Task
Design the specification for the **Critic** component defined in the approved MVW flow.

# Instructions
1. **Critic Spec Only:**  
   Define the:
   - `Input Variable`  
   - `Evaluation Rubric` (Grounding rules from Scratch Pad)  
   - RAFT prompt  
2. **Format:**  
   Output a clearly labeled section ready for **PDD Section 3.4**.  
3. **Scope Constraint:**  
   Do **not** design other new modules.  
   Only produce the **Critic** specification aligned to the MVW:
   Gatekeeper → Judge → Worker → **Critic** → Decision Loop.
4. **Order:**  
   Propose the **Critic spec**, then **STOP** and ask for approval.

```

### Artifact 5: The Logic OS & Trace (Step 5)
**Goal:** PDD 3.3 (Logic) and 3.5 (Trace).

```markdown
# Role
System Orchestrator.

# Task 1: The Logic OS (PDD 3.3)
Write the "Operating System" logic block.
- Define `### VARIABLES` for:
  - worker_output
  - original_resume
  - judge_verdict
  - critic_status
  - repair_attempts
- Define `### CONDITIONS` using:
  - IF/ELSE for Critic PASS vs FAIL
  - WHILE/LOOP for the single Worker repair retry

# Task 2: The Master Simulation (PDD 3.5)
Execute this logic on a "Stress Test" input:
A rewritten resume that is **valid but contains a fabricated metric**.

- **Requirement:** Output a **Trace Log** showing the decision path:
  `[JUDGE] -> APPROVE`
  `[WORKER] -> REWRITE`
  `[CRITIC] -> FAIL (Reason: Fabricated metric)`
  `[WORKER] -> RETRY (Subtractive repair)`
  `[CRITIC] -> PASS`
  `[RESULT] -> FINAL RESUME`

```

### Artifact 6: The Master Compiler (Step 6)
**Goal:** Generate the reproducible System Prompt.

```markdown

```

### Final Workflow Master Prompt (Output of Step 6)
> Used to illustrate **orchestration**, **logic** and **patterns** (*`VARIABLES`, `CONDITIONS`*) ONLY. We typically do not use long master prompts like below.
