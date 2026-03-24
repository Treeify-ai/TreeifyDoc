---
title: 6. 合作伙伴（Partnership）
---

> **产品名称**：Treeify  
> **版本**：0.2-beta  
> **日期**：2025.07.10  
>

## 🔄 将 Treeify 生成的测试用例导出到 TestCaseLab

### 🧠 如何在 TestCaseLab 场景中使用 Treeify 进行 AI 测试用例生成

如果你希望用 AI 快速生成测试用例，并直接同步到你的 TestCaseLab 项目中，**Treeify** 可以让整个流程变得简单且高效。借助 Treeify 的 AI 辅助测试设计流程，你可以在几分钟内生成测试场景；同时通过原生集成能力，只需几次点击即可将结构化测试用例导出到 TestCaseLab 的工作区。

本指南将带你完成 Treeify 与 TestCaseLab 的连接配置，并快速开始导出测试用例。

---

### ✅ 你需要准备什么

要将 [Treeify](https://treeifyai.com) 生成的测试用例导出到 [TestCaseLab](https://testcaselab.com)，你需要从 TestCaseLab 账号中准备以下信息：

- **API Token**
- **Company ID（公司 ID）**

这些信息用于安全地将 Treeify 连接到你的 TestCaseLab 工作区。

---

### Step 1：获取 API Token

在 TestCaseLab 中生成 API Token 需要具备 **Company Admin（公司管理员）** 权限。

1. 登录 TestCaseLab  
2. 进入 **Company Settings > Company Profile**  
3. 下滑找到 **API Tokens**  
4. 创建并复制一个新的 API Token  

> 只有 Company Admin 才能创建与查看 API Token。

---

### Step 2：获取 Company ID 与 Project ID

你可以使用 **Postman**（或其他 API 调试工具）通过 API Token 获取这些信息。

#### 获取 Company ID

- 发送 `GET` 请求到：
https://app.testcaselab.com/api/v2/companies

- 在请求 Header 中设置：
Authorization: Bearer YOUR_API_TOKEN

#### 响应示例

```json
[
  {
    "id": 123,
    "name": "你的公司名称",
    "subdomain": "yourcompany"
  }
]
```

复制其中的 id 字段 —— 这就是你的 Company ID。

>注：本文档后续步骤中会提到 Project ID，但当前 Treeify 导出流程通常会在界面中让你选择目标项目；如你的集成流程需要 Project ID，可按你们内部方式继续通过 TestCaseLab API 获取。

### Step 3：在 Treeify 中连接 TestCaseLab

当你拿到 API Token 与 Company ID 后，就可以开始使用集成能力：
- 登录你的 Treeify 账号（说明：当前仅支持个人账号）
- 按流程完成测试用例生成
- 生成完成后，进入 导出到 TestCaseLab（Export） 区域

填写并选择目标项目后导出：
- API Token
- Company ID
- 校验凭证信息
- 点击 Export to TestCaseLab，测试用例将会立即同步到 TestCaseLab

## 你可能会关心

- Treeify 目前处于开放体验阶段，是一个非常适合 QA 团队进行试用与验证的窗口期。
- 如需文件方式，你仍然可以将测试用例导出为 Excel 或 JSON。
- 如需协助，我们支持 1-对-1 上手引导；也欢迎加入 微信【TreeifyAI】 社区一起交流。

---

## 软件测试全生命周期的战略合作招募

在 Treeify，我们专注于 AI 驱动的 测试用例设计（Test Case Design），并已与 TestCaseLab 完成集成，覆盖结构化的 测试管理（Test Management）。两者结合，打通了测试生命周期中两个最关键的阶段。

但我们不会止步于此。

我们正在积极寻找测试生命周期其他关键环节的合作伙伴，共同构建一个“互联、智能、可扩展”的 QA 生态。

---

## 📌 按测试阶段的合作方向
| 生命周期阶段 | 期待合作的伙伴类型 |
| 需求管理	| 需求平台、ALM 工具、文档系统（如 Jama、Aha!、Confluence 等）
| 测试用例设计 |	已由 Treeify 覆盖 |
| 测试管理	| 已与 TestCaseLab 集成 |
| 测试实现	| 自动化框架、脚本生成工具（如 Playwright、Selenium、Cypress 等） |
| 测试执行	| CI/CD 与执行平台（如 Jenkins、GitHub Actions、LambdaTest、BrowserStack 等） |
| 测试报告与分析	| 报告与看板、缺陷跟踪、集成生态（如 Allure、ReportPortal、Jira 相关集成等） |

---

## 一起共建

我们希望与以下类型的伙伴展开合作：
- 开发者工具厂商
- QA SaaS 创业团队
- 自动化测试框架与生态
- DevOps 与可观测性平台
- 正在构建 AI 友好 QA Pipeline 的团队

无论你是垂直领域产品，还是正在扩展的平台型能力，我们都愿意探索：
- 双向 API 的无缝集成
- 典型场景共创与联合方案
- 联合市场活动与共增长曝光

---

##  联系方式
如果你正在上述任一方向构建产品，并希望一起推动测试智能化的未来，欢迎联系：
- 📧 contact@treeifyai.com
- 🫧 微信【TreeifyAI】

让软件质量的关键环节真正连起来 —— 我们一起把点连成线。

![微信联系](./getting-started-image/wechat.png)
