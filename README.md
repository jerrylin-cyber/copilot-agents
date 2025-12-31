# VS Code Copilot Agents

一套完整的 37 個專業 AI agents 集合，專為 VS Code GitHub Copilot 設計，轉換自 [Contains Studio AI Agents](https://github.com/contains-studio/agents)。每個 agent 都是其領域的專家，隨時準備增強你的開發工作流程。

## 🚀 快速開始

```bash
# 克隆專案
git clone https://github.com/lazyjerry/vscode-copilot-agents.git
cd vscode-copilot-agents

# 複製單一 agent 到 .github/agents/ 目錄
mkdir -p .github/agents
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/

# 或使用互動式安裝工具
./install-vscode-agents.sh
```

然後重新載入 VS Code（`Cmd+Shift+P` > "Reload Window"）並開始使用 Copilot Chat！

## 📁 專案結構

本專案提供兩種格式的 agents：

### 📄 vscode-copilot-agents/ - 即用格式 ⭐

**所有 37 個 agents 都在單一目錄中，方便存取！**

```
vscode-copilot-agents/
├── copilot-engineering-frontend-developer.agent.md
├── copilot-engineering-backend-architect.agent.md
├── copilot-design-ui-designer.agent.md
├── copilot-marketing-content-creator.agent.md
└── ... (共 37 個 .agent.md 檔案)
```

**特點：**
- ✅ 統一命名：`copilot-{類別}-{名稱}.agent.md`
- ✅ 所有檔案集中在一處
- ✅ 易於搜尋和過濾
- ✅ 可直接複製使用

**快速使用：**
```bash
# 創建 agents 目錄
mkdir -p .github/agents

# 單一 agent
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/

# 多個 agents
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/
cp vscode-copilot-agents/copilot-design-ui-designer.agent.md .github/agents/

# 整個類別的所有 agents
cp vscode-copilot-agents/copilot-engineering-*.agent.md .github/agents/
```

### 📚 vscode-copilot/ - 文件與指南

完整的文件和類別索引：

```
vscode-copilot/
├── engineering/          # 7 個 agents 索引
├── design/              # 5 個 agents 索引
├── marketing/           # 7 個 agents 索引
├── product/             # 3 個 agents 索引
├── project-management/  # 3 個 agents 索引
├── studio-operations/   # 5 個 agents 索引
├── testing/             # 5 個 agents 索引
├── bonus/               # 2 個 agents 索引
├── README.md            # 主要文件
├── QUICK_START.md       # 5 分鐘指南
├── USAGE_GUIDE.md       # 完整使用指南
├── METADATA.md          # Metadata 說明
└── STRUCTURE.md         # 結構詳情
```

## 🎯 可用的 Agents（共 37 個）

### 工程開發 (7)
- **frontend-developer** - React/Vue/Angular、狀態管理、效能優化
- **backend-architect** - API、資料庫、可擴展系統
- **devops-automator** - CI/CD、部署、基礎設施
- **ai-engineer** - ML/AI 整合、模型部署
- **mobile-app-builder** - iOS/Android 原生開發
- **rapid-prototyper** - MVP 開發、快速迭代
- **test-writer-fixer** - 測試、除錯、品質保證

### 設計 (5)
- **ui-designer** - 介面設計、元件系統
- **ux-researcher** - 使用者研究、可用性測試
- **brand-guardian** - 品牌一致性、視覺識別
- **visual-storyteller** - 視覺內容、故事敘述
- **whimsy-injector** - 愉悅互動、動畫效果

### 行銷 (7)
- **content-creator** - 部落格文章、社群媒體、影片腳本
- **growth-hacker** - 病毒式循環、使用者獲取
- **tiktok-strategist** - TikTok 內容策略
- **instagram-curator** - Instagram 內容與互動
- **twitter-engager** - Twitter/X 互動策略
- **reddit-community-builder** - Reddit 社群管理
- **app-store-optimizer** - ASO、應用商店優化

### 產品 (3)
- **feedback-synthesizer** - 使用者回饋分析
- **sprint-prioritizer** - 功能優先順序
- **trend-researcher** - 市場趨勢、機會分析

### 專案管理 (3)
- **project-shipper** - 專案交付、上線
- **studio-producer** - 團隊協調
- **experiment-tracker** - A/B 測試、實驗追蹤

### 營運 (5)
- **analytics-reporter** - 資料分析、洞察報告
- **finance-tracker** - 財務追蹤
- **infrastructure-maintainer** - 基礎設施管理
- **legal-compliance-checker** - 法規合規檢查
- **support-responder** - 客戶支援

### 測試 (5)
- **api-tester** - API 測試、驗證
- **performance-benchmarker** - 效能優化
- **test-results-analyzer** - 測試分析
- **tool-evaluator** - 工具評估
- **workflow-optimizer** - 工作流程優化

### 額外 (2)
- **studio-coach** - 團隊指導、最佳實踐
- **joker** - 科技幽默、調節氣氛

## 🛠️ 安裝方法

### 方法 1：互動式安裝工具（推薦）

```bash
# macOS/Linux
./install-vscode-agents.sh

# Windows
.\install-vscode-agents.ps1
```

可選擇預設組合：
- 前端開發者
- 全端開發者
- 設計團隊
- 行銷團隊
- 自訂選擇

### 方法 2：直接複製

```bash
# 創建 agents 目錄
mkdir -p .github/agents

# 前端開發者設定
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/
cp vscode-copilot-agents/copilot-design-ui-designer.agent.md .github/agents/
cp vscode-copilot-agents/copilot-engineering-test-writer-fixer.agent.md .github/agents/

# 全端開發者設定
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/
cp vscode-copilot-agents/copilot-engineering-backend-architect.agent.md .github/agents/
cp vscode-copilot-agents/copilot-engineering-devops-automator.agent.md .github/agents/
```

### 方法 3：從原始檔案重新生成

```bash
# 從原始格式轉換所有 agents
node convert-to-vscode.js --all

# 生成 .agent.md 檔案
./generate-agent-files.sh
```

## 📖 使用範例

### 前端開發
```
使用 React 和 Tailwind CSS 創建一個響應式儀表板，包含圖表和資料表格
```

### UI 設計
```
設計一個符合 2024 年設計趨勢的現代化登入頁面，支援深色模式
```

### 內容創作
```
為我們的新功能撰寫一篇部落格文章，並創建對應的社群媒體貼文
```

### API 開發
```
設計一個用於使用者認證的 RESTful API，包含速率限制和快取機制
```

## 🔑 Metadata 格式

每個 agent 都包含完整的 YAML frontmatter：

```yaml
---
name: frontend-developer
description: 當需要建立使用者介面時使用此 agent...
tools: Write, Read, MultiEdit, Bash, Grep, Glob
color: blue
---
```

- **name**：唯一識別符
- **description**：使用情境和專長
- **tools**：可用工具（供參考）
- **color**：視覺識別（供參考）

## 📚 文件

- [快速開始指南](vscode-copilot/QUICK_START.md) - 5 分鐘快速上手
- [使用指南](vscode-copilot/USAGE_GUIDE.md) - 完整使用說明
- [Metadata 指南](vscode-copilot/METADATA.md) - 理解 metadata
- [目錄結構](DIRECTORY_STRUCTURE.md) - 詳細結構說明
- [Agent 檔案 README](vscode-copilot-agents/README.md) - 單檔案格式指南

## 🔄 轉換細節

這些 agents 從 Claude Code 格式轉換為 VS Code Copilot 格式：

**保留內容：**
- ✅ 完整的系統提示詞
- ✅ 所有專業知識
- ✅ Metadata（name、description、tools、color）
- ✅ 最佳實踐和框架

**優化內容：**
- ✅ 清理描述中的 XML 標籤
- ✅ 按類別組織
- ✅ 新增單檔案格式方便使用
- ✅ 創建完整文件

## 🤝 貢獻

發現問題或有建議？

- **本專案**：https://github.com/lazyjerry/vscode-copilot-agents
  - [Issues](https://github.com/lazyjerry/vscode-copilot-agents/issues)
  - [Discussions](https://github.com/lazyjerry/vscode-copilot-agents/discussions)

- **原始專案**：https://github.com/contains-studio/agents
  - [Issues](https://github.com/contains-studio/agents/issues)
  - [Discussions](https://github.com/contains-studio/agents/discussions)

## 📜 授權

與原始 [Contains Studio AI Agents](https://github.com/contains-studio/agents) 專案相同的授權。

## 🙏 致謝

特別感謝 [Contains Studio](https://github.com/contains-studio) 創建和維護原始的 AI agents 集合。

---

**總 Agents 數**：37  
**格式**：VS Code Copilot 兼容  
**Metadata**：完整（name、description、tools、color）  
**最後更新**：2025-12-31  
**轉換成功率**：100%

用 ❤️ 為 VS Code Copilot 社群製作
