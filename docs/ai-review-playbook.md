
# AI Review Playbook

Welcome to the Huddlehouse AI Review Lab!

AI can help documentation teams inspect content, identify possible problems, and work more efficiently.

But a useful AI workflow needs more than a clever prompt. It needs clear instructions, approved source material, measurable expectations, and human review.

This playbook gives writers a repeatable approach.

> **Nova:** AI can help us spot things we might miss.
>
> **Pip:** But we still have to check its homework!

## 1. The AI-assisted review cycle

Use this process when asking an AI tool to review documentation.

1. **Prepare:** Gather the draft, approved source information, and applicable editorial standards.
2. **Prompt:** Explain the audience, review task, constraints, and expected output.
3. **Inspect:** Ask AI to identify possible issues and explain its findings.
4. **Evaluate:** Review each suggestion for accuracy and usefulness.
5. **Verify:** Ask the appropriate subject matter expert to confirm technical details.
6. **Revise:** Make the editorial decisions and update the document.
7. **Record:** Document significant changes and complete the normal review process.

AI is an assistant in this workflow, not an approver.

## 2. Prompt structure

A strong prompt gives the tool enough context to perform a specific task.

Include these elements:

| Element | What to provide |
|---|---|
| Role | The perspective AI should take |
| Audience | Who will read the documentation |
| Task | What you want reviewed |
| Standards | The style guide or editorial rules |
| Source | The approved information AI may use |
| Constraints | What AI must not change or assume |
| Output | The format in which findings should be returned |

Avoid vague instructions such as "Make this better."

Instead, explain what better means for the current document.

## 3. Prompt: Style-guide review

**Use when:** A draft needs an editorial consistency check.

**Prompt:**

You are an editorial assistant reviewing technical documentation for Huddlehouse.

Compare the supplied draft against the provided Huddlehouse Documentation Style Guide.

Review for:

- Inconsistent terminology
- Product-name capitalization
- Unclear or overly complex sentences
- Unnecessary repetition
- Heading hierarchy and structure
- UI-label formatting
- Inconsistent instructions or formatting
- Accessibility and plain-language concerns

Do not invent technical facts or change product behavior.

Preserve approved product names, commands, configuration keys, code, and API terminology.

Return a table containing:

1. Original text
2. Potential issue
3. Suggested revision
4. Applicable style-guide rule
5. Reason for the suggestion

Separate definite style-guide violations from optional editorial improvements. Flag uncertain issues instead of guessing.

**Draft:**

[Paste the documentation draft.]

**Style Guide:**

[Paste the relevant approved style-guide rules.]

## 4. Prompt: Content gap analysis

**Use when:** Reviewing a guide from the perspective of a first-time user.

**Prompt:**

You are reviewing technical documentation from the perspective of a reader who has never completed this workflow.

Identify potential missing information, including:

- Prerequisites
- Required permissions
- Required software or configuration
- Ordered steps
- Decision points
- Expected results
- Troubleshooting guidance
- Recovery instructions
- Relevant links and next steps

Do not create missing technical instructions.

For each potential gap, return:

1. The section or step affected
2. The missing information
3. Why the reader may need it
4. The source or subject matter expert needed to confirm it

Distinguish between confirmed omissions and questions that require more information.

**Document:**

[Paste the draft.]

## 5. Prompt: Technical consistency review

**Use when:** Comparing documentation against an approved specification or verified product information.

**Prompt:**

You are assisting with a technical documentation consistency review.

Compare the supplied draft only against the approved source material.

Check:

- Product names and terminology
- Commands and command-line flags
- Configuration keys and accepted values
- API parameters and response examples
- Defaults and prerequisites
- Permissions and security requirements
- Compatibility and version statements
- Expected results and product behavior

Do not infer missing behavior, invent values, or resolve conflicting information by guessing.

Return a table containing:

1. Statement in the documentation
2. Relevant source evidence
3. Potential discrepancy
4. Recommended next action
5. Whether subject matter expert confirmation is required

If the source material does not support a statement, flag it for verification.

**Draft:**

[Paste the documentation.]

**Approved source:**

[Paste the approved specification, test results, or SME notes.]

## 6. Prompt: Plain-language and usability review

**Use when:** A document is technically correct but may be difficult for its intended audience.

**Prompt:**

Review this technical documentation for readability and usability.

The intended audience is:

[Describe the reader's experience and technical background.]

Identify:

- Unexplained technical terms
- Long or complicated sentences
- Missing context
- Instructions that combine too many actions
- Ambiguous references such as "this" or "it"
- Steps with unclear expected results
- Places where an example would improve understanding

Do not remove necessary technical detail.

For each recommendation, provide the original wording, the issue, a possible revision, and why the revision helps the intended reader.

Do not change product behavior or technical meaning.

**Draft:**

[Paste the documentation.]

## 7. Prompt: Release-note review

**Use when:** Preparing customer-facing release notes.

**Prompt:**

You are an editorial assistant reviewing draft release notes.

Use only the approved release information provided.

For each item, check whether the content explains:

- What changed
- Who is affected
- The user or developer impact
- Any required customer action
- Availability or version information, when confirmed
- Relevant documentation links

Do not invent release dates, availability, compatibility, or product behavior.

Return a table containing:

1. Release item
2. Missing or unclear information
3. Suggested editorial improvement
4. Questions requiring Product or Engineering confirmation

Keep the language concise and customer-focused.

**Approved release information:**

[Paste approved release details.]

**Draft release notes:**

[Paste the draft.]

## 8. Evaluate AI suggestions

A long list of AI findings does not automatically mean the review was successful.

Evaluate each recommendation.

| Evaluation question | What to look for |
|---|---|
| Is it accurate? | Does the source support the finding? |
| Is it relevant? | Does it matter to the intended reader? |
| Does it preserve meaning? | Does the revision change technical intent? |
| Does it follow the Style Guide? | Is the suggested change consistent with approved rules? |
| Is it actionable? | Can a writer understand what needs to change? |
| Is it appropriately cautious? | Does it flag uncertainty rather than guessing? |

### Recognize false positives

A false positive occurs when AI reports a problem that is not actually a problem.

Examples:

- Flagging an approved product name as a spelling error.
- Recommending a change to a required API parameter.
- Treating a necessary technical term as unnecessary jargon.
- Suggesting a rewrite that changes the meaning of a command.

### Recognize missed issues

A missed issue occurs when AI fails to identify a real problem.

Examples:

- Missing an incorrect command-line flag.
- Failing to notice a missing prerequisite.
- Overlooking a broken cross-reference.
- Accepting an unsupported compatibility statement.

Both types of errors matter when evaluating an AI-assisted review process.

## 9. Build a repeatable evaluation test

To evaluate an AI tool or prompt, prepare a small set of sample documents.

Include known examples of:

- Incorrect terminology
- Inconsistent capitalization
- Missing prerequisites
- Unclear instructions
- Unsupported technical claims
- Incorrect links
- Valid technical terms that should not be changed

Run the same review more than once when appropriate.

Record:

| Test area | Result to record |
|---|---|
| Known issues detected | Which intentional issues were found? |
| False positives | Which suggestions were incorrect? |
| Missed issues | Which intentional problems were overlooked? |
| Unsupported claims | Did AI invent or infer information? |
| Consistency | Were similar issues handled consistently? |
| Usefulness | Did the output help the writer make a decision? |

Use the results to improve the prompt, the source material, or the review process.

Do not evaluate a tool only by how many suggestions it produces.

## 10. Improve prompts when results are poor

### Problem: AI rewrites technical terminology

**Possible improvement:** Tell the tool to preserve approved product names, commands, configuration keys, API terminology, and code.

### Problem: AI invents missing instructions

**Possible improvement:** Explicitly instruct it to identify missing information without creating technical steps.

### Problem: AI returns vague feedback

**Possible improvement:** Request the original wording, specific issue, suggested revision, and explanation.

### Problem: AI flags too many harmless differences

**Possible improvement:** Supply the relevant style-guide rules and ask it to distinguish required corrections from optional improvements.

### Problem: AI misses important content gaps

**Possible improvement:** Define the intended reader, their prerequisites, and the expected outcome of the workflow.

## 11. Keep the human review process intact

AI-assisted content follows the same approval process as other documentation.

| Responsibility | Owner |
|---|---|
| Provide the draft and source information | Technical Writer |
| Identify possible editorial issues | AI review assistant |
| Evaluate recommendations | Technical Writer |
| Verify product behavior | Engineering or appropriate SME |
| Confirm product intent | Product team, when needed |
| Approve editorial content | Designated human reviewer |
| Approve and publish the change | Authorized team members |

AI must not independently approve or publish documentation.

## 12. Protect information

Before using an AI tool:

- Confirm that the tool is approved for the information being processed.
- Follow organizational data-handling policies.
- Do not submit credentials, passwords, private keys, confidential customer data, or restricted company information to an unapproved service.
- Use fictional or approved sample material for training and demonstrations.
- Provide only the source material necessary for the task.

See the [Huddlehouse AI Usage Guidelines](article.html?doc=huddle-ai-guidelines) for the broader responsible-use requirements.

## 13. Final AI review checklist

- [ ] The AI tool is approved for the information being used.
- [ ] The task and intended audience are clear.
- [ ] The correct Style Guide is supplied or referenced.
- [ ] Approved technical source material is available.
- [ ] The prompt includes clear constraints.
- [ ] AI suggestions are evaluated individually.
- [ ] False positives and missed issues are considered.
- [ ] Unsupported claims are rejected.
- [ ] Required SMEs verify technical details.
- [ ] A human approves the final content.
- [ ] Normal editorial, source-control, and publication processes are complete.

## The Huddlehouse rule

AI can help us inspect, compare, evaluate, and improve documentation.

People remain responsible for accuracy, judgment, security, and approval.

> **Nova:** Let AI help us find the questions.
>
> **Pip:** Let the team verify the answers!
