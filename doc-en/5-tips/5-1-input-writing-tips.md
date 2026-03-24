---
title: 5.1 Tips for Writing Input That AI Can Understand Better
---

Treeify understands, analyzes, and structures test design based on the requirement materials you provide. The clearer your input is, the more stable AI's judgment will usually be when identifying requirement boundaries, business rules, and testing priorities. As a result, the generated output is more likely to be accurate, complete, and usable.

That is why, when entering requirements, it helps to use wording that is consistent, clear, and easy to break down. The suggestions below can help Treeify understand your requirements more accurately.

---

## Why input style affects result quality

When Treeify analyzes requirements, it does more than read the text itself. It also interprets hierarchy, logical boundaries, and semantic emphasis across the content. If the input is messy, heavily compressed, or mixes information together, AI is more likely to run into problems such as:

- Unclear requirement boundaries
- Missing key rules
- Different types of requirements getting mixed together
- Unstable test object decomposition
- Incomplete coverage in generated test scenarios

On the other hand, when the input is well structured and clearly expressed, Treeify is more likely to:

- Correctly identify document structure and hierarchy
- Distinguish functions, rules, constraints, and exception conditions more accurately
- Complete requirement analysis and test decomposition more consistently
- Reduce misunderstanding, omissions, and unsupported expansions

You can think of it this way: **the clearer the input, the more reliable the foundation for the rest of the test design process.**

---

## Organize content with clear section headings

Use explicit section headings to organize requirement content, such as grouping by functional module, requirement type, or business topic. This helps Treeify identify the boundary between different blocks of content more accurately and reduces cross-section confusion.

For example, you can organize content by categories such as "Functional Requirements," "Performance Requirements," and "Security Requirements," or by specific modules such as "Login," "Orders," or "Access Control."

Example:

```md
## 1. Functional Requirements
### 1.1 Login Module
1. Users can log in with email and password.
2. Users can reset their password through email.
3. The system must support two-factor authentication.

## 2. Security Requirements
### 2.1 Access Control
1. Only administrators can delete users.
2. Regular users must not be able to view other users' sensitive information.
```

When requirement materials are long, clear headings become especially important. They help Treeify preserve more stable context boundaries during analysis instead of treating the whole document as one continuous block of text.

---

## Highlight key information clearly

For critical information such as roles, constraints, trigger conditions, important fields, state changes, and exception handling, it helps to use bolding or other light emphasis. This makes it easier for Treeify to identify what truly deserves focus in the test design.

For example:

- When the password is entered incorrectly, the system should display an error message.
- Only administrators can delete records.
- If inventory is insufficient, the system must not allow the order to be submitted.

This is not about formatting for appearance. It is about helping AI capture important rules and constraints more reliably in long text.

---

## Use numbered lists or bullets for rules and constraints

For business rules, validation logic, input restrictions, and process constraints, it is usually better to list them item by item with numbers or bullets instead of compressing multiple rules into a single paragraph.

That helps Treeify understand each point more consistently and reduces the chance of different rules being blended together.

Example:

```markdown
1. The form must validate the following:
   - Required fields
   - Email format
   - Password length
2. After a successful submission, the system should show a success message.
3. If submission fails, the system should preserve the user's entered data.
```

When there are many rules, list-based writing is usually better suited for downstream test design because it is easier to split into independent testing concerns.

---

## Group content by requirement type

To improve Treeify's ability to classify and decompose requirements, it is best to group different types of requirements instead of mixing them together.

Common groupings include:

- Functional requirements
- Performance requirements
- Security requirements
- Compatibility requirements
- API requirements
- Compliance requirements

This makes it easier for Treeify to understand the testing focus for each category. For example, functional requirements center on business behavior and outcomes, performance requirements center on response time and throughput, and security requirements center on permissions, data protection, and risk control.

When different types of requirements are mixed together, AI is more likely to drift in testing focus or classify content inconsistently.

---

## Keep terminology consistent and avoid vague wording

Within the same requirement material, try to keep terminology consistent. Do not refer to the same object by multiple names in different places, and do not switch between words like "submit" and "save" unless they truly mean different things in the business context.

It also helps to avoid vague expressions such as:

- `etc.`
- `similar cases`
- `when needed`
- `as appropriate`

These phrases tend to hide boundaries and make it harder for AI to judge what is actually required.

---

## Notes on multilingual input

Treeify supports multilingual requirement input, including Chinese, English, and other common languages.

In most cases, Treeify tries to keep its analysis and output aligned with the language style of your input. However, if one document mixes multiple languages or uses inconsistent terminology, the cost of understanding still goes up for AI.

So when possible, keep the main language consistent within the same requirement material, and make sure key terms stay consistent from beginning to end.

---

## How to write incomplete documents in a way AI can still understand

In real projects, requirement materials are not always complete. In those cases, you do not need to force every detail into place, but it helps to make at least the following points as clear as possible:

- What problem the current feature is meant to solve
- Who will use the feature
- What the core flow looks like
- What rules or constraints are already known
- Which parts are still uncertain

Even when the information is incomplete, Treeify can still understand the existing content more reliably and help you keep moving the test design forward, as long as the structure is clear and the boundaries are explicit.
