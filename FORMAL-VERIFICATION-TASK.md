#  - AI Agentic Development - Formal Verification Task

## Overview

This repository documents my project-based work with Handshake AI on the Dynamo benchmark, focused on designing and structuring a challenging formal verification task for an AI coding/reasoning agent.

The proposed task requires an AI agent to determine whether a target theorem is syntactically derivable from a collection of premises using a predefined propositional-logic proof system.

The task was designed to be:

- Fully self-contained
- Deterministic and reproducible
- Executable in a terminal environment
- Independent of internet access
- Based on a finite formal search space
- Independently verifiable
- Difficult enough to evaluate advanced AI reasoning and coding capabilities

## My Contribution

My work focused on designing the task specification and defining how an AI agent should approach and be evaluated on the formal verification problem.

The proposed workflow required the agent to:

1. Parse logical premises and the target theorem.
2. Parse the predefined inference rules.
3. Construct an internal representation of propositional formulas.
4. Determine the permitted finite search space.
5. Perform systematic proof search.
6. Track dependencies between premises and derived statements.
7. Generate a complete ordered proof when the target is derivable.
8. Produce the required `output.json` result.
9. Validate the generated proof independently against the rule definitions.

The task was specifically designed to prevent shortcut strategies and require genuine systematic reasoning.

## Task Specification

The formal system is propositional logic.

The task defines:

- Premises
- A target theorem
- Named inference rules
- A finite formula search space
- A required output schema
- Independent proof verification

The formula syntax defines operator precedence as:

`NOT → AND → OR → IMPLIES`

Implication is right-associative.

The system does not permit:

- First-order variables
- Quantifiers
- Semantic reasoning
- Rules outside the supplied rule definitions

## Expected Agent Output

For a derivable theorem:

```json
{
  "derivable": true,
  "steps": [
    {
      "line": 1,
      "formula": "...",
      "rule": "...",
      "references": []
    }
  ],
  "final_conclusion": "..."
}

Every proof step must identify the exact inference rule used and reference only valid premises or previously derived statements.

Verification Design

The verifier is authoritative and does not require the agent to reproduce one specific proof.

Instead, it independently checks:

Whether the reported derivability result is correct
Whether referenced proof lines exist
Whether every inference step is legal
Whether the named rule matches its rule template
Whether derived formulas remain inside the permitted search space
Whether the final conclusion matches the target theorem

This allows multiple valid proofs to be accepted.

For non-derivable cases, derivability is defined through exhaustive forward saturation over the finite negation-closed subformula space.



Repository Structure

.
├── .github/
│   └── workflows/
│       ├── dynamo-rerun.yml
│       ├── dynamo-review.yml
│       ├── dynamo-run-trials.yml
│       └── dynamo-validate.yml
│
├── references/
│   ├── check-base-image.sh
│   ├── diversity-taxonomy.toml
│   └── dynamo-rubric.toml
│
├── task/
│   ├── environment/
│   │   └── Dockerfile
│   │
│   ├── instruction.md
│   │
│   ├── solution/
│   │   └── solve.sh
│   │
│   ├── tests/
│   │   ├── test.sh
│   │   └── test_outputs.py
│   │
│   └── task.toml
│
├── .gitignore
└── README.md



Engineering Characteristics

The proposed task emphasizes:

Formal logic
Automated theorem proving
Proof search
Rule-based reasoning
Dependency tracking
Deterministic verification
Containerized execution
Automated testing
GitHub Actions
AI agent evaluation
Project Context

This work was completed in the context of project-based AI agent development with Handshake AI / Dynamo.

The repository demonstrates experience with:

AI agent task design
Agent instruction design
Formal reasoning workflows
Git and GitHub
Docker-based environments
Automated testing
CI/CD workflows
Benchmark and verifier design
Debugging and validation
Status

This repository represents the task specification and Dynamo task structure used during development and evaluation.

The repository infrastructure separates:

Task Instructions → Agent Environment → Reference Solution → Verification Tests → Automated Dynamo Evaluation

This separation helps make the benchmark reproducible, independently verifiable, and suitable for evaluating AI coding/reasoning agents.


### One thing I would change for your recruiter impression

Don't call the README something vague like **"AI Agent Project"**.

Use a clear title such as:

> **AI Agentic Development | Formal Verification Task**

And your repository description could be:

> **Designed a deterministic formal verification benchmark for AI agents using propositional logic, proof search, rule-based inference, automated verification, Docker, and GitHub Actions.**

That is much stronger than simply saying *"Worked with Handshake AI."*

Also, the folder tree above is based on the **actual ZIP you sent me**, including the four `.github/workflows`, `references`, `task/environment`, `task/solution`, and `task/tests` sections. I can use this repository structure as our reference when you send the next files/screenshots. 
