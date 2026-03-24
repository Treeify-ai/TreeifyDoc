---
title: 5.2 What `<Note: Related information is missing>` Means
---

When you see `<Note: Related information is missing>` in Treeify-generated test design results, it means the AI **could not find enough explicit information in the requirement materials you provided to support that part of the test logic**.

In most cases, that means the relevant content was either not described in the original requirement document at all, or was mentioned only partially or ambiguously, so it cannot reliably support downstream test design.

Treeify marks these information gaps explicitly instead of filling them in with vague assumptions or subjective guesses. The goal is to help you spot uncertainty in the requirements earlier while keeping control over test design quality.

---

## Why this "missing information" note appears

Treeify analyzes system behavior and generates structured test design based on the PRD, user stories, specifications, flowcharts, and other materials you provide.

Treeify may mark `<Note: Related information is missing>` when situations like the following occur:

- Key preconditions are not specified
- Differences in roles or permissions are not clearly described
- The expected result after an action is not defined
- Boundary conditions, exception branches, or failure handling are missing
- A decision rule is ambiguous and cannot be interpreted reliably
- Different input materials conflict with each other and there is no clear source of truth

In other words, this note does not mean Treeify cannot do the work. It means: **under the current input conditions, this part should not be treated as a clearly defined requirement.**

---

## Why Treeify marks information gaps explicitly

In many AI tools, when requirements are incomplete, the model tends to fill in missing pieces based on common sense, habits, or context. On the surface, that can make the output look more complete, but it also introduces clear risks:

- The output may look reasonable, but it may not come from the actual requirement
- Test coverage may be built on incorrect assumptions
- During review, it becomes hard to tell what was explicitly required versus what the AI inferred
- Requirement logic and test logic may later turn out to be inconsistent during execution

Treeify takes the opposite approach:

> If the requirement does not state something clearly, Treeify does not assume it. It marks the gap.

The value of that approach is that it:

- Preserves traceability in test design results
- Reduces the risk of AI hallucination
- Helps teams spot gaps in requirement expression early
- Keeps test design grounded in more reliable evidence

So `<Note: Related information is missing>` is not an error message. It is a **requirement testability reminder**.

---

## Where this usually appears

`<Note: Related information is missing>` usually appears in places like these:

| Where it appears | Possible reason |
|---------|------|
| Preconditions | The document does not clearly describe environment requirements, data setup, or dependencies |
| Roles and permissions | The input does not clearly define access scope or operational differences across roles |
| Expected results | The requirement does not explain how the system should respond after success or failure |
| Boundary conditions | The document is missing thresholds, upper and lower limits, or special-input handling logic |
| Exception flows | Error handling, retry logic, fallback strategy, or alternate paths are not described |
| State changes | The requirement does not explain how an object's state should change after an action |

These are often the parts of test design most likely to cause problems, so marking them explicitly actually helps later supplementation and calibration.

---

## What to do when you see "missing information"

When you see this note, do not just ignore it as ordinary text. First ask whether this information should already be explicit at the current stage.

In most cases, you can handle it in one of the following ways.

### Option 1: Fill in the missing information

If the missing information directly affects test logic, coverage, or result evaluation, the best option is usually to add it.

For example, you can further clarify:

- Whether the action has preconditions
- Whether different roles should be handled differently
- What the system state should be after success
- What feedback the user should see after failure
- Whether there are boundary values, exception paths, or fallback strategies

After the missing information is added, you can include the updated content in your requirement materials and ask Treeify to analyze and generate results again from the fuller input.

This is usually the recommended approach because it directly improves the accuracy and executability of later test design.

### Option 2: Keep the gap as a review item

If the information really cannot be confirmed yet, or if it needs to be decided later during review, you can keep the note for now.

In that case, it is best to treat it as an open question rather than silently accepting an AI guess. That helps you avoid locking in test logic too early when the information is still incomplete.

---

## How to tell whether a gap must be filled in

Not every gap needs to be resolved immediately, but you should usually prioritize it when it:

- Directly affects whether the test can be executed
- Affects how expected results are judged
- Causes clear differences across roles or paths
- Affects exception handling or boundary coverage
- Is likely to create disagreement during review, development, or integration

If the gap only involves weak supporting information and does not affect the core testing logic, it can be left open temporarily. But if it already affects "how to test" or "what counts as passing," it usually needs clarification as soon as possible.

---

## Example

Treeify might generate something like this:

```json
{
  "step": "The user clicks Submit on the checkout page",
  "expected_result": "<Note: Related information is missing>"
}
```

This means that, in the current input materials, Treeify could not find explicit information describing what should happen after the user clicks Submit.

If you later add a requirement such as:

> After submission succeeds, the page should display a confirmation page containing the order details.

Then after reanalysis, Treeify can generate a fuller and more verifiable test design result based on that explicit requirement.

---

## The real value of this note

From a product perspective, the value of `<Note: Related information is missing>` is not merely that it "points out a problem." Its real value is that it helps you identify the missing pieces in a requirement that are most likely to affect test quality.

It can help you:

- Identify more quickly which parts of the logic are still undefined
- Distinguish real requirements from AI inference
- Pull requirement review earlier into the test design stage
- Improve the clarity and testability of your input materials
- Make test design results more trustworthy and actionable

So instead of seeing it as an obstacle, it is better to see it as an extra capability Treeify provides:
it not only helps generate test design, it also helps uncover what the requirement still has not made clear.

---

## Summary

- `<Note: Related information is missing>` means Treeify could not find sufficiently explicit supporting information in the current input materials
- Treeify marks these gaps proactively instead of replacing real requirements with subjective assumptions
- This reduces hallucination risk and improves traceability and trustworthiness in test design
- When the gap affects test logic, it should be filled as soon as possible; if it cannot be confirmed yet, it should be kept as a review item

The clearer the requirement, the more stable the test design.
Treeify marks "missing information" not to interrupt the process, but to help you see key issues clearly before test design moves too far forward.
