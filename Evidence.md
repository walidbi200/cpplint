# Maintainer evidence

Live-state snapshot: 2026-09-22. GitHub links and exact SHAs are authoritative for this snapshot only; refresh before using this document in an application.

## Current review coverage

The detailed audit is in [`cpplint-local-logs/current-review-coverage-audit.md`](../cpplint-local-logs/current-review-coverage-audit.md). At this snapshot there are 18 open PRs: one authored by `walidbi200` and 17 requiring independent review. All 17 have a submitted public review by `walidbi200` anchored to the exact live head SHA. This means current-head coverage is complete at the snapshot; it does not mean every PR is approved.

| PR | Head SHA | Public review state | Current-head verification |
|---:|---|---|---|
| [#473](https://github.com/cpplint/cpplint/pull/473) | `1be454680df8dd9239ee1a7fa4a12c8b4e93df89` | APPROVED | verified |
| [#470](https://github.com/cpplint/cpplint/pull/470) | `d160830482ddd092abc2b0943232ad851a8fdc04` | APPROVED | verified |
| [#469](https://github.com/cpplint/cpplint/pull/469) | `b497da2f561ab66649ffe59cacb377d69589a6c6` | APPROVED | verified |
| [#468](https://github.com/cpplint/cpplint/pull/468) | `307051b9d4b285f717e7503f0740a6464eb70aa2` | APPROVED | verified |
| [#464](https://github.com/cpplint/cpplint/pull/464) | `91557ed1aa846c72ec7d32e48d77978755fb4a20` | CHANGES_REQUESTED | verified |
| [#463](https://github.com/cpplint/cpplint/pull/463) | `d736a62355d78377579e6879b5ab8307775e9b2e` | APPROVED | verified |
| [#458](https://github.com/cpplint/cpplint/pull/458) | `c6a64d4409fe1f1707b3fbc5b46606cee5628069` | CHANGES_REQUESTED | verified |
| [#457](https://github.com/cpplint/cpplint/pull/457) | `b4371d21885b2dc2e4d6e07ca3fbcff8eb718ed6` | APPROVED | verified |
| [#456](https://github.com/cpplint/cpplint/pull/456) | `7914485ddcce8227ef2e001423069ae2512857f6` | CHANGES_REQUESTED | verified |
| [#454](https://github.com/cpplint/cpplint/pull/454) | `fee646d9af3f4ee5e70bb5a235b057c797230940` | CHANGES_REQUESTED | verified |
| [#450](https://github.com/cpplint/cpplint/pull/450) | `8e213e741ba1f1bbc83207fb15a3fc868488bcdb` | APPROVED | verified |
| [#449](https://github.com/cpplint/cpplint/pull/449) | `2e8aa7d5da83fd291ddbce07243ae537cdde5e61` | CHANGES_REQUESTED | verified |
| [#448](https://github.com/cpplint/cpplint/pull/448) | `62c0094e9d5d8f805efdadaa7f779ddcd3fabafb` | APPROVED | verified |
| [#447](https://github.com/cpplint/cpplint/pull/447) | `cd67aa7c575948de807659693534bd40ec1dd379` | CHANGES_REQUESTED | verified |
| [#389](https://github.com/cpplint/cpplint/pull/389) | `a44637ea662d54dd70fe477cd268b00174ada607` | CHANGES_REQUESTED | verified |
| [#381](https://github.com/cpplint/cpplint/pull/381) | `e89746cffe0e5b8ff23a3607602da7efe32ea965` | CHANGES_REQUESTED | verified |
| [#377](https://github.com/cpplint/cpplint/pull/377) | `f44a09acf0a936fecda31f23cd6c049d63d48044` | CHANGES_REQUESTED | verified |

State distinctions used here:

- **Investigated locally**: behavior or code was checked in a local worktree.
- **Public review submitted**: GitHub records a submitted review.
- **Public review verified current on latest head**: the latest review's `commit_id` exactly equals the live PR head SHA.

## High-signal review findings

### #463 — percent-path crash and verified author fix

- Initial submitted review at `db3dfc930f030a8e387cf86b71a7643c5e38cedf`: reproduced a non-quiet crash for an excluded path such as `percent%2f/baz.cc`; the newly supported relative-path route fed a literal `%` path into later percent formatting. [Review](https://github.com/cpplint/cpplint/pull/463#pullrequestreview-5192744294)
- Author fixed the failure and added quiet/non-quiet coverage for percent characters in the target, config path, and pattern.
- Follow-up submitted approval at current head `d736a62355d78377579e6879b5ab8307775e9b2e`: reproduced the old failure, verified literal output on the fixed head, then ran focused/full tests and repository validation. [Follow-up](https://github.com/cpplint/cpplint/pull/463#pullrequestreview-5240129095)

### #470 — filesystem identity/path correctness and verified author fix

- Initial submitted review at `1592d0bd72feb5516aeb8e35a743f3e3272fefdc`: found both false-positive and false-negative same-directory-header behavior through a symlink plus `..`, and self-include suppression through symlink/hard-link aliases. [Review](https://github.com/cpplint/cpplint/pull/470#pullrequestreview-5192193211)
- Author changed the implementation to use real-path/file-identity handling and added regressions.
- Follow-up submitted approval at current head `d160830482ddd092abc2b0943232ad851a8fdc04`: re-ran all four original failure modes plus ordinary, missing, invalid, symlink, broken-symlink, and fallback cases. [Follow-up](https://github.com/cpplint/cpplint/pull/470#pullrequestreview-5260936772)

### #456 — independent `LINT_C_FILE` / IWYU state inconsistency

- Submitted change request at current head `7914485ddcce8227ef2e001423069ae2512857f6`: showed that `ProcessGlobalSuppressions()` can honor `/* LINT_C_FILE */` before multiline-comment removal while `ProcessFileData()` later derives IWYU language mode from mutated `raw_lines`, producing C suppressions but a C++ `<cstdio>` suggestion. It also documented the test-helper aliasing hazard and an outstanding required Ruff failure. [Review](https://github.com/cpplint/cpplint/pull/456#pullrequestreview-5261161475)

### #377 — function-pointer/noexcept gap and real-cast suppression

- Submitted change request at current head `f44a09acf0a936fecda31f23cd6c049d63d48044`: verified the exact #354 case but found missed spaced/commented function-pointer declarations and false negatives for real adjacent C-style pointer casts such as `(uintptr_t)(void*)p`. [Review](https://github.com/cpplint/cpplint/pull/377#pullrequestreview-5261269774)
- Built and validated a narrower local candidate based on declarator context; focused/full unit tests, pylint, mypy, pre-commit, and diff checking passed. This candidate was not pushed.

### #447 — requires-expression and template-boundary coverage

- Submitted current-head change request at `cd67aa7c575948de807659693534bd40ec1dd379`: independently reproduced outstanding `requires`-expression continuation, multiline function-template definition, and inner template-template/outer span failures. [Review](https://github.com/cpplint/cpplint/pull/447#pullrequestreview-5273206237)

## Follow-through evidence

The clearest complete blocker → author change → new-head fetch → re-test → updated review chains are:

1. [#463 initial change request](https://github.com/cpplint/cpplint/pull/463#pullrequestreview-5192744294) → author fix → [current-head approval](https://github.com/cpplint/cpplint/pull/463#pullrequestreview-5240129095).
2. [#470 initial change request](https://github.com/cpplint/cpplint/pull/470#pullrequestreview-5192193211) → author fix → [current-head approval](https://github.com/cpplint/cpplint/pull/470#pullrequestreview-5260936772).

These are stronger responsibility evidence than raw review counts because they show the original claim was re-tested against later code rather than left as a stale thread.

## Authored contributions

GitHub search currently finds one cpplint PR authored by `walidbi200`:

- [#474 — `fix: handle operators after brace initialization`](https://github.com/cpplint/cpplint/pull/474), linked to [#373](https://github.com/cpplint/cpplint/issues/373), open, non-draft, unmerged, current head `15836727ece29678e2be254e34d7acaf47008cfb`.
- The original #373 failure was reproduced on `upstream/develop`; the PR fixes it and includes an operator matrix.
- Private adversarial self-review found a block-brace false negative at the current head. A local uncommitted candidate and regression exist; full candidate validation passed. Therefore this document does **not** claim the current public head is ready to merge. See [`pr-474-self-review.md`](../cpplint-local-logs/pr-474-self-review.md).
- No human review has been submitted on #474 at this snapshot. CodeRabbit reported no actionable comments. Merge status: **not merged**.

## Maintainer interactions and responsibility status

[Issue #402](https://github.com/cpplint/cpplint/issues/402) asks for more maintainers. Maintainers explicitly told candidates to review/comment on open work, identify unclear or duplicate issues, identify PRs ready to merge, and—most specifically—to approve or disapprove every open PR they did not author. [Maintainer guidance](https://github.com/cpplint/cpplint/issues/402#issuecomment-4976719712)

Current status for `walidbi200`:

- Volunteered responsibility: **not yet posted in #402**.
- Maintainer acknowledgement of this contributor’s recurring work: **none verified**.
- Explicit recurring assignment: **none verified**.
- Collaborator/triage/write permission: **none verified**.
- Formal maintainer status: **none verified**.

The current review coverage satisfies the concrete public guidance at this snapshot, but it is evidence supporting a request—not proof that responsibility or permissions were granted.

## Application evidence checklist

- [ ] Refresh GitHub account age from the live profile immediately before application.
- [ ] Refresh recent public OSS activity; link only relevant, substantive work.
- [ ] Verify cpplint’s OSI-license/project status from primary repository/package metadata.
- [ ] Refresh cpplint package usage evidence from current authoritative package sources; do not reuse old download/dependent counts.
- [ ] Obtain or accurately report formal/explicit recurring maintainer responsibility. Current state: none granted.
- [x] Strong review links: #463, #470, #456, #377, #447 above.
- [ ] Resolve #474’s private self-review blocker, then refresh its head, CI, and review status.
- [ ] Refresh the current Anthropic/Claude for Open Source program requirements from the official program source immediately before application.
- [ ] Re-run the current-head coverage audit immediately before any claim of complete coverage.
