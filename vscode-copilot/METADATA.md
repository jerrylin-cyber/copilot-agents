# Metadata 完整說明

# Metadata 完整說明

## 概述

所有轉換後的 agents 都保留了完整的 YAML frontmatter metadata，包括 `name`、`description`、`tools` 和 `color` 欄位。

## Metadata 欄位

### 1. name（必要）

**用途**：Agent 的唯一識別符

**格式**：kebab-case（小寫字母，用連字號分隔）

**範例**：
```yaml
name: frontend-developer
name: ui-designer
name: content-creator
name: growth-hacker
```

**在 VS Code Copilot 中的作用**：
- 識別不同的 agent
- 用於文件和參考

---

### 2. description（必要）

**用途**：描述 agent 的專長和使用情境

**格式**：單行文字（可使用 `\n` 表示換行）

**範例**：
```yaml
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
```

**在 VS Code Copilot 中的作用**：
- 幫助 Copilot 理解何時應該應用此 agent 的知識
- 提供上下文給 AI 模型
- 作為文件參考

---

### 3. tools（選用，保留自 Claude Code）

**用途**：列出 agent 可以使用的工具

**格式**：逗號分隔的工具名稱列表

**可用工具**：
- `Write` - 寫入檔案
- `Read` - 讀取檔案
- `MultiEdit` - 批次編輯多個檔案
- `Bash` - 執行 shell 命令
- `Grep` - 搜尋檔案內容
- `Glob` - 檔案模式匹配
- `WebSearch` - 網路搜尋
- `WebFetch` - 獲取網頁內容
- `Task` - 執行任務

**範例**：
```yaml
# 工程類 agents
tools: Write, Read, MultiEdit, Bash, Grep, Glob

# 設計類 agents
tools: Write, Read, MultiEdit, WebSearch, WebFetch

# 行銷類 agents
tools: Write, Read, WebSearch, WebFetch

# 測試類 agents
tools: Write, Read, MultiEdit, Bash, Grep
```

**在 VS Code Copilot 中的作用**：
- **主要供參考**：VS Code Copilot 使用自己的內建工具系統
- 可以幫助理解 agent 的預期能力範圍
- 作為文件和遷移參考

**VS Code Copilot 的對應功能**：
| Claude Code Tool | VS Code Copilot 對應 |
|------------------|---------------------|
| Write | 程式碼建議和編輯 |
| Read | @workspace, #file:path |
| MultiEdit | 多檔案編輯建議 |
| Bash | #terminalLastCommand |
| Grep | 內建搜尋功能 |
| Glob | 檔案模式匹配 |
| WebSearch | 內建知識庫 |
| WebFetch | 內建知識庫 |

---

### 4. color（選用，保留自 Claude Code）

**用途**：Agent 的視覺識別顏色

**格式**：顏色名稱

**可用顏色**：
- `blue` - 藍色（通常用於工程類）
- `green` - 綠色（通常用於成長/優化類）
- `purple` - 紫色（通常用於產品類）
- `indigo` - 靛藍色（通常用於品牌/設計類）
- `magenta` - 洋紅色（通常用於設計類）
- `cyan` - 青色（通常用於測試類）
- `orange` - 橙色（通常用於行銷類）
- `red` - 紅色（通常用於緊急/修復類）
- `yellow` - 黃色（通常用於警告/分析類）

**範例**：
```yaml
color: blue      # frontend-developer
color: magenta   # ui-designer
color: cyan      # test-writer-fixer
color: orange    # content-creator
```

**在 VS Code Copilot 中的作用**：
- **主要供參考**：VS Code Copilot 目前不顯示顏色標記
- 可以幫助在文件中快速識別 agent 類型
- 保留以便未來可能的功能支援

---

## 完整範例

### 工程類 Agent
```yaml
---
name: frontend-developer
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
tools: Write, Read, MultiEdit, Bash, Grep, Glob
color: blue
---
```

### 設計類 Agent
```yaml
---
name: ui-designer
description: Use this agent when creating user interfaces, designing components, building design systems, or improving visual aesthetics. This agent specializes in creating beautiful, functional interfaces that can be implemented quickly within 6-day sprints.
tools: Write, Read, MultiEdit, WebSearch, WebFetch
color: magenta
---
```

### 行銷類 Agent
```yaml
---
name: content-creator
description: The Content Creator specializes in cross-platform content generation, from long-form blog posts to engaging video scripts and social media content.
tools: Write, Read, WebSearch, WebFetch
color: orange
---
```

### 測試類 Agent
```yaml
---
name: test-writer-fixer
description: Use this agent when code changes have been made and you need to write new tests, run existing tests, analyze failures, and fix them while maintaining test integrity.
tools: Write, Read, MultiEdit, Bash, Grep
color: cyan
---
```

---

**最後更新**: 2025-12-31  
**版本**: 1.0.0  
**Metadata 完整性**: 100%


## Metadata 欄位

### 1. name（必要）✅

**用途**：Agent 的唯一識別符

**格式**：kebab-case（小寫字母，用連字號分隔）

**範例**：
```yaml
name: frontend-developer
name: ui-designer
name: content-creator
```

**在 GitHub Copilot 中的作用**：
- 識別和調用特定的 agent
- 用於 agent 選擇和路由

---

### 2. description（必要）✅

**用途**：簡短描述 agent 的專長和使用情境

**格式**：單行文字

**範例**：
```yaml
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
```

**在 GitHub Copilot 中的作用**：
- 幫助 Copilot 理解何時應該使用此 agent
- 提供上下文給 AI 模型
- 顯示在 agent 選擇介面

---

### 3. instructions（必要）✅

**用途**：詳細的 agent 指令和行為規範

**格式**：多行文字（使用 YAML 的 `|` 語法）

**範例**：
```yaml
instructions: |
  You are an elite frontend development specialist with deep expertise in modern JavaScript frameworks.
  
  Your primary responsibilities:
  
  1. **Component Architecture**: When building interfaces, you will:
     - Design reusable, composable component hierarchies
     - Implement proper state management
  
  2. **Performance Optimization**: You will ensure fast experiences by:
     - Implementing lazy loading and code splitting
     - Optimizing React re-renders
```

**在 GitHub Copilot 中的作用**：
- 定義 agent 的行為和專業知識
- 提供詳細的上下文和指導
- 影響 AI 的回應風格和內容

---

## 完整範例

### 工程類 Agent
```yaml
---
name: frontend-developer
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance.
instructions: |
  You are an elite frontend development specialist with deep expertise in modern JavaScript frameworks.
  
  Your primary responsibilities:
  1. Component Architecture
  2. Responsive Design
  3. Performance Optimization
---
```

### 設計類 Agent
```yaml
---
name: ui-designer
description: Use this agent when creating user interfaces, designing components, or building design systems.
instructions: |
  You are a visionary UI designer who creates beautiful, implementable interfaces.
  
  Your expertise includes:
  - Modern design trends
  - Component architecture
  - Design systems
---
```

---

## 與 Claude Code 的差異

### Claude Code 格式
```yaml
---
name: frontend-developer
description: Agent description with examples
color: blue
tools: Write, Read, MultiEdit, Bash
---
```

### GitHub Copilot 格式
```yaml
---
name: frontend-developer
description: Agent description
instructions: |
  Detailed agent instructions
---
```

### 主要差異

| 欄位 | Claude Code | GitHub Copilot |
|------|-------------|----------------|
| `name` | ✅ 支援 | ✅ 支援 |
| `description` | ✅ 支援（含範例） | ✅ 支援（簡短描述） |
| `instructions` | ❌ 不使用 | ✅ **必要**（詳細指令） |
| `color` | ✅ 支援 | ❌ 不支援 |
| `tools` | ✅ 支援 | ❌ 不支援 |

---

## 轉換邏輯

### 從 Claude Code 到 GitHub Copilot

1. **name** → 直接保留
2. **description** → 清理 XML 標籤後保留
3. **系統提示詞** → 轉換為 `instructions`
4. **color** → 移除（不支援）
5. **tools** → 移除（不支援）

### 範例轉換

**轉換前（Claude Code）：**
```yaml
---
name: frontend-developer
description: Use this agent when building UIs...
color: blue
tools: Write, Read, MultiEdit
---

You are an elite frontend developer...
```

**轉換後（GitHub Copilot）：**
```yaml
---
name: frontend-developer
description: Use this agent when building UIs...
instructions: |
  You are an elite frontend developer...
---
```

---

## 使用建議

### 1. 選擇合適的 Agent

根據 `description` 快速了解 agent 的用途：

```bash
# 搜尋特定功能的 agents
grep "description:" vscode-copilot/*/*.md | grep "user interface"
```

### 2. 查看 Agent 指令

```bash
# 查看完整的 agent 定義
head -n 50 vscode-copilot/engineering/frontend-developer.md
```

### 3. 自訂 Agent

編輯 `instructions` 欄位來自訂 agent 行為：

```yaml
---
name: my-custom-agent
description: My custom agent for specific tasks
instructions: |
  You are a specialist in [your domain].
  
  Your responsibilities:
  1. [Task 1]
  2. [Task 2]
  
  Your approach:
  - [Guideline 1]
  - [Guideline 2]
---
```

---

## 常見問題

### Q: 為什麼移除了 `tools` 和 `color`？

A: GitHub Copilot 官方格式不支援這些欄位。Copilot 使用自己的工具系統，不需要明確定義。

### Q: `instructions` 可以多長？

A: 沒有明確限制，但建議保持在 2000-3000 字以內，以確保最佳效能。

### Q: 可以使用 Markdown 格式嗎？

A: 可以！`instructions` 欄位支援 Markdown 格式，包括標題、列表、程式碼區塊等。

### Q: 如何驗證格式正確？

A: 使用以下命令檢查：
```bash
# 檢查 YAML frontmatter
head -n 10 vscode-copilot/engineering/frontend-developer.md

# 驗證所有必要欄位都存在
grep -A 3 "^---$" vscode-copilot/engineering/frontend-developer.md | head -n 10
```

---

## 官方文件參考

- [VS Code Copilot Custom Agents](https://code.visualstudio.com/docs/copilot/customization/custom-agents)
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [VS Code Copilot Chat](https://code.visualstudio.com/docs/copilot/copilot-chat)

---

**最後更新**: 2025-12-31  
**版本**: 2.0.0  
**格式**: GitHub Copilot 官方格式  
**兼容性**: VS Code 1.85+


## Metadata 欄位

### 1. name（必要）

**用途**：Agent 的唯一識別符

**格式**：kebab-case（小寫字母，用連字號分隔）

**範例**：
```yaml
name: frontend-developer
name: ui-designer
name: content-creator
name: growth-hacker
```

**在 VS Code Copilot 中的作用**：
- 識別不同的 agent
- 用於文件和參考

---

### 2. description（必要）

**用途**：描述 agent 的專長和使用情境

**格式**：單行文字（可使用 `\n` 表示換行）

**範例**：
```yaml
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
```

**在 VS Code Copilot 中的作用**：
- 幫助 Copilot 理解何時應該應用此 agent 的知識
- 提供上下文給 AI 模型
- 作為文件參考

---

### 3. tools（選用，保留自 Claude Code）

**用途**：列出 agent 可以使用的工具

**格式**：逗號分隔的工具名稱列表

**可用工具**：
- `Write` - 寫入檔案
- `Read` - 讀取檔案
- `MultiEdit` - 批次編輯多個檔案
- `Bash` - 執行 shell 命令
- `Grep` - 搜尋檔案內容
- `Glob` - 檔案模式匹配
- `WebSearch` - 網路搜尋
- `WebFetch` - 獲取網頁內容
- `Task` - 執行任務

**範例**：
```yaml
# 工程類 agents
tools: Write, Read, MultiEdit, Bash, Grep, Glob

# 設計類 agents
tools: Write, Read, MultiEdit, WebSearch, WebFetch

# 行銷類 agents
tools: Write, Read, WebSearch, WebFetch

# 測試類 agents
tools: Write, Read, MultiEdit, Bash, Grep
```

**在 VS Code Copilot 中的作用**：
- **主要供參考**：VS Code Copilot 使用自己的內建工具系統
- 可以幫助理解 agent 的預期能力範圍
- 作為文件和遷移參考

**VS Code Copilot 的對應功能**：
| Claude Code Tool | VS Code Copilot 對應 |
|------------------|---------------------|
| Write | 程式碼建議和編輯 |
| Read | @workspace, #file:path |
| MultiEdit | 多檔案編輯建議 |
| Bash | #terminalLastCommand |
| Grep | 內建搜尋功能 |
| Glob | 檔案模式匹配 |
| WebSearch | 內建知識庫 |
| WebFetch | 內建知識庫 |

---

### 4. color（選用，保留自 Claude Code）

**用途**：Agent 的視覺識別顏色

**格式**：顏色名稱

**可用顏色**：
- `blue` - 藍色（通常用於工程類）
- `green` - 綠色（通常用於成長/優化類）
- `purple` - 紫色（通常用於產品類）
- `indigo` - 靛藍色（通常用於品牌/設計類）
- `magenta` - 洋紅色（通常用於設計類）
- `cyan` - 青色（通常用於測試類）
- `orange` - 橙色（通常用於行銷類）
- `red` - 紅色（通常用於緊急/修復類）
- `yellow` - 黃色（通常用於警告/分析類）

**範例**：
```yaml
color: blue      # frontend-developer
color: magenta   # ui-designer
color: cyan      # test-writer-fixer
color: orange    # content-creator
```

**在 VS Code Copilot 中的作用**：
- **主要供參考**：VS Code Copilot 目前不顯示顏色標記
- 可以幫助在文件中快速識別 agent 類型
- 保留以便未來可能的功能支援

---

## 完整範例

### 工程類 Agent
```yaml
---
name: frontend-developer
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
tools: Write, Read, MultiEdit, Bash, Grep, Glob
color: blue
---
```

### 設計類 Agent
```yaml
---
name: ui-designer
description: Use this agent when creating user interfaces, designing components, building design systems, or improving visual aesthetics. This agent specializes in creating beautiful, functional interfaces that can be implemented quickly within 6-day sprints.
tools: Write, Read, MultiEdit, WebSearch, WebFetch
color: magenta
---
```

### 行銷類 Agent
```yaml
---
name: content-creator
description: The Content Creator specializes in cross-platform content generation, from long-form blog posts to engaging video scripts and social media content.
tools: Write, Read, WebSearch, WebFetch
color: orange
---
```

### 測試類 Agent
```yaml
---
name: test-writer-fixer
description: Use this agent when code changes have been made and you need to write new tests, run existing tests, analyze failures, and fix them while maintaining test integrity.
tools: Write, Read, MultiEdit, Bash, Grep
color: cyan
---
```

---

## Metadata 統計

### 按類別統計

| 類別 | Agents 數量 | 常見 Tools | 常見 Color |
|------|------------|-----------|-----------|
| Engineering | 7 | Write, Read, MultiEdit, Bash, Grep, Glob | blue, cyan |
| Design | 5 | Write, Read, MultiEdit, WebSearch, WebFetch | magenta, indigo |
| Marketing | 7 | Write, Read, WebSearch, WebFetch | orange, yellow |
| Product | 3 | Write, Read, WebSearch | purple |
| Project Management | 3 | Write, Read, Bash | green |
| Studio Operations | 5 | Write, Read, Bash, Grep | yellow, green |
| Testing | 5 | Write, Read, MultiEdit, Bash, Grep | cyan |
| Bonus | 2 | 各異 | 各異 |

### Tools 使用頻率

| Tool | 使用次數 | 使用率 |
|------|---------|--------|
| Write | 37 | 100% |
| Read | 37 | 100% |
| MultiEdit | 25 | 68% |
| Bash | 20 | 54% |
| Grep | 18 | 49% |
| Glob | 15 | 41% |
| WebSearch | 12 | 32% |
| WebFetch | 12 | 32% |

### Color 分布

| Color | 使用次數 | 主要類別 |
|-------|---------|---------|
| blue | 8 | Engineering |
| cyan | 6 | Testing, Engineering |
| magenta | 5 | Design |
| orange | 5 | Marketing |
| green | 4 | Product, Operations |
| purple | 3 | Product |
| indigo | 3 | Design |
| yellow | 2 | Operations |
| red | 1 | Bonus |

---

## 使用建議

### 1. 選擇 Agents 時

根據 `tools` 欄位選擇合適的 agents：

- **需要檔案操作**：選擇有 `Write, Read, MultiEdit` 的 agents
- **需要執行命令**：選擇有 `Bash` 的 agents
- **需要搜尋功能**：選擇有 `Grep, Glob` 的 agents
- **需要網路資訊**：選擇有 `WebSearch, WebFetch` 的 agents

### 2. 組合 Agents 時

根據 `color` 分組來組合互補的 agents：

- **藍色系**（blue, cyan）：工程和測試
- **紅色系**（magenta, orange）：設計和行銷
- **綠色系**（green, yellow）：產品和營運

### 3. 文件參考時

使用 `description` 快速了解 agent 的用途：

```bash
# 搜尋特定功能的 agents
grep -r "user interface" vscode-copilot/*/

# 列出所有工具組合
grep "^tools:" vscode-copilot/*/*.md
```

---

## 與 Claude Code 的兼容性

### 完全兼容
- ✅ `name` - 格式和用途完全相同
- ✅ `description` - 格式和用途完全相同

### 保留但用途不同
- ⚠️ `tools` - 保留供參考，但 VS Code Copilot 使用自己的工具系統
- ⚠️ `color` - 保留供參考，但 VS Code Copilot 不顯示顏色

### 遷移建議

如果你想在 Claude Code 和 VS Code Copilot 之間切換：

1. **保留所有 metadata**：確保兩個平台都能正確讀取
2. **使用相同的檔案**：YAML frontmatter 格式兩個平台都支援
3. **注意工具差異**：了解 `tools` 欄位在不同平台的實際作用

---

## 常見問題

### Q: VS Code Copilot 會使用 `tools` 欄位嗎？

A: 不會直接使用。VS Code Copilot 有自己的工具系統。但保留此欄位有以下好處：
- 作為文件參考
- 幫助理解 agent 的能力範圍
- 保持與 Claude Code 的兼容性

### Q: 為什麼保留 `color` 欄位？

A: 雖然 VS Code Copilot 目前不顯示顏色，但保留此欄位：
- 便於在文件中識別 agent 類型
- 為未來可能的功能預留
- 保持與 Claude Code 的兼容性

### Q: 可以自訂 metadata 欄位嗎？

A: 可以！YAML frontmatter 支援自訂欄位。你可以添加：
```yaml
---
name: my-agent
description: My custom agent
tools: Write, Read
color: blue
version: 1.0.0
author: Your Name
tags: custom, experimental
---
```

### Q: 如何驗證 metadata 格式正確？

A: 使用以下命令檢查：
```bash
# 檢查所有 agents 的 metadata
for file in vscode-copilot/*/*.md; do
  echo "=== $file ==="
  head -n 10 "$file" | grep -A 5 "^---"
done
```

---

**最後更新**: 2025-12-31  
**版本**: 1.0.0  
**Metadata 完整性**: 100%
