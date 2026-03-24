---
title: 4.3 Why Project Settings Matter
---

In Treeify, configuring your Project correctly has a direct impact on the **accuracy, coverage, and efficiency** of the AI-generated test cases.
It determines which domain knowledge Treeify should use, which testing dimensions it should focus on, and at what level of granularity it should generate your results, so the output better fits your business and your current testing stage.

---

## Industry

Treeify activates relevant domain knowledge and terminology based on the **industry** you select, helping it understand requirement meaning and business processes more accurately.

**Why it matters:**

- It helps AI build context that is closer to the real business. For example, "claim submission" in insurance is very different from "placing an order" in e-commerce.
- Industry-specific workflows and terminology reduce the risk of fabricated assumptions and make the generated output more realistic.

**Example:**

> In a **Healthcare** scenario, Treeify will proactively pay attention to compliance-related concerns such as **HIPAA**, including access control and audit trails.

---

## Testing Type

You can choose the testing directions that should receive the most attention in the current generation, such as:

- Functional
- Performance
- Security
- Compatibility
- API
- More types are being added continuously

**Why it matters:**

- It helps AI decide which test objects and test scenarios should be generated.
- It keeps the output centered on the right dimensions instead of becoming too generic or drifting off target.

**Example:**

> If you choose **Performance Testing**, Treeify will prioritize test objects and scenarios related to response time, concurrent users, throughput, and similar concerns.

---

## Testing Stage

You should specify the testing stage you are currently in, for example:

- Requirement validation
- Integration testing
- System-level verification
- Regression testing

**Why it matters:**

- Treeify adjusts the **granularity and scope** of testing based on the stage.
- It makes the output better fit your current QA goal, whether you are checking high-level process risk or running stability-focused regression coverage.

**Example:**

> In the **system testing** stage, Treeify tends to generate end-to-end business flows rather than unit-level or single-point checks.

---

## Generation Strategy

You can choose how broadly and deeply AI should explore coverage:

- **Strict**: Generate strictly from the input you provide. Accuracy is usually higher, but it may not fill in coverage points that are implied but not explicitly stated.
- **Complement**: Allow AI to make reasonable additions based on industry and domain patterns. Coverage is broader, but it consumes more Credits and may include some lower-priority test cases.

**Why it matters:**

- It affects generation depth, coverage breadth, and Credit usage.
- `Complement` is more exhaustive, but it usually requires more prioritization and review afterward.

---

## Tip

- When you already have **complete, clear, and executable requirement input**, choose **Strict** first for more stable and precise results.
- When you are still in an early exploration stage, the requirements are not detailed enough, or you want to quickly broaden coverage, choose **Complement** to fill in ideas and boundaries.
