
# Huddlehouse AI Usage Guidelines

Welcome to the AI corner!

Nova and Pip love useful tools. AI can help writers work more efficiently, identify potential content problems, and explore better ways to explain complicated information.

But AI can also make mistakes.

These guidelines explain how the Huddlehouse documentation team uses AI responsibly.

## 1. What AI can help us do

AI tools can support several documentation activities.

| Activity | Example |
|---|---|
| Editorial review | Identify unclear sentences and unnecessary repetition |
| Style checking | Compare wording against the Huddlehouse Style Guide |
| Content gap analysis | Identify missing prerequisites or expected results |
| Summarization | Summarize approved product information |
| Release notes | Create a first draft from verified release details |
| Troubleshooting | Suggest possible questions or missing diagnostic steps |
| Maintenance | Identify potentially outdated references and links |

AI suggestions are starting points. They are not automatically approved content.

## 2. What AI must not decide alone

AI must not independently approve:

- Product behavior
- Commands and command-line options
- API parameters
- Security requirements
- Configuration instructions
- Release dates or availability
- Technical compatibility claims

These details require verification against authoritative information.

Engineering or the appropriate product subject matter expert must confirm technical accuracy.

## 3. Protect information

Before using an AI tool, consider the information being shared.

Never submit confidential customer data, credentials, passwords, private keys, security-sensitive information, or restricted company material to an unapproved AI service.

Follow the organization's data handling and AI tool approval policies.

Use fictional or approved sample content for demonstrations and training.

## 4. Write useful prompts

A good prompt explains:

1. The role AI should perform.
2. The intended audience.
3. The task.
4. The standards to follow.
5. The information AI is allowed to use.
6. What the response should look like.

### Example: Style guide review

**Prompt:**

You are an editorial assistant reviewing Huddlehouse documentation.

Review the supplied text against the Huddlehouse Documentation Style Guide.

Check for:

- Inconsistent terminology
- Unclear sentences
- Passive voice where active voice would be clearer
- Unnecessary repetition
- Heading and formatting inconsistencies
- Missing context

Do not invent technical facts or change product behavior.

Return a table with:

- Original text
- Potential issue
- Suggested revision
- Reason for the suggestion

Flag uncertain issues instead of guessing.

### Example: Content gap analysis

**Prompt:**

Review the supplied user guide from the perspective of a first-time user.

Identify potential missing information, including:

- Prerequisites
- Required permissions
- Ordered steps
- Expected results
- Troubleshooting guidance
- Relevant links

Do not create missing technical instructions.

List each potential gap and explain what information needs confirmation from the product team.

## 5. Evaluate AI-generated suggestions

When reviewing AI output, ask:

- Is the suggestion accurate?
- Does it preserve the intended meaning?
- Does it follow the Style Guide?
- Is it appropriate for the intended audience?
- Does it introduce an unsupported technical claim?
- Does it remove important information?
- Does it make the instructions easier to follow?

Accept useful suggestions, revise incomplete ones, and reject inaccurate recommendations.

## 6. The human review process

Every AI-assisted documentation change follows a human review process.

1. The writer provides approved source information.
2. AI evaluates the content using a defined prompt.
3. AI returns potential issues and suggestions.
4. The writer reviews each recommendation.
5. Engineering verifies technical details when required.
6. The writer makes the final editorial decisions.
7. The approved content enters the normal review and publication process.

## 7. Evaluating AI quality

AI tools should be evaluated rather than trusted automatically.

The documentation team can test them using sample documents containing known issues.

Measure whether the tool:

- Identifies real style problems
- Detects inconsistent terminology
- Finds intentionally missing prerequisites
- Avoids inventing technical details
- Provides useful explanations
- Produces consistent results

Track false positives and missed issues.

A tool that produces many suggestions is not necessarily a good tool. The suggestions must be useful.

## 8. Improving prompts

When results are poor, improve the prompt.

For example:

**Problem:** AI rewrites technical terminology.

**Improvement:** Explicitly tell the tool to preserve approved product names, configuration keys, commands, and API terminology.

**Problem:** AI invents missing setup instructions.

**Improvement:** Tell the tool to identify missing information without creating instructions.

**Problem:** AI returns vague feedback.

**Improvement:** Request the original sentence, specific issue, suggested revision, and explanation.

## 9. Approved AI tools

Use only AI tools approved for the information being processed.

Examples of tools that may support documentation work include:

- ChatGPT
- Claude
- Microsoft Copilot
- Gemini

Tool availability and data-handling permissions must be confirmed by the organization.

## 10. The Huddlehouse rule

AI helps us inspect, evaluate, and improve documentation.

Humans remain responsible for:

- Accuracy
- Editorial decisions
- Technical verification
- Appropriate information handling
- Final approval

> Nova says: Let AI help with the heavy lifting.
>
> Pip says: But always check what it brings back!

## Final checklist

- [ ] The AI tool is approved for the information being used.
- [ ] The prompt identifies the task and audience.
- [ ] The correct Style Guide is supplied or referenced.
- [ ] Technical information comes from approved sources.
- [ ] AI suggestions are evaluated individually.
- [ ] Unsupported claims are rejected.
- [ ] Required subject matter experts verify technical details.
- [ ] A human approves the final content.
