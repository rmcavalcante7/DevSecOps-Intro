# AI Repository Operating System

Canonical guide for this repository.

This `README.md` consolidates the guidance that was previously split across:

- `AI_Repository_Guide_v2.md`
- `AI_Repository_Guide_v3.md`
- `AI_Repository_Guide_v3_improved.md`

Those files can be kept as historical drafts, but this README is the canonical human-facing guide from this point forward.

---

## What This Repository Is

This is not just a folder structure.

It is a controlled environment for AI-assisted engineering, designed to make an AI behave like a senior engineer working inside a structured system.

The repository is built around five core ideas:

- context replaces guesswork
- decisions prevent architectural drift
- runbooks standardize execution
- checklists enforce validation
- feedback drives continuous improvement
- wikilinks expose relationships as an Obsidian knowledge graph

It is especially useful for:

- automation and RPA projects
- internal integration systems
- data-processing services
- reusable Python packages and internal SDKs

---

## Core Structure

### `.aiassistant/project_context/`

Purpose:

- holds the current understanding of the system
- contains the only active runtime context file

Main file:

- `CURRENT_CONTEXT.md`

Rule:

- this is the single source of truth for current system behavior

### `.aiassistant/decisions/`

Purpose:

- stores accepted architectural rules and constraints

Use it for:

- integration boundaries
- security rules
- dependency strategy
- long-lived trade-offs

### `.aiassistant/runbooks/`

Purpose:

- stores executable, repeatable procedures

Use it for:

- generating project documentation
- preparing packaging metadata
- publishing a Python package
- bootstrapping project context

### `.aiassistant/checklists/`

Purpose:

- validates that an output is safe and correct before completion

Use it for:

- release readiness
- environment validation
- delivery checks
- critical input validation

### `.aiassistant/rules/`

Purpose:

- defines how the repository and the AI should behave

Main files:

- `AGENTS.md`
- `CONTEXT_RULES.md`
- `CONTEXT_TEMPLATE.md`
- `REPOSITORY_GUIDELINES.md`
- `WIKILINK_RULES.md`

### `.aiassistant/tools/`

Purpose:

- stores repository-local support scripts
- validates or exports derived data from `.aiassistant` artifacts

Rule:

- tools are helpers, not a source of truth

---

## Advanced Structure

### `.aiassistant/feedback/`

Captures real-world problems, pain points, bugs, and improvement opportunities.

### `.aiassistant/roadmap/`

Defines release-oriented planning, phases, and scope.

### `.aiassistant/specs/`

Defines how a complex or impactful change should be implemented before coding.

### `.aiassistant/prompts/`

Stores reusable, project-specific prompts for recurring tasks.

### `.aiassistant/templates/`

Provides reusable starter files for new artifacts.

Important:

- templates accelerate creation
- templates are not a source of truth
- every generated file must be adapted to the real project
- example files in this directory are illustrative only

### Knowledge Graph

The repository supports Obsidian-compatible wikilinks between `.aiassistant` Markdown artifacts.

Use this feature to connect context, decisions, runbooks, checklists, feedback, roadmap, specs, prompts, and rules.

Important:

- links should represent real operational or architectural relationships
- the graph must not create a second source of truth
- open `.aiassistant` directly as the Obsidian vault for first-phase visualization
- use the wikilink validator before accepting new graph relationships

---

## How The System Flows

Typical evolution flow:

1. `feedback/` identifies a problem or opportunity
2. `roadmap/` plans what should be built
3. `specs/` defines how a change should work
4. `decisions/` records binding architectural rules when needed
5. `runbooks/` execute repeatable procedures
6. `checklists/` validate correctness and safety
7. `project_context/CURRENT_CONTEXT.md` is updated to reflect reality
8. wikilinks connect meaningful relationships for graph navigation

Not every project uses every layer every day, but the layers exist to keep the system consistent as it grows.

---

## Two Main Project Profiles

### 1. Operational Projects

Use this profile for:

- automations
- RPAs
- internal workers
- integration pipelines
- background jobs

Typical focus:

- operational flow
- entrypoints
- folders such as input, output, temp, logs, and errors
- credentials and execution environment

### 2. Product Projects

Use this profile for:

- Python libraries
- installable packages
- internal SDKs
- public repositories

Typical focus:

- installability
- public API
- packaging metadata
- release validation
- distribution and versioning

Important rule:

- packaging and publish runbooks are for product projects
- pure automations do not automatically need packaging or release runbooks

---

## Quick Start For A New Project

### If the project has no `CURRENT_CONTEXT.md`

Do not invent context.

Use `.aiassistant/runbooks/bootstrap-project-context.md` to gather the minimum real information required to create the first version of `CURRENT_CONTEXT.md`.

The initial goal is not to document everything.

The goal is to establish enough trustworthy context to stop the AI from guessing.

### After context exists

Use the repository incrementally:

- update context when the system changes
- create decisions when constraints become binding
- add runbooks when execution must be repeatable
- add checklists when failure is costly
- capture feedback when real pain points appear

---

## What Should Be General At Project Start

Some things are useful in almost every new project, even before the project becomes sophisticated:

- an initial `CURRENT_CONTEXT.md`
- a bootstrap checklist
- a decision template
- a spec template
- a roadmap template
- a prompt template for recurring tasks

That is why this repository now includes `.aiassistant/templates/` with starter artifacts that can be adapted per project.

There is also a filled example for a fictional automation project at:

- `.aiassistant/templates/current-context-example-automation.md`

Important:

- it is only a reference
- it is not active context
- it must not replace a real `CURRENT_CONTEXT.md`

---

## Recommended First Artifacts

For a fresh automation project:

- `CURRENT_CONTEXT.md`
- an operational `README.md`
- a bootstrap checklist
- one or more runbooks for execution-critical flows

For a fresh library or SDK:

- `CURRENT_CONTEXT.md`
- a product `README.md`
- `pyproject.toml`
- a release checklist
- publish runbook alignment

---

## Common Mistakes

- skipping context creation
- treating historical notes as active context
- changing behavior without recording a decision
- using runbooks as explanation instead of execution
- finishing work without a validation checklist
- mixing automation and package workflows without deciding the project type first

---

## Practical Rules For Humans And Agents

- read current context before coding when it exists
- do not override accepted decisions silently
- do not create parallel sources of truth
- do not invent missing architecture
- update context after meaningful system changes
- prefer explicit process over improvisation

---

## Current State Of This Repository

This repository is still a starter operating system, not a populated project instance.

That means:

- many directories currently contain guidance and templates rather than project-specific artifacts
- the value today is the process scaffolding
- real project context is expected to be created when this template is instantiated for an actual system

---

## Canonical References

If you are operating this repository, the main reference points are:

- `AGENTS.md`
- `.aiassistant/rules/AGENTS.md`
- `.aiassistant/rules/CONTEXT_RULES.md`
- `.aiassistant/rules/REPOSITORY_GUIDELINES.md`
- `.aiassistant/runbooks/`

---

## Final Goal

The goal is simple:

- make the AI behave with context
- make engineering decisions explicit
- make repeated work reproducible
- make validation unavoidable

In short, this repository exists to reduce guessing and increase operational rigor.
