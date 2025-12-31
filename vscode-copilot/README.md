# VS Code Copilot Agents - 文件和索引

這個資料夾包含所有 VS Code Copilot agents 的**文件、使用指南和索引**。

## ⚠️ 重要說明

**實際的 agent 檔案位於 [`../vscode-copilot-agents/`](../vscode-copilot-agents/) 目錄！**

- 本目錄（`vscode-copilot/`）：文件和索引
- [`vscode-copilot-agents/`](../vscode-copilot-agents/)：37 個 `.agent.md` 檔案

## 📚 本目錄內容

### 文件
- [README.md](README.md) - 本檔案
- [QUICK_START.md](QUICK_START.md) - 5 分鐘快速開始
- [USAGE_GUIDE.md](USAGE_GUIDE.md) - 完整使用指南
- [METADATA.md](METADATA.md) - Metadata 詳細說明
- [STRUCTURE.md](STRUCTURE.md) - 結構說明
- [CONVERSION_NOTES.md](CONVERSION_NOTES.md) - 轉換技術說明
- [SUMMARY.md](SUMMARY.md) - 轉換總結

### 索引目錄
每個目錄包含該類別的 README.md 索引：
- [engineering/](engineering/) - 工程開發 (7 個 agents)
- [design/](design/) - 設計 (5 個 agents)
- [marketing/](marketing/) - 行銷 (7 個 agents)
- [product/](product/) - 產品 (3 個 agents)
- [project-management/](project-management/) - 專案管理 (3 個 agents)
- [studio-operations/](studio-operations/) - 營運 (5 個 agents)
- [testing/](testing/) - 測試 (5 個 agents)
- [bonus/](bonus/) - 額外 (2 個 agents)

## 📥 如何使用 Agents

### 推薦方式：使用 vscode-copilot-agents/ 目錄 ⭐

**所有實際的 agent 檔案都在 [`../vscode-copilot-agents/`](../vscode-copilot-agents/) 目錄！**

```bash
# 方法 1: 直接複製單一 agent
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/copilot-instructions.md

# 方法 2: 合併多個 agents
cat vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md \
    vscode-copilot-agents/copilot-design-ui-designer.agent.md \
    > .github/copilot-instructions.md

# 方法 3: 按類別選擇
cat vscode-copilot-agents/copilot-engineering-*.agent.md > .github/copilot-instructions.md
```

### 使用安裝腳本

```bash
# 互動式安裝
./install-vscode-agents.sh

# 指定預設組合
./install-vscode-agents.sh --project --frontend
./install-vscode-agents.sh --project --fullstack
```

詳細使用方式請參閱：
- [vscode-copilot-agents/README.md](../vscode-copilot-agents/README.md) - 單檔案格式使用指南
- [QUICK_START.md](QUICK_START.md) - 快速開始
- [USAGE_GUIDE.md](USAGE_GUIDE.md) - 完整使用指南

## 🔑 Metadata 完整保留

每個 agent 都包含完整的 YAML frontmatter metadata：

```yaml
---
name: frontend-developer
description: Use this agent when building user interfaces...
tools: Write, Read, MultiEdit, Bash, Grep, Glob
color: blue
---
```

- **name** - Agent 唯一識別符
- **description** - 使用情境和專長說明
- **tools** - 可用工具列表（供參考）
- **color** - 視覺識別顏色（供參考）

詳細說明請參閱 [METADATA.md](METADATA.md)

## 🚀 使用方式

在 VS Code 的 Copilot Chat 中，你可以：

1. **直接描述任務**：Copilot 會根據上下文自動應用相關的 agent 指令
2. **使用 @workspace**：讓 Copilot 理解整個專案結構
3. **參考特定檔案**：使用 `#file:filename` 來指定檔案

### 使用範例

```
# 前端開發
"使用 React 和 Tailwind CSS 創建一個響應式的儀表板介面"

# UI 設計
"為這個登入頁面設計一個現代化的 UI，要符合 2024 年的設計趨勢"

# 內容創作
"為我們的新功能撰寫一篇部落格文章和對應的社群媒體貼文"
```

## 📁 目錄結構

```
vscode-copilot/
├── engineering/          # 7 agents
├── design/              # 5 agents
├── marketing/           # 7 agents
├── product/             # 3 agents
├── project-management/  # 3 agents
├── studio-operations/   # 5 agents
├── testing/             # 5 agents
└── bonus/               # 2 agents
```

## 🎯 推薦組合

### 前端開發者
```bash
cat vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md \
    vscode-copilot-agents/copilot-design-ui-designer.agent.md \
    vscode-copilot-agents/copilot-engineering-test-writer-fixer.agent.md \
    > .github/copilot-instructions.md
```

### 全端開發者
```bash
cat vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md \
    vscode-copilot-agents/copilot-engineering-backend-architect.agent.md \
    vscode-copilot-agents/copilot-engineering-devops-automator.agent.md \
    > .github/copilot-instructions.md
```

### 設計團隊
```bash
cat vscode-copilot-agents/copilot-design-*.agent.md > .github/copilot-instructions.md
```

### 行銷團隊
```bash
cat vscode-copilot-agents/copilot-marketing-*.agent.md > .github/copilot-instructions.md
```

## 💡 最佳實踐

1. **明確的任務描述**：清楚說明你想要達成的目標
2. **提供上下文**：使用 @workspace 或 #file 提供相關檔案
3. **迭代開發**：從簡單開始，逐步完善
4. **組合使用**：在同一個對話中結合多個 agent 的專長

## 📖 相關資源

### 本專案文件
- [QUICK_START.md](QUICK_START.md) - 5 分鐘快速開始
- [USAGE_GUIDE.md](USAGE_GUIDE.md) - 完整使用指南
- [METADATA.md](METADATA.md) - Metadata 說明
- [STRUCTURE.md](STRUCTURE.md) - 結構說明
- [../DIRECTORY_STRUCTURE.md](../DIRECTORY_STRUCTURE.md) - 目錄結構詳細說明
- [../vscode-copilot-agents/README.md](../vscode-copilot-agents/README.md) - 單檔案格式使用指南

### 原始專案
- [本專案](https://github.com/lazyjerry/vscode-copilot-agents) - VS Code Copilot Agents
- [Contains Studio AI Agents](https://github.com/contains-studio/agents) - 原始專案

### 官方文件
- [GitHub Copilot 文件](https://docs.github.com/en/copilot)
- [VS Code Copilot Chat](https://code.visualstudio.com/docs/copilot/copilot-chat)
- [Copilot 最佳實踐](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)

## 🤝 貢獻與回饋

如果你發現問題或有改進建議：
- 本專案 Issues: https://github.com/lazyjerry/vscode-copilot-agents/issues
- 本專案 Discussions: https://github.com/lazyjerry/vscode-copilot-agents/discussions
- 原始專案 Issues: https://github.com/contains-studio/agents/issues
- 原始專案 Discussions: https://github.com/contains-studio/agents/discussions

---

**總 Agents**: 37  
**格式**: 完整 metadata（name, description, tools, color）  
**最後更新**: 2025-12-31
