# Local cpplint Agent Rules

Goal: make high-quality, reviewable contributions to cpplint.

## Authority
- The human user makes all final decisions.
- Never open, submit, approve, merge, or close a PR without explicit user approval.
- Never claim something is correct unless tests or direct code reasoning support it.

## Git
- Official upstream: cpplint/cpplint.
- Base work on upstream/develop.
- Never make feature changes directly on develop.
- Use one branch per issue or PR review.
- Never force-push.
- Never rewrite unrelated history.

## Scope
- Keep changes narrowly scoped to the selected issue.
- Do not perform unrelated refactors.
- Do not modernize code merely because it looks old.
- Preserve backwards compatibility unless the issue explicitly requires otherwise.
- Before implementing a fix, reproduce or understand the problem first.

## cpplint contribution requirements
For code changes:
- Add or update relevant tests, normally in cpplint_unittest.py.
- Update CHANGELOG.rst when appropriate.
- Explain the problem being solved.
- Prefer minimal changes over architectural rewrites.

## Validation
Before presenting work as complete, run:
1. Relevant targeted test.
2. python -m pytest
3. python -m pylint cpplint.py
4. pre-commit run --all-files

Report exact commands and results.

## Reviews
When reviewing a PR:
- Read the issue and PR context.
- Inspect the actual diff.
- Try to reproduce the bug when practical.
- Run relevant tests.
- Look for regressions and backwards-compatibility problems.
- Do not approve merely because CI is green.
- Distinguish confirmed problems from speculation.

## AI assistance
AI may implement or analyze code, but:
- generated code must be inspected;
- assumptions must be stated;
- no mass-generated issues, PRs, comments, or reviews;
- quality matters more than contribution count.

If uncertain, stop and explain the uncertainty instead of guessing.
