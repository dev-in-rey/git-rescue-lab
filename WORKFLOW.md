# WORKFLOW

## 1) Bisect finding from Task 1
`git bisect` identified commit `c99fb4209e6fb6e5ed2789893fdb2f893d61d6c6` as the first bad commit; it changed the BULK20 check so carts with exactly 5 items no longer received the discount.

## 2) Recommended branching strategy for a team of 4
GitHub Flow is the best fit: each change goes into a short-lived branch, is reviewed in a pull request, and merges back to `main` after checks pass. It keeps process overhead low while still enforcing code review and CI discipline.

## 3) How to fully remove the old secret from history
You must rewrite repository history (for example with `git filter-repo` or BFG), force-push the rewritten refs, and have all collaborators re-sync to the new history; you should also rotate/revoke the leaked credential. This assignment did not require that full rewrite because it is disruptive to shared history and the lab only required stopping current tracking plus adding ignore protection.

## 4) Why rewriting history was acceptable in Task 2 but not after teammates pulled
It was acceptable in Task 2 because the commits were still local/private and no teammates depended on those commit IDs. Rewriting commits that teammates already pulled would break their histories and require manual repair (rebase/reset/cherry-pick), creating avoidable collaboration risk.
