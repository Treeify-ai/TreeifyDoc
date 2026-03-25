---
title: 4.1 Treeify 的 Credits 计费机制说明
---

Treeify 采用基于 Credits 的计费方式，为 AI 测试设计能力提供“消耗型”资源支持。每一次生成都会根据任务复杂度消耗一定 Credits。

---

## 哪些操作会消耗 Credits？
当你执行以下操作时，会消耗 Credits：

- **需求分析（Requirement Analysis）**
- **测试对象生成（Test Objects）**
- **测试场景生成（Test Scenarios）**
- **重新生成任意步骤（Re-generate）**
- **AI对话（AI Chat）**

以上每个操作都会触发 Treeify 的多 Agent 推理流程。输入越复杂、细节越多，可能消耗的 Credits 也会更多。

---

## 什么因素会影响 Credits 消耗？
Credits 消耗是动态计算的，通常受以下因素影响：

- 需求内容的**长度**与**细节丰富度**
- 覆盖的测试维度数量（如：功能 / 安全 / 性能等）
- 多 Agent 分析过程中 LLM 的 **Token 使用深度**

输入越完整 = AI 推理越充分 = 消耗的 Credits 越多。

---

## 注册即送免费 Credits
新用户注册账号后，将获得 **100 Credits 免费额度**，足够你完整体验 Treeify 的全流程能力。

---

## 内测用户专属：免费 Credits 支持计划
Treeify 目前处于 **内测** 阶段，我们会将免费提供更多 Credits **优先提供给愿意参与内测、并持续提供产品反馈的用户**，用于支持你完整体验 Treeify 的全流程能力。

- 通过参与内测，你可以获得一定的免费 Credits（额度视内测计划与反馈情况而定）
- 你的真实使用反馈会直接影响我们的产品优化优先级与路线图

**如果你希望加入内测并获得免费 Credits 支持，欢迎联系我们，微信【TreeifyAI】。**

![微信联系](../images/wechat.png)
