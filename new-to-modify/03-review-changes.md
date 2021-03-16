---
id: review-changes
title: Review changes
kind: doc
---

## Review changes

### Create a review

A [reference/#Review] allows you to peer review changes on a source branch before merging them into a target branch.

To create one, navigate to the Reviews page using the left navigation bar and click the Create review button.

First select a source branch to review and a target branch to merge into. Check the diff shows the expected changes.

Next, name your review, assign a reviewer(s) and click the Create review button.

### Perform a review

In the review, review assignees can use the activity tab to write comments, the changes tab to review changes and commit additional changes, and the merge tab to merge changes from a source into a target branch.

Before you can merge, at least one reviewer must approve the changes and the automated merge checks must pass.

Automated merge checks will fail when:

- The target branch has diverged from the source branch: you must perform a branch update on your source branch before merging
- There are uncommitted changes on your source or target branches: you will need to commit these before merging
- There are merge conflicts on your source branch: you will need to resolve conflicts before merging.

Once these checks have passed, click the Merge button to fast forward merge your source into your target branch.

Once merged, the status of your review will change from `pending` to `merged`. You can now navigate to the target branch in your repository and observe the integrated changes.
