---
name: jira-ticket
description: Create a Jira ticket from the current context — code changes, bug description, or feature request
arguments:
  - name: type
    description: "Issue type: bug, story, task, or spike (default: task)"
    required: false
  - name: project
    description: Jira project key (e.g., PROJ)
    required: false
---

# Jira Ticket Command

Create a well-structured Jira ticket based on the current context.

## Steps

1. **Gather context**: Look at recent code changes (`git diff`), conversation history, and any error messages to understand what the ticket should describe
2. **Determine issue type**: Use the provided type argument, or infer from context:
   - Bug: error reports, failing tests, unexpected behavior
   - Story: new user-facing functionality
   - Task: technical work, refactoring, infrastructure
   - Spike: research or investigation needed
3. **Draft the ticket**:
   - **Summary**: Clear, concise title (under 80 characters)
   - **Description**: Context, reproduction steps (for bugs), or requirements (for stories)
   - **Acceptance criteria**: Measurable definition of done
   - **Labels**: Relevant team/area labels
4. **Confirm with user**: Show the draft and ask for confirmation before creating
5. **Create the ticket**: Use the Jira MCP tools to create the issue in the specified project
