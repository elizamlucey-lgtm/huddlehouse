
# Projects: Documentation Planning and Delivery

Welcome to Projects!

Nova and Pip are here to help the documentation team plan work, coordinate reviews, and deliver accurate, useful content.

A documentation project is more than writing a page. It includes understanding the request, gathering reliable information, working with subject matter experts, testing instructions, reviewing content, and publishing the finished result.

This guide explains how the Huddlehouse documentation team manages that work.

> **Nova:** Let's make the work visible.
>
> **Pip:** And let's make sure it's ready before we ship it!

## 1. Start with a clear request

Every documentation task should explain what needs to change and why.

A useful task includes:

- **Purpose:** What problem are we solving?
- **Audience:** Who needs this information?
- **Scope:** Which guides, pages, examples, or workflows are affected?
- **Source information:** Where will the technical details come from?
- **Owner:** Who is responsible for moving the task forward?
- **Priority:** How important or time-sensitive is the work?
- **Acceptance criteria:** How will we know the task is complete?

For example:

**Task:** Update the CLI installation guide.

**Purpose:** Customers need clearer installation instructions.

**Audience:** Developers installing the product for the first time.

**Scope:** Installation steps, command options, prerequisites, and expected output.

**Source information:** Approved CLI reference and Engineering confirmation.

**Acceptance criteria:**

- Installation instructions have been tested.
- Commands and flags match the current product.
- Prerequisites are clearly identified.
- Expected results are documented.
- Editorial review is complete.

A clear request helps the team avoid rework.

## 2. Move work through the project board

The Projects board uses four workflow stages.

| Stage | What it means |
|---|---|
| Backlog | The task is identified but work has not started |
| In Progress | Someone is actively researching, writing, or testing |
| In Review | The draft is being checked by reviewers |
| Ready to Publish | Required reviews and validation are complete |

A task should move forward when its required work is complete—not simply because a deadline is approaching.

## 3. Follow the documentation delivery workflow

### Step 1: Draft

The writer gathers requirements and approved source information.

Activities may include:

- Reviewing product requirements
- Interviewing subject matter experts
- Examining existing documentation
- Identifying gaps and dependencies
- Creating or updating the draft

### Step 2: Technical review

The appropriate subject matter expert verifies technical details.

Review may include:

- Product behavior
- Installation and configuration steps
- Commands and command-line flags
- API parameters and examples
- Permissions and security requirements
- Compatibility and version information

The writer records questions and updates the draft based on verified feedback.

### Step 3: Editorial review

The content is checked for clarity, consistency, and usability.

Review may include:

- Organization and heading structure
- Terminology and product names
- Sentence clarity and plain language
- Style-guide consistency
- Accessibility
- Links and cross-references

### Step 4: QA and validation

Documentation is tested before publication.

Examples include:

- Following procedures from a clean starting point
- Running approved commands in a safe test environment
- Checking sample requests and responses
- Verifying links and navigation
- Comparing examples against current specifications
- Confirming expected results

A technically accurate sentence is not enough if the procedure does not work when a reader follows it.

### Step 5: Publish

The approved changes enter the normal source-control and publication workflow.

The team confirms:

- Required approvals are complete.
- The pull request is approved and merged.
- The published content is available.
- Release notes or announcements are ready.
- Related documentation links are updated.

## 4. Collaborate using Git and pull requests

Huddlehouse uses a docs-as-code workflow for documentation changes.

A typical process looks like this:

1. Start from the current main branch.
2. Create a feature branch for the documentation change.
3. Edit Markdown, YAML, or other required source files.
4. Preview and test the changes.
5. Commit the work with a clear message.
6. Push the branch to the remote repository.
7. Open a pull request.
8. Request technical and editorial review.
9. Address review comments.
10. Merge the approved change.

A pull request should explain:

- What changed
- Why the change was needed
- Which documentation areas were affected
- What testing or validation was performed
- Which reviewers are needed

Review comments should be specific and actionable.

## 5. Manage dependencies and release milestones

Some documentation tasks depend on work outside the documentation team.

Examples:

- A command reference depends on Engineering confirming the current syntax.
- A release note depends on Product approving the release details.
- An integration guide depends on an updated compatibility matrix.
- A troubleshooting article depends on Support identifying recurring customer issues.

Record dependencies in the task so the team can see what is blocking progress.

A release milestone groups related documentation tasks around a planned product release.

The documentation owner should track:

- Required deliverables
- Technical review status
- Editorial review status
- Testing status
- Publication dependencies
- Customer communication

## 6. Use the Style Guide as the editorial source of truth

The Huddlehouse Documentation Style Guide defines how documentation should look and sound.

Use it when:

- Creating new content
- Reviewing an existing page
- Choosing terminology
- Writing instructions and examples
- Editing AI-assisted drafts
- Preparing release notes

The Style Guide helps different writers create a consistent experience.

[Open the Documentation Style Guide](../huddle/style-guide.md)

## 7. Use AI as a review assistant

AI can help identify possible issues before a document enters human review.

Examples include:

- Style and terminology checks
- Plain-language suggestions
- Content gap analysis
- Repetition and consistency checks
- Release-note draft reviews
- Potentially outdated references

AI output is not automatically correct.

Writers must evaluate suggestions, and subject matter experts must verify technical claims.

The Huddlehouse AI Usage Guidelines explain approved practices:

[Open AI Usage Guidelines](../huddle/ai-guidelines.md)

The AI Review Playbook provides reusable prompts and a structured evaluation process:

[Open the AI Review Playbook](../ai-review-playbook.md)

## 8. Know when a task is complete

Before moving a task to Ready to Publish, confirm:

- [ ] The request and audience are understood.
- [ ] The content uses approved source information.
- [ ] Required technical review is complete.
- [ ] Editorial review is complete.
- [ ] Commands, examples, and procedures have been validated.
- [ ] Links and navigation have been checked.
- [ ] Style-guide requirements have been considered.
- [ ] AI suggestions, if used, have been reviewed by a human.
- [ ] The pull request has the required approvals.
- [ ] Publication and release communication are ready.

## 9. The Huddlehouse approach

Good documentation is a team effort.

Writers organize and explain information. Engineers verify product behavior. Product teams clarify intended functionality. Support and Customer Success share customer needs.

Projects gives that work a visible path from request to publication.

> **Nova:** A task isn't finished just because the draft is written.
>
> **Pip:** It's finished when the reader can use it successfully!
