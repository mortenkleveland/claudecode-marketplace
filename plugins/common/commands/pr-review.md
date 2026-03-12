---
name: pr-review
description: Review a pull request for code quality, correctness, and team conventions
arguments:
  - name: pr
    description: PR number or URL to review
    required: true
---

# PR Review Command

Review the specified pull request thoroughly.

## Steps

1. **Fetch PR details**: Get the PR diff, description, and linked issues using `gh pr view $ARGUMENTS.pr` and `gh pr diff $ARGUMENTS.pr`
2. **Understand context**: Read the PR description and any linked Jira tickets to understand the intent
3. **Review the diff**:
   - Check for correctness and potential bugs
   - Verify error handling is adequate
   - Look for security issues (injection, XSS, secrets, etc.)
   - Check naming conventions and code style consistency
   - Verify tests cover new/changed functionality
   - Look for performance concerns
4. **Summarize findings**: Provide a structured review with:
   - **Summary**: What the PR does in 1-2 sentences
   - **Approval recommendation**: Approve / Request Changes / Needs Discussion
   - **Issues found**: Categorized as Critical / Warning / Suggestion
   - **Positive notes**: Good patterns or improvements worth calling out
