# Claude Code 到 VS Code Copilot 轉換說明

## 轉換概述

這份文件說明如何將 Claude Code 的 agent 格式轉換為 VS Code Copilot 可用的格式。

## 主要差異

### 1. 檔案格式

#### Claude Code
```markdown
---
name: frontend-developer
description: Use this agent when... Examples:\n\n<example>...
color: blue
tools: Write, Read, MultiEdit, Bash, Grep, Glob
---

System prompt content...
```

#### VS Code Copilot
```markdown
# Frontend Developer Agent

## 概述
Agent description...

## 核心職責
...

## 回應格式
...
```

### 2. Agent 觸發機制

| 特性 | Claude Code | VS Code Copilot |
|------|-------------|-----------------|
| **觸發方式** | YAML frontmatter 中的 description 和 examples | 透過對話內容和上下文 |
| **自動選擇** | 根據任務描述自動選擇合適的 agent | 需要在對話中提供足夠的上下文 |
| **多 Agent** | 可以自動協調多個 agents | 需要在單一對話中整合多個專業領域 |

### 2. 工具存取

#### Claude Code
明確定義可用工具：
- `Write`: 寫入檔案
- `Read`: 讀取檔案
- `MultiEdit`: 批次編輯
- `Bash`: 執行命令
- `Grep`: 搜尋內容
- `Glob`: 檔案匹配
- `WebSearch`: 網路搜尋
- `WebFetch`: 獲取網頁內容

#### VS Code Copilot
使用 VS Code 內建功能：
- 透過程式碼建議進行檔案修改
- 使用 `@workspace` 存取專案檔案
- 使用 `#file:path` 參考特定檔案
- 使用 `#terminalLastCommand` 參考終端機輸出

**注意**：轉換後的檔案保留了 `tools` 欄位供參考，但 VS Code Copilot 會使用自己的工具系統。

### 4. 視覺識別

- **Claude Code**: 支援顏色標記（blue, green, purple, indigo, magenta, cyan 等）
- **VS Code Copilot**: 不支援視覺標記（但轉換後的檔案保留 `color` 欄位供參考）

## 轉換策略

### 1. 保留核心內容

✅ **保留：**
- 系統提示詞的主要內容
- 專業領域知識
- 最佳實踐和框架
- 技術規格和標準

❌ **移除：**
- YAML frontmatter
- 顏色標記
- 工具列表
- Claude Code 特定的範例格式

### 2. 重新組織結構

**原始結構（Claude Code）：**
```
YAML Frontmatter
├── name
├── description (含 examples)
├── color
└── tools

System Prompt
├── Introduction
├── Responsibilities
├── Expertise
└── Best Practices
```

**轉換後結構（VS Code Copilot）：**
```
# Agent Title

## 概述
(從 description 提取)

## 核心職責
(從 system prompt 提取)

## 專業領域
(從 system prompt 提取)

## 最佳實踐
(從 system prompt 提取)

## 回應格式
(新增：指導 Copilot 如何回應)
```

### 3. 調整範例格式

#### Claude Code 範例格式
```xml
<example>
Context: Building a new user interface
user: "Create a dashboard for displaying user analytics"
assistant: "I'll build an analytics dashboard..."
<commentary>
Complex UI components require frontend expertise...
</commentary>
</example>
```

#### VS Code Copilot 格式
將範例整合到「概述」或「使用情境」章節：

```markdown
## 使用情境

### 建立新的使用者介面
當需要建立複雜的 UI 元件（如分析儀表板）時，
此 agent 會提供前端專業知識，確保元件的效能和可維護性。
```

## 自動轉換腳本

使用提供的 `convert-to-vscode.js` 腳本：

```bash
# 轉換所有 agents
node convert-to-vscode.js --all

# 轉換特定 agent
node convert-to-vscode.js --agent=frontend-developer

# 查看可用的 agents
node convert-to-vscode.js
```

### 腳本功能

1. **解析 YAML frontmatter**：提取 metadata
2. **清理描述**：移除 XML 標籤和特殊格式
3. **重組內容**：按照 VS Code Copilot 格式重新組織
4. **添加回應格式**：為每個 agent 添加標準的回應指南

## 手動轉換步驟

如果需要手動轉換：

### 步驟 1: 提取基本資訊

從 YAML frontmatter 中提取：
- `name`: 用作檔案名稱和標題
- `description`: 轉換為「概述」章節
- 忽略 `color` 和 `tools`

### 步驟 2: 清理描述

移除：
- `\n` 轉義字元
- `<example>` 和 `</example>` 標籤
- `<commentary>` 和 `</commentary>` 標籤
- XML 格式的對話範例

### 步驟 3: 重組系統提示詞

保持原有的結構，但確保：
- 使用清晰的 Markdown 標題
- 保留所有技術細節
- 保持最佳實踐和框架

### 步驟 4: 添加回應格式

在文件末尾添加：

```markdown
## 回應格式

當收到相關任務時：
1. 分析需求和上下文
2. 提供清晰的解決方案或建議
3. 包含具體的實作步驟或程式碼範例
4. 考慮最佳實踐和潛在問題
5. 提供可行的下一步建議
```

## 轉換後的使用差異

### Claude Code 使用方式

```
# Agent 會自動根據任務描述被觸發
"Create a responsive dashboard"
→ 自動使用 frontend-developer agent
```

### VS Code Copilot 使用方式

```
# 需要提供更多上下文
"使用 React 和 Tailwind CSS 創建一個響應式的儀表板，
包含圖表和資料表格，要符合無障礙標準"
→ Copilot 根據載入的指令提供專業建議
```

## 最佳化建議

### 1. 合併相關 Agents

對於小型專案，可以合併相關的 agents：

```bash
# 合併前端相關的 agents
cat vscode-copilot/agents/frontend-developer.md \
    vscode-copilot/agents/ui-designer.md \
    > .github/copilot-instructions.md
```

### 2. 專案特定調整

為不同專案使用不同的 agent 組合：

- **前端專案**：frontend-developer + ui-designer
- **全端專案**：frontend-developer + backend-architect
- **內容專案**：content-creator + tiktok-strategist

### 3. 團隊自訂

根據團隊需求調整：
- 添加公司特定的最佳實踐
- 整合內部工具和流程
- 調整技術棧偏好

## 限制與權衡

### Claude Code 的優勢

1. **自動 Agent 選擇**：根據任務自動選擇合適的 agent
2. **多 Agent 協作**：可以無縫協調多個 agents
3. **明確的工具存取**：清楚定義每個 agent 可以使用的工具
4. **視覺識別**：顏色標記幫助識別不同的 agents

### VS Code Copilot 的優勢

1. **深度整合**：與 VS Code 緊密整合
2. **即時建議**：在編輯器中提供即時程式碼建議
3. **廣泛採用**：更多開發者使用和熟悉
4. **持續更新**：GitHub 持續改進和更新

### 權衡考量

| 考量點 | Claude Code | VS Code Copilot |
|--------|-------------|-----------------|
| **學習曲線** | 需要理解 agent 系統 | 熟悉的 VS Code 介面 |
| **自動化程度** | 高（自動選擇 agent） | 中（需要明確指導） |
| **客製化** | 透過 YAML 配置 | 透過 Markdown 指令 |
| **協作** | 原生多 agent 支援 | 需要手動協調 |
| **成本** | Claude API 費用 | GitHub Copilot 訂閱 |

## 遷移檢查清單

- [ ] 備份原始 Claude Code agents
- [ ] 執行轉換腳本或手動轉換
- [ ] 檢查轉換後的內容完整性
- [ ] 測試關鍵 agents 的功能
- [ ] 根據團隊需求調整內容
- [ ] 更新團隊文件和使用指南
- [ ] 培訓團隊成員使用新格式
- [ ] 收集回饋並持續改進

## 進一步改進

### 短期改進

1. 為每個 agent 添加更多使用範例
2. 創建快速參考卡片
3. 建立 agent 選擇流程圖

### 長期改進

1. 開發 VS Code 擴展以更好地支援 agents
2. 建立 agent 效能追蹤系統
3. 創建社群分享平台

## 支援與回饋

如果在轉換過程中遇到問題：

1. 檢查轉換腳本的輸出日誌
2. 手動檢查有問題的 agent 檔案
3. 參考已成功轉換的範例
4. 在專案 Issues 中回報問題
