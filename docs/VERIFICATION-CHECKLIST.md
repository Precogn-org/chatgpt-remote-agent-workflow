# Verification checklist

## Before opening a PR

- [ ] Confirm repository, branch, and clean/expected working tree.
- [ ] Describe the problem and narrow scope.
- [ ] Record explicit exclusions and related issues.
- [ ] Add or update tests where practical.
- [ ] Report exactly which commands/tests ran and their results.
- [ ] Review the diff for unrelated changes, credentials, personal data, and private URLs.
- [ ] Include risk and importance using the project's established process.
- [ ] Identify whether deployment or configuration changes are required.

## Before human merge

- [ ] Diff reviewed by coordinator or reviewer.
- [ ] Test evidence is clear and reproducible.
- [ ] Required approvals and CI checks are satisfied.
- [ ] No agent has merged without explicit human authorization.

## After merge

- [ ] Read the actual target branch and merge commit.
- [ ] Confirm intended changes are present and exclusions remain excluded.
- [ ] Distinguish tests rerun by verifier from tests merely reported by the author.
- [ ] Update related issue/status records.
- [ ] State deployment status separately: deployed and verified, deployed but unverified, or not deployed.
- [ ] Do not announce production security improvements until runtime behavior is checked.
