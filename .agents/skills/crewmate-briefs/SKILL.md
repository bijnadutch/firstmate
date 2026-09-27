---
name: crewmate-briefs
description: >-
  Agent-only authoring contract for Firstmate ship, scout, and charter briefs.
  Load before scaffolding, filling, or regenerating any brief, including a scout promotion's implementation brief.
user-invocable: false
metadata:
  internal: true
---

# Crewmate briefs

`bin/fm-brief.sh` and its help own scaffold syntax, generated variants, status protocol, delivery-mode definitions of done, and exact safety mechanics.
`AGENTS.md` section 11 owns the always-loaded load trigger and the worktree-isolation assertion that a ship brief must keep.
Use the scaffold as the contract and alter generated sections only when the task genuinely differs from the standard shape.

## Filling the task subsections

Fill `## Captain's intent` (`{TASK}`) with the captain's own ask and any boundary the captain stated, plus the context needed to read it, including the substance of any report, decision, or PR the ask refers to.
Never widen the ask there into a general goal or an enumerated coverage list, because the reviewer treats that subsection as acceptance criteria.
Fill `## Firstmate spec` (`{FIRSTMATE_SPEC}`) with only the build instructions that ask requires, naming what stays out of scope when the ask is narrow.
A generalization, consistency sweep, or extra hardening the captain did not ask for is follow-up work to note, not scope to add.
Keep additions task-specific rather than repeating lifecycle instructions.
`bin/fm-dod-lib.sh` owns intent authoring without added speaker labels or direct address, its provenance markers, what a no-mistakes worker may pass as `--intent`, and the string's self-sufficiency rule.
`AGENTS.md` section 7 owns the mid-task rule for appending a captain's later ask to a brief already in flight.

## Required guards

If a ship task touches firstmate's shared tracked material, explicitly require `firstmate-coding-guidelines` before editing; that skill's trigger-hygiene section owns why the scaffold cannot add this instruction for you.
If a task will drive Herdr lifecycle behavior, scaffold with `--herdr-lab`; if that need appears after an unguarded scaffold, stop and regenerate rather than adding commands by hand.
The generated Herdr contract must use a named non-`default` isolated lab and its guarded helper for every lifecycle action.

## Status and charters

Status appends are sparse supervisor-actionable events, not routine progress; `bin/fm-classify-lib.sh` owns keyed open and resolved semantics.
Load `secondmate-provisioning` before creating or using a charter brief and preserve its idle-by-default and marked-return-channel contracts.
