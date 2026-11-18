# AI Job-Search Agents

A multi-agent system I built in Claude Code to run my own job search: finding roles, judging fit honestly, tailoring CVs, networking and interview prep. I'm a commercial strategist, not a software engineer. I designed the workflow, wrote the rules, and directed Claude Code to build and run it.

This repo shows the design. The real system holds my CVs, application tracker and contacts, so it stays private. Everything here is rewritten for a fictional candidate.

## The problem

A search across several role types means many job posts, a different CV angle for each, outreach to real people, and interview prep, all at once. Generic AI tools speed this up but make two things worse: they invent experience to match a job post, and they score every role as a good fit. I wanted speed without either problem.

## How it works

```
                    ┌────────────────────────────┐
                    │  Orchestrator              │  owns the rules, the folder map,
                    │  (project architect)       │  and handoffs between agents
                    └─────────────┬──────────────┘
          ┌──────────────┬────────┴─────┬───────────────┐
          ▼              ▼              ▼               ▼
   Agent Scout     Agent Tailor    Agent Connect    Agent Coach
   find + score    fit analysis,   find people,     interview prep,
   job posts       CV, cover       draft messages   story practice
                   letter
          │              │              │               │
          └──────────────┴──────┬───────┴───────────────┘
                                ▼
              Google Sheets tracker + one folder per application
```

One role moves through one conversation: Scout logs it, Tailor analyzes it and builds the CV, Connect drafts outreach, Coach prepares the interviews. The tracker's Status column shows where every role stands.

## Design choices

**Three layers of context.** Every session loads the same project rules (identity, target roles, truth rules, tone, file map). Each agent adds its own spec. Each repeatable task (CV tailoring, cover letters, networking) is a skill with step-by-step method. Rules live in one place, so a change reaches every agent.

**One source of truth for facts.** Agents may only use facts from three files: a master CV, a master profile and a story bank. If a fact is missing, the agent asks instead of writing it.

**Honest fit scoring.** Scout and Tailor score roles against the job post's literal requirements, including function-specific years, level and work-authorization terms. Weak fits are labeled weak.

**People stay in control.** Agents draft; I approve and send. Nothing goes to a recruiter, a form or a public page without my yes.

**The system learns from corrections.** When I correct an agent, the correction is saved as a dated rule with the reason, so the same mistake does not come back in a later session.

## What went wrong, and what changed

- A networking run lost its browser connection halfway, filled the gaps with placeholder names, and wrote nothing to disk. Fix: networking must run through its skill end to end and always writes a file.
- My strategy documents changed, but the rule files the agents load did not, so agents worked from old targets. Fix: agent-loaded rules are the single source, with a dated change log in each file.
- I kept editing a downloaded duplicate of a CV instead of the real file. Fix: agents return the path of the canonical file, never a download.

## Repo contents

- [`docs/agents.md`](docs/agents.md): what each agent does, its inputs, outputs and approval gates
- [`docs/tracker-schema.md`](docs/tracker-schema.md): the application tracker's status values and key columns
- [`examples/CLAUDE.md.example`](examples/CLAUDE.md.example): the layered rules file, for a fictional candidate
- [`examples/skills/truthful-cv-tailoring/SKILL.md`](examples/skills/truthful-cv-tailoring/SKILL.md): a shortened example skill

## Built with

Claude Code (agents, skills, memory), Google Sheets with a small Python helper (tracker), python-docx and LibreOffice (CV editing and page checks), a browser agent (job pages and LinkedIn research).
