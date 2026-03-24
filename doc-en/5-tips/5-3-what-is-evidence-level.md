---
title: Concept: How to Understand `evidence_level`
---

In some Treeify-generated results, you will see a field called `evidence_level`.

This field indicates **how strongly the current item is grounded in the original requirement input**.

It is not a quality score, and it is not a priority label. It is there to help you judge whether a piece of content comes directly from the requirement, is logically derived from it, or was added based on common test design patterns.

The currently supported values are:

- `explicit`
- `implied`
- `inferred_type`
- `domain_common`

---

## Why Treeify provides `evidence_level`

In test design, not every item comes from the same kind of evidence.

Some things are stated very clearly in the requirement. Some are not written word for word, but can still be reasonably derived from the surrounding context. Others are added to make the test design more complete, based on the requirement type or general domain knowledge.

Without distinguishing those sources, users often run into two problems:

- They cannot tell which items are explicitly required
- They cannot tell which items still need confirmation or review

That is why Treeify uses `evidence_level` to show where each item comes from, giving you a stronger basis for review and decision-making.

---

## What the four `evidence_level` values mean

## `explicit`

This means the content is **explicitly stated in the requirement input**, or can be directly located in the original wording.

This is usually the most direct and stable form of requirement evidence.

For example, if the requirement says:

> Lock the account after five consecutive failed login attempts.

Then test design content related to locking the account after five failures can be marked as `explicit`.

You can think of `explicit` as meaning:

- There is direct textual evidence
- It can be traced directly to the input
- It should usually be treated as stable requirement content first

---

## `implied`

This means the content **is not written word for word, but can be reasonably derived from the existing requirement context**.

It is still grounded in the input, but it is not a direct sentence copied from the source. It is a natural extension of the existing logic.

For example, if the requirement says:

> After a successful submission, the user is redirected to the order confirmation page.

The requirement may not explicitly say that "a failed submission should show failure feedback," but if the surrounding context makes it clear the system must handle failure branches, some related testing concerns may be marked as `implied`.

You can think of `implied` as meaning:

- It is not directly stated in the original wording
- But it has a strong logical connection to the existing requirement
- It is usually worth reviewing, though it may still need human confirmation

---

## `inferred_type`

This means the content **does not come from a specific sentence, but is inferred from the type of requirement, the task goal, or structural characteristics of the input**.

This usually appears when the requirement itself does not fully expand all testing concerns, but the type of requirement strongly suggests what should typically be covered.

For example, if a requirement clearly belongs to API input validation, but does not list every field-level validation rule, Treeify may infer some testing concerns from the fact that this is an API contract-style requirement and mark them as `inferred_type`.

You can think of `inferred_type` as meaning:

- It comes from identifying the kind of requirement this is
- It is more about structured inference than direct textual evidence
- It is useful for completing the test design, but it should usually be reviewed before adoption

---

## `domain_common`

This means the content **comes from common testing concerns or business conventions in the domain**, rather than from something explicitly written in the current requirement.

Its purpose is usually not to claim that "the requirement definitely says this." Instead, it highlights testing points that are often worth considering or confirming in this kind of domain.

For example, in areas such as payments, permissions, security, and compliance, Treeify may mark input validation, permission isolation, exception handling, and audit logging as `domain_common`, even when they are not fully spelled out in the requirement.

You can think of `domain_common` as meaning:

- It leans more on domain convention or general testing experience
- It does not mean the requirement has already confirmed it
- It works best as a supplement, review prompt, or item to confirm

---

## How to use these four labels in practice

You do not need to treat `evidence_level` as a right-or-wrong judgment. It is better understood as a description of **where the evidence comes from**.

A practical way to read it is:

- `explicit`: clearly stated in the requirement, so it is easier to trust and trace
- `implied`: reasonably derived from the requirement context, so it should be reviewed against that context
- `inferred_type`: inferred from the requirement type, so it should receive focused review
- `domain_common`: based on common domain practice, so it should be treated as a useful prompt rather than a confirmed fact

In other words, a later value in the list does not mean the content is "worse." It means the content requires more judgment from you based on the project background, team standards, and actual requirement.

---

## Why Treeify does not output only `explicit`

If Treeify only output `explicit` content, the results would be more conservative, but they would also miss many of the things that matter in real test design.

That is because real requirement documents are often incomplete. Many important pieces of logic are not written in enough detail, especially boundary conditions, exception branches, role differences, and common domain risks. If AI never adds anything beyond what is explicitly stated, the output may be safe, but it often will not be useful enough.

That is why Treeify preserves traceability for explicit requirements while also using `implied`, `inferred_type`, and `domain_common` to show you:

- Which content is clearly stated by the requirement
- Which content is a natural extension of the surrounding context
- Which content was added to make the test design more complete

This is Treeify's way of balancing **reduced hallucination risk** with **practical usability**.

---

## Usage suggestions

When reviewing results that include `evidence_level`, it helps to use them like this:

1. Confirm `explicit` items first and make sure they match the original requirement.
2. Review `implied` items against the broader context to see whether they fit the real business logic.
3. Check whether `inferred_type` items match the testing goals typically associated with this kind of requirement.
4. Treat `domain_common` items as valuable prompts or additions, not as facts already confirmed by the requirement.

If your team has a high bar for traceability in test design, this field is especially useful. It helps you clearly separate **requirement-based evidence** from **design-level supplementation**, which improves review efficiency and lowers the risk of accepting something by mistake.

---

## Summary

`evidence_level` explains **the strength and source of the connection between a Treeify-generated item and the original requirement**.

It helps answer questions like:

- Was this explicitly stated in the requirement?
- Was it derived from the context?
- Was it added based on the requirement type?
- Was it suggested based on common domain experience?

With this field, Treeify aims to make test design results not only more complete, but also more transparent, traceable, and easier to review.
