# Agents

Each agent has a spec file with its rules and workflow. All agents share the project rules and may only use facts from the master CV, master profile and story bank.

## Agent Scout: find and score roles

- **Mode A, search:** runs parallel sub-agents, one per target role type, across company career sites and job boards. Each sub-agent checks that the post is live, reads the posting date, and skips duplicates already in the tracker.
- **Mode B, my links:** I paste job links; Scout opens each one, scores it and logs it.
- **Output:** a tracker row per role with a fit score, a short fit note and the posting date.
- **Gate:** I decide which roles move to Tailor.

## Agent Tailor: fit analysis, CV and cover letter

- **Phase 0:** confirm the job is still open.
- **Phase 1:** fit analysis against the job post's literal requirements, scored on a fixed rubric, with gaps stated plainly.
- **CV:** starts from the closest base CV for that role type and edits it as tracked changes, so every change is visible. Hard limits: one page, no invented facts, consistent formatting.
- **Cover letter:** a fixed three-part structure, written only from verified material.
- **Gate:** I review the tracked changes and accept or reject each one before I submit.

## Agent Connect: networking

- Finds real, current employees who match the role: recruiters for that function, the likely hiring team, and alumni.
- Drafts connection notes and follow-ups within LinkedIn's character limits, with a different message for each type of person.
- Writes one networking file per application and logs contacts in the tracker.
- **Gate:** I send every message myself.

## Agent Coach: interview prep

- Builds a prep pack per interview round: company and product context, likely questions, and which stories from the story bank answer them.
- Runs mock interviews and gives feedback on structure and delivery.
- Logs each round's date, format, interviewer and outcome in the tracker.

## Orchestrator

Owns the project rules, the folder map, skills and scripts, and the handoffs between agents. When a rule changes, the Orchestrator updates the file that owns it and records the change with a date and a reason.
