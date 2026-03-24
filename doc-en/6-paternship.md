---
title: 6. Partnership
---

> **Product**: Treeify
> **Version**: 0.2-beta
> **Date**: 2025.07.10

## Exporting Treeify Test Cases to TestCaseLab

### How to use Treeify for AI test case generation in a TestCaseLab workflow

If you want to generate test cases quickly with AI and sync them directly into your TestCaseLab project, **Treeify** makes the process simple and efficient. With Treeify's AI-assisted test design workflow, you can generate structured test scenarios within minutes. Through its native integration capabilities, you can then export those structured test cases into your TestCaseLab workspace in just a few clicks.

This guide walks you through connecting Treeify to TestCaseLab and getting started with exporting test cases.

---

### What you need to prepare

To export Treeify-generated test cases to [TestCaseLab](https://testcaselab.com), you need the following information from your TestCaseLab account:

- **API Token**
- **Company ID**

These are used to securely connect Treeify to your TestCaseLab workspace.

---

### Step 1: Get your API Token

To generate an API Token in TestCaseLab, you need **Company Admin** permission.

1. Log in to TestCaseLab.
2. Go to **Company Settings > Company Profile**.
3. Scroll down to **API Tokens**.
4. Create and copy a new API Token.

> Only Company Admins can create and view API Tokens.

---

### Step 2: Get your Company ID and Project ID

You can use **Postman** or any other API debugging tool to retrieve this information with your API Token.

#### Get the Company ID

- Send a `GET` request to:
  `https://app.testcaselab.com/api/v2/companies`
- Set this request header:
  `Authorization: Bearer YOUR_API_TOKEN`

#### Example response

```json
[
  {
    "id": 123,
    "name": "Your Company Name",
    "subdomain": "yourcompany"
  }
]
```

Copy the `id` field. That is your Company ID.

> Note: Later sections of this document mention Project ID, but in Treeify's current export flow, you usually choose the target project directly in the UI. If your integration process requires Project ID, you can retrieve it through the TestCaseLab API using your own internal method.

### Step 3: Connect TestCaseLab in Treeify

Once you have your API Token and Company ID, you can start using the integration:

- Log in to your Treeify account. At the moment, only personal accounts are supported.
- Complete your test case generation flow.
- After generation is complete, open the **Export to TestCaseLab** area.

Fill in the required credentials, select the target project, and export:

- API Token
- Company ID
- Validate the credentials
- Click **Export to TestCaseLab** and the test cases will sync to TestCaseLab immediately

## You may also care about

- Treeify is currently in an open trial phase, which makes this a good time for QA teams to evaluate it.
- If you prefer file-based delivery, you can still export test cases as Excel or JSON.
- If you need help, we offer one-on-one onboarding support. You are also welcome to join the WeChat community at `TreeifyAI`.

---

## Strategic partnership program across the software testing lifecycle

At Treeify, we focus on AI-driven **test case design**, and we have already integrated with TestCaseLab for structured **test management**. Together, these two parts cover two of the most critical stages in the testing lifecycle.

But we are not stopping there.

We are actively looking for partners across the rest of the testing lifecycle so we can build an interconnected, intelligent, and extensible QA ecosystem together.

---

## Partnership directions by testing stage

| Lifecycle Stage | Partner Types We Want to Work With |
|------|------|
| Requirements Management | Requirement platforms, ALM tools, and documentation systems such as Jama, Aha!, and Confluence |
| Test Case Design | Already covered by Treeify |
| Test Management | Already integrated with TestCaseLab |
| Test Implementation | Automation frameworks and script generation tools such as Playwright, Selenium, and Cypress |
| Test Execution | CI/CD and execution platforms such as Jenkins, GitHub Actions, LambdaTest, and BrowserStack |
| Reporting and Analysis | Reporting dashboards, defect tracking systems, and integration ecosystems such as Allure, ReportPortal, and Jira-related integrations |

---

## Build with us

We are looking to collaborate with partners such as:

- Developer tooling companies
- QA SaaS startups
- Automation testing frameworks and ecosystems
- DevOps and observability platforms
- Teams building AI-friendly QA pipelines

Whether you are a focused vertical product or a broader platform expanding your capabilities, we are open to exploring:

- Seamless two-way API integrations
- Co-created solutions for representative use cases
- Joint marketing activities and shared growth opportunities

---

## Contact

If you are building in any of the directions above and want to help shape the future of intelligent testing, feel free to reach out:

- `contact@treeifyai.com`
- WeChat: `TreeifyAI`

Let's connect the key stages of software quality in a meaningful way, together.
