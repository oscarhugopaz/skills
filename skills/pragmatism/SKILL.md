---
name: pragmatism
description: Guides durable engineering judgment for software design, implementation, refactoring, debugging, and review. Use when deciding scope, choosing between designs, simplifying code, evaluating trade-offs, or judging how much change a problem deserves.
---

# Pragmatism

Pragmatism is disciplined judgment under real constraints. Build what solves the problem, fits the system, and can be maintained by the next person.

## Start With Reality

Understand the actual problem before changing code.
Read the surrounding system until the change has a natural home.
Prefer evidence from code, behavior, tests, logs, and users over guesses.
Separate the reported symptom from the underlying cause.
Solve the shared cause when the same flaw can surface through multiple paths.
Do not satisfy the wording of a request while leaving the real problem intact.

## Respect The Existing System

Treat the codebase as the record of decisions already paid for.
Follow established conventions unless they block the change or cause harm.
Reuse local patterns, helpers, and boundaries before introducing new ones.
Improve the current design before replacing it.
Make the new code look inevitable in its surroundings.
Avoid novelty that future maintainers must decode before they can work.

## Prefer The Smallest Complete Change

Make the smallest change that fully solves the problem.
Small does not mean partial. Preserve behavior, invariants, and coherence.
Delete code when deletion is the clearer fix.
Avoid speculative features, unused options, and flexibility with no present caller.
Do not build the second implementation before the second need exists.
Stop when the problem is solved and the remaining work is only imagined.

## Keep Complexity Honest

Every abstraction must earn its cost.
Add a layer only when it removes real duplication, clarifies ownership, or protects a boundary that already matters.
Prefer direct code over indirection that only renames the same idea.
Prefer boring structures that reveal intent quickly.
Do not hide simple behavior behind architecture.
Let complexity live only where the domain requires it.

## Own What You Add

Treat every dependency, flag, setting, public surface, and extension point as future maintenance.
Add a dependency only when it clearly beats what the platform, standard library, or codebase already provides.
Prefer fewer moving parts when the behavior is stable and local.
Prefer explicit ownership when the behavior crosses boundaries or affects data, security, money, or trust.
Leave fewer things to configure unless variation is already real.

## Preserve The Hard Parts

Never simplify away correctness, security, data integrity, accessibility, observability, or recovery from failure.
Validate at trust boundaries.
Handle errors where ignoring them would lose data, corrupt state, or mislead users.
Keep edge cases that the domain actually needs.
Choose the simple robust option over the simple fragile one.

## Refactor With Purpose

Refactor when it makes the requested change safer, removes proven duplication, or clarifies a boundary.
Do not refactor to express taste.
Keep unrelated cleanup separate unless it is required to finish safely.
Prefer incremental improvement over dramatic rewrites.
Leave the system easier to change along the path it is already taking.

## Explain Trade-Offs

Name the cost of the chosen solution.
Name what was deliberately not built.
Name the condition that would justify revisiting the decision.
Prefer a clear limitation over hidden ambition.
Make future work visible without making it today's work.

## Finish With Evidence

Verify the behavior at the smallest useful level.
Match verification effort to risk.
Use existing checks when they already cover the change.
Add focused checks when the change introduces logic, fixes a bug, or protects a contract.
Do not let verification become a second place to speculate.

## Default Posture

Read first.
Find the cause.
Change less.
Reuse more.
Name trade-offs.
Protect the hard parts.
Leave maintainable code.
