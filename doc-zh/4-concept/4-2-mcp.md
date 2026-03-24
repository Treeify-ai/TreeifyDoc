---
title: 4.2 Treeify MCP 安装与配置
---

Treeify MCP 让你的 AI Coding IDE/Agent 直接“调用 Treeify 的测试设计能力”，把需求/代码上下文转成**可追溯、可 review、可导出**的测试设计产物（例如测试对象、测试场景、测试用例、覆盖检查建议等），并支持在自动化流程里复用（CI/PR review、Spec-Driven Development、生成后导入测试管理工具等）。

---

## Treeify MCP 能做什么

接入成功后，你可以在 IDE 里直接用自然语言让 Agent 调用 Treeify 工具来完成：

- **测试场景与用例生成**：从 PRD/用户故事/接口说明中抽取关键业务规则、边界与异常路径，围绕主流程/替代流程/异常流程、权限/状态/并发/兼容性等维度生成高覆盖测试场景与用例。
- **覆盖检查与缺口提示**：基于需求与已有用例对比，提示漏测点（边界值、异常分支、权限矩阵、状态迁移等）。
- **结构化输出**：便于你后续导出 CSV/Excel、或对接测试管理工具/流水线（具体能力取决于你们 MCP Server 暴露的工具集合）。

> 提示：不同 IDE 展示的 “tools list” 会不同；你可以在接入后先让 Agent “列出 Treeify MCP 提供的工具”，再按工具能力写更具体的提示词。

---

## 示例提示词（直接复制可用）

下面这些提示词不依赖具体工具名，适合在 Cursor / VS Code / Claude Code / Goose / Windsurf / Codex 等环境里直接使用：

### A. 从需求生成测试用例（功能测试）
```text
请使用 Treeify MCP 工具，基于当前打开的需求描述生成测试用例。  
需要包含功能性测试、性能测试。
```

### B. 输出到文件（适合 Cursor/VS Code/CLI）
```text
使用 Treeify MCP 生成用例后，请把结果保存为 `./treeify/testcases.csv`（或 `./treeify/testcases.xlsx`）。  
```

---

## MCP 配置说明（手动配置）

### 1. 通用配置说明
Treeify MCP 使用 远程 SSE（Streamable HTTP） 的方式提供服务，你只需要在各个 IDE 的 MCP 配置中加入如下配置即可：
```json
{
  "mcpServers": {
    "treeify-ai": {
      "type": "streamableHttp",
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```
- treeify-ai：建议保留这个名称，后面在各 IDE 里会看到同名工具。
- YOUR_API_TOKEN：替换成你们给用户发放的真实 Token。
- 如果 IDE 报错不支持 streamableHttp，可以尝试改成：
    - "type": "sse"

### 2) Cursor

**步骤**
1. 打开 Cursor → Settings → Tools & Integrations → MCP Tools
2. 选择“编辑 MCP 配置”（或直接打开 ~/.cursor/mcp.json）
3. 粘贴并保存配置
```
{
  "mcpServers": {
    "treeify-ai": {
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_TREEIFY_TOKEN"
      }
    }
  }
}
```
4. 重启 Cursor
5. 回到 “编辑 MCP 配置”，看是否出现Tools并且mcp图标为“绿色”
![cursor_mcp](./mcp/cursor_4.png)

>如果 Cursor 对 /sse 要求显式类型为 sse，把 type 改成 sse 再试（不同版本实现可能有差异）。

### 2) Kiro
**配置文件位置（两种）**
1. Workspace：.kiro/settings/mcp.json
2. User：~/.kiro/settings/mcp.json（全局生效）

**步骤**
1. 打开 Command Palette（Cmd/Ctrl + Shift + P）
2. 搜索并打开 MCP config（User 或 Workspace）
3. 粘贴配置并保存
4. 回到对话/Agent，确认工具可用

**配置示例：**
```
{
  "mcpServers": {
    "treeify-ai": {
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_TREEIFY_TOKEN"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### 3) Claude Code

**命令行快速添加（推荐）**
```bash
claude mcp add --transport sse treeify-ai https://treeifyai.com/op/mcp/sse \
  --header "Authorization: Bearer YOUR_TREEIFY_TOKEN"
```

### 4) VS Code（Copilot Chat / Agent）

**步骤**

1. 在项目根目录创建：.vscode/mcp.json
2. 粘贴配置
3. 打开 VS Code Chat（Copilot Chat/Agent）
4. 在工具选择器里启用 Treeify server（或重启 VS Code）

**配置示例：**
```
{
  "servers": {
    "treeify": {
      "type": "sse",
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_TREEIFY_TOKEN"
      }
    }
  }
}
```

### 5) Codex（OpenAI Codex）

**示例（TOML，按 SSE）**
```toml
[mcp_servers.treeify]
transport = "sse"
url = "https://treeifyai.com/op/mcp/sse"

[mcp_servers.treeify.headers]
Authorization = "Bearer YOUR_TREEIFY_TOKEN"
```

#### 验证是否安装成功（通用）

接入成功的标准通常是：
- MCP Server 显示为 已启用 / connected
- Chat/Agent 模式里能看到来自 treeify 的 tools
- 你问一句：
    - “List the tools from Treeify MCP”
    - 或 “What tools do you have from treeify?”
    - 能返回工具清单（而不是 401/连接失败）

### 6) Trae
**配置步骤（Trae UI 手动添加）**
1. 在 IDE 模式界面中，点击界面右上角的 `设置` 图标，进入设置中心。
   或
   在 SOLO 模式界面中，点击对话面板右上角的 `设置` 图标，进入设置中心。
2. 在左侧导航栏中，选择 `MCP`，打开 `MCP` 窗口。
3. 在 MCP 窗口的右上角，点击 `添加 > 手动添加`。若你是首次添加 MCP Server，还可以直接点击窗口中部的 `手动添加` 按钮。
4. 界面上显示 `手动配置` 窗口。
5. 填入 MCP Server 的配置内容。
```json
{
  "mcpServers": {
    "operation-platform": {
      "type": "streamableHttp",
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```
- 保存配置，返回 Trae 的 chat对话框

### 7) CodeBuddy
**配置步骤**
1. 在侧栏对话面板右上方的中，点击 CodeBuddy Settings 按钮。
2. 切换到 MCP 标签页，点击右侧的 Add MCP 按钮。
3. 在 json 配置文件中，添加 MCP Server 配置内容：
```json
{
  "mcpServers": {
    "operation-platform": {
      "type": "streamableHttp",
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```

### 8) Qcoder
**配置步骤**
1. 在 Qoder IDE 的右上角，点击用户图标，或使用键盘快捷键（⌘ ⇧ ,（macOS）或 Ctrl Shift ,（Windows）），然后选择 Qoder 设置。
2. 在左侧导航窗格中，点击 MCP。
3. 在弹出的 JSON 文件中，添加你的服务配置信息：
```json
{
  "mcpServers": {
    "operation-platform": {
      "type": "streamableHttp",
      "url": "https://treeifyai.com/op/mcp/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```
4. 保存后，新服务会出现在你的列表中，链接图标表示连接成功。展开该条目可以查看可用工具。
