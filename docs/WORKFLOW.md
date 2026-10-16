# Workflow lifecycle and responsibilities

## 1. Define the change

The human states the desired outcome, boundaries, risk tolerance, and acceptance criteria. The coordinator turns this into a bounded task and identifies any decision that must return to the human.

## 2. Inspect before acting

Read the current branch, repository status, related issues/PRs, relevant source, tests, and deployment model. Never infer that a change is live just because it exists on a branch.

## 3. Implement and document

The coding agent makes the smallest useful change, adds or updates tests, and prepares a diff. The PR should explain scope, exclusions, test evidence, risk, importance, and rollout requirements.

## 4. Review and merge

The coordinator checks the diff and test evidence. The human reviews and performs the merge. Agents must not silently cross a human-approval boundary.

## 5. Verify the merged state

A separate verifier inspects the actual target branch and commit. It should report:

- exact commit and files checked;
- tests it ran itself versus tests reported by others;
- differences between PR claims and merged code;
- known exclusions and follow-up issues;
- whether production deployment was independently confirmed.

## 6. Deploy separately

Deployment or service restart requires its own authorization. After deployment, check the running service through a suitable health check or behavior test. If no such check happened, state that production status is unverified.

## Responsibility map

| Role | Responsibility | Must not imply |
|---|---|---|
| Human | Goals, permissions, final merge/deploy decisions | That an agent's claim is proof |
| ChatGPT coordinator | Plan, inspect, draft, edit, coordinate, report | That a command succeeded without evidence |
| Coding agent | Bounded implementation and tests | That a merged change is deployed |
| Independent verifier | Check repository state and evidence | That tests ran if it only inspected their files |
| GitHub | Durable source of truth for diffs and review history | That production matches `main` |
| VPS/runtime | Execute and host the code | That local state equals deployed state |
