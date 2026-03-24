---
title: 4.2 Installing and Configuring Treeify MCP
---

Treeify MCP lets your AI coding IDE or agent directly **invoke Treeify's test design capabilities**. It turns requirement and code context into test design artifacts that are **traceable, reviewable, and exportable**, such as test objects, test scenarios, test cases, and coverage review suggestions. It can also be reused in automated workflows, including CI, PR review, spec-driven development, or exporting generated results into test management tools.

---

## What Treeify MCP can do

Once connected, you can ask your agent in the IDE to use Treeify tools through natural language to complete tasks such as:

- **Generate test scenarios and test cases**: Extract key business rules, edge cases, and exception paths from PRDs, user stories, or API specifications, then generate high-coverage test scenarios and cases across dimensions such as main flows, alternate flows, exception flows, permissions, states, concurrency, and compatibility.
- **Check coverage and identify gaps**: Compare requirements against existing test cases and flag missing coverage, such as boundary values, exception branches, permission matrices, and state transitions.
- **Produce structured output**: Make it easier to export to CSV or Excel later, or connect to test management tools and pipelines, depending on the tool set exposed by your MCP server.

> Tip: Different IDEs present the available tool list differently. After connecting, it is often helpful to first ask the agent to "list the tools provided by Treeify MCP," then write more specific prompts based on what is available.

---

## Example prompts you can copy directly

The prompts below do not depend on specific tool names, so they work well in environments such as Cursor, VS Code, Claude Code, Goose, Windsurf, and Codex.

### A. Generate test cases from a requirement

```text
Please use the Treeify MCP tools to generate test cases from the requirement currently open in the editor.
Include both functional testing and performance testing.
```

### B. Save output to a file

```text
After generating the test cases with Treeify MCP, please save the result to `./treeify/testcases.csv` (or `./treeify/testcases.xlsx`).
```

---

## MCP configuration guide

### 1. General configuration

Treeify MCP is provided through remote SSE (Streamable HTTP). You only need to add the following configuration to your IDE's MCP settings:

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

- `treeify-ai`: We recommend keeping this name. You will see the same tool name in supported IDEs.
- `YOUR_API_TOKEN`: Replace this with the real token issued to the user.
- If your IDE reports that `streamableHttp` is unsupported, try changing:
  - `"type": "sse"`

### 2. Cursor

**Steps**

1. Open Cursor, then go to `Settings -> Tools & Integrations -> MCP Tools`.
2. Choose "Edit MCP Config" or open `~/.cursor/mcp.json` directly.
3. Paste and save the configuration:

```json
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

4. Restart Cursor.
5. Go back to the MCP configuration page and check whether the tools appear and whether the MCP icon is green.

> If Cursor requires an explicit `sse` type for the `/sse` endpoint, change `type` to `sse` and try again. Behavior may vary by version.

### 3. Kiro

**Config file locations**

1. Workspace-level: `.kiro/settings/mcp.json`
2. User-level: `~/.kiro/settings/mcp.json` for global effect

**Steps**

1. Open the Command Palette with `Cmd/Ctrl + Shift + P`.
2. Search for and open the MCP config, either User or Workspace.
3. Paste the configuration and save.
4. Return to the chat or agent view and confirm that the tools are available.

**Example configuration**

```json
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

### 4. Claude Code

**Quick CLI setup (recommended)**

```bash
claude mcp add --transport sse treeify-ai https://treeifyai.com/op/mcp/sse \
  --header "Authorization: Bearer YOUR_TREEIFY_TOKEN"
```

### 5. VS Code (Copilot Chat / Agent)

**Steps**

1. Create `.vscode/mcp.json` in your project root.
2. Paste the configuration.
3. Open VS Code Chat, such as Copilot Chat or Agent.
4. Enable the Treeify server in the tool selector, or restart VS Code.

**Example configuration**

```json
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

### 6. Codex (OpenAI Codex)

**Example (TOML, using SSE)**

```toml
[mcp_servers.treeify]
transport = "sse"
url = "https://treeifyai.com/op/mcp/sse"

[mcp_servers.treeify.headers]
Authorization = "Bearer YOUR_TREEIFY_TOKEN"
```

#### How to verify the installation

Typical signs of a successful connection include:

- The MCP server shows as enabled or connected.
- You can see Treeify tools in chat or agent mode.
- If you ask:
  - `List the tools from Treeify MCP`
  - or `What tools do you have from Treeify?`
  the agent returns a tool list instead of a `401` or connection error.

### 7. Trae

**Manual setup steps in the Trae UI**

1. In IDE mode, click the `Settings` icon in the upper-right corner to open the settings center.
   Or, in SOLO mode, click the `Settings` icon in the upper-right corner of the chat panel.
2. In the left navigation bar, choose `MCP` to open the MCP window.
3. In the upper-right corner of the MCP window, click `Add -> Manual Add`. If this is your first MCP server, you can also click the `Manual Add` button in the middle of the window.
4. The `Manual Configuration` window appears.
5. Fill in the MCP server configuration:

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

- Save the configuration and return to the Trae chat view.

### 8. CodeBuddy

**Setup steps**

1. In the upper-right corner of the sidebar chat panel, click the CodeBuddy Settings button.
2. Switch to the MCP tab and click the Add MCP button on the right.
3. Add the MCP server configuration to the JSON config file:

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

### 9. Qoder

**Setup steps**

1. In the upper-right corner of the Qoder IDE, click the user icon, or use the keyboard shortcut `Cmd + Shift + ,` on macOS or `Ctrl + Shift + ,` on Windows, then open Qoder Settings.
2. In the left navigation pane, click MCP.
3. In the JSON file that opens, add your service configuration:

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

4. After saving, the new service appears in your list. A linked icon indicates that the connection succeeded. Expand the item to view the available tools.
