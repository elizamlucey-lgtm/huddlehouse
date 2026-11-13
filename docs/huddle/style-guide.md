
# Huddlehouse Documentation Style Guide

Welcome to the Huddlehouse Style Guide!

This guide helps everyone create documentation that feels consistent, understandable, and useful.

Nova believes good documentation should help readers move forward without guessing. Pip checks the details to make sure our writing follows the same rules.

## 1. Our writing principles

Huddlehouse documentation should be:

- **Clear:** Explain what the reader needs to know.
- **Concise:** Remove unnecessary words.
- **Consistent:** Use the same terminology and formatting throughout.
- **Accurate:** Verify technical details before publication.
- **Task-focused:** Help readers complete their goals.
- **Friendly:** Sound helpful without becoming overly casual.

## 2. Voice and tone

Our voice is friendly, confident, and practical.

| Use | Avoid |
|---|---|
| Select Save to keep your changes. | You should probably click Save. |
| The request was not completed. | Oops! Something went wrong!!! |
| Check your connection settings. | Just mess around with your settings. |

Use a conversational tone, but do not sacrifice technical precision.

## 3. Write for the reader

Before writing, identify:

- Who will read this?
- What are they trying to accomplish?
- What do they already know?
- What information do they need before starting?
- What should happen when they finish?

Explain unfamiliar terms when readers may not know them.

Do not assume every reader has developer or administrator experience.

## 4. Headings and page structure

Use headings to help readers scan and navigate content.

- Use one H1 for the page title.
- Use H2 headings for major topics.
- Use H3 headings for supporting topics.
- Keep headings descriptive.
- Use sentence case for headings.

Good heading:

`Configure a workspace connection`

Less helpful heading:

`Configuration`

## 5. Procedures and numbered steps

Use numbered steps when readers must complete actions in a specific order.

Each step should describe an action.

Good example:

1. Open the workspace settings.
2. Select Connections.
3. Enter the connection details.
4. Select Save.

Avoid combining several unrelated actions into one long step.

Include the expected result when it helps readers confirm success.

## 6. Notes, warnings, and important information

Use consistent labels.

> **Note:** Additional information that helps readers understand a procedure.

> **Important:** Information that readers should understand before continuing.

> **Warning:** Information about a possible risk or unwanted result.

Do not use warnings for ordinary reminders.

## 7. Product terminology

Use approved product names and technical terms consistently.

| Term | Writing rule |
|---|---|
| Huddlehouse | Capitalize the product name |
| Huddle | Capitalize when referring to the product area |
| Projects | Capitalize when referring to the product area |
| workspace | Use lowercase in general references |
| API | Always uppercase |
| JSON | Always uppercase |
| YAML | Always uppercase |
| sign in | Use as a verb |
| sign-in | Use as an adjective or noun |

When Engineering confirms an official product term, use that term consistently.

Do not invent a new name for an existing setting or feature.

## 8. Buttons and interface labels

Use the exact text displayed in the product interface.

Example:

Select **Create project**.

Do not rewrite interface labels in a way that makes them difficult to recognize.

If an interface label changes, review affected documentation.

## 9. Code and command examples

Use code formatting for:

- Commands
- File names
- Configuration values
- API paths
- Code samples
- Parameter names

Example:

```bash
huddlehouse workspace list
```

Explain what the command does and identify any prerequisites.

Never invent command options or technical behavior.

## 10. Links and cross-references

Use descriptive link text.

Good:

[Read the authentication guide](../developer/authentication.md)

Avoid:

[Click here](../developer/authentication.md)

Check that links point to the correct destination before publication.

## 11. Tables and lists

Use tables when readers need to compare related information.

Use lists when readers need to scan several items.

Keep table headings descriptive and avoid overcrowded tables.

## 12. Editorial review checklist

Before submitting a document, check the following:

- [ ] The content addresses a clear reader goal.
- [ ] The title describes the subject.
- [ ] Headings follow the correct hierarchy.
- [ ] Terminology matches approved product language.
- [ ] Interface labels match the product.
- [ ] Procedures use the correct order.
- [ ] Commands and examples have been verified.
- [ ] Notes and warnings are used appropriately.
- [ ] Links work and use descriptive text.
- [ ] The content follows the Huddlehouse voice and tone.
- [ ] Technical details have an identified verification source.

## 13. Before-and-after example

**Before:**

> You will want to go ahead and click on the button to save everything that you just entered.

**After:**

> Select **Save** to keep your changes.

Why is the second version better?

- It is shorter.
- It uses the exact interface label.
- It tells the reader what happens next.
- It avoids unnecessary wording.

## 14. Using AI with the Style Guide

AI tools may help identify possible writing issues.

They can suggest:

- Clearer wording
- Consistent terminology
- Improved headings
- Missing prerequisites
- Repeated information
- Potentially confusing instructions

However, AI suggestions must be reviewed by a human writer.

The Style Guide is the standard. AI is an assistant, not the final decision-maker.

> Pip's final check: A suggestion is not automatically an improvement. Always check whether it is accurate, useful, and appropriate for the reader.
