# VS Code Copilot Agents 快速開始

## 5 分鐘快速設定

### 步驟 1: 選擇你需要的 Agents

根據你的工作類型選擇：

**前端開發者：**
```bash
cp vscode-copilot/agents/frontend-developer.md .github/copilot-instructions.md
cat vscode-copilot/agents/ui-designer.md >> .github/copilot-instructions.md
```

**全端開發者：**
```bash
cp vscode-copilot/agents/frontend-developer.md .github/copilot-instructions.md
cat vscode-copilot/agents/backend-architect.md >> .github/copilot-instructions.md
cat vscode-copilot/agents/devops-automator.md >> .github/copilot-instructions.md
```

**產品團隊：**
```bash
cp vscode-copilot/agents/ui-designer.md .github/copilot-instructions.md
cat vscode-copilot/agents/ux-researcher.md >> .github/copilot-instructions.md
cat vscode-copilot/agents/feedback-synthesizer.md >> .github/copilot-instructions.md
```

**行銷團隊：**
```bash
cp vscode-copilot/agents/content-creator.md .github/copilot-instructions.md
cat vscode-copilot/agents/tiktok-strategist.md >> .github/copilot-instructions.md
cat vscode-copilot/agents/growth-hacker.md >> .github/copilot-instructions.md
```

### 步驟 2: 重新載入 VS Code

- 按 `Cmd+Shift+P` (macOS) 或 `Ctrl+Shift+P` (Windows/Linux)
- 輸入 "Reload Window"
- 按 Enter

### 步驟 3: 開始使用

打開 Copilot Chat 並嘗試：

```
使用 React 和 Tailwind CSS 創建一個響應式的導航列
```

## 常用命令範例

### 前端開發

```
創建一個可存取的表單元件，包含驗證和錯誤處理
```

```
優化這個元件的效能 #file:src/components/DataTable.tsx
```

```
為這個頁面添加深色模式支援 @workspace
```

### UI 設計

```
設計一個現代化的登入頁面，要符合 2024 年的設計趨勢
```

```
創建一個設計系統的色彩方案，包含主色、輔助色和語意色
```

```
為這個應用程式設計一套圖示系統
```

### 內容創作

```
為我們的新功能撰寫一篇部落格文章（800 字）
```

```
將這篇文章改寫成 3 則 Twitter 貼文和 1 則 LinkedIn 貼文
```

```
創建一個 TikTok 影片腳本來推廣這個功能
```

### 後端開發

```
設計一個 RESTful API 來處理使用者認證和授權
```

```
為這個 API 添加速率限制和快取機制
```

```
優化這個資料庫查詢的效能 #file:src/db/queries.ts
```

## 進階使用

### 使用工作區上下文

```
@workspace 分析整個專案的架構，建議如何改進
```

### 參考特定檔案

```
根據 #file:src/styles/theme.ts 的設計系統，創建新的元件
```

### 多步驟任務

```
第一步：設計使用者儀表板的 UI
```

```
第二步：使用 React 實作這個設計
```

```
第三步：添加資料視覺化圖表
```

## 疑難排解

### 問題：Copilot 沒有使用 agent 指令

**解決方案：**
1. 確認 `.github/copilot-instructions.md` 檔案存在
2. 重新載入 VS Code 視窗
3. 在提示中提供更多上下文

### 問題：回應不夠專業

**解決方案：**
1. 在提示中明確提到專業領域（如「作為前端開發專家」）
2. 提供更多技術細節
3. 使用 @workspace 提供專案上下文

### 問題：需要不同的專業知識

**解決方案：**
1. 複製額外的 agent 檔案到 `.github/copilot-instructions.md`
2. 或者在新的對話中明確說明需要的專業領域

## 下一步

- 閱讀 [完整使用指南](USAGE_GUIDE.md)
- 查看 [轉換說明](CONVERSION_NOTES.md)
- 探索所有可用的 [agents](agents/)
- 根據團隊需求自訂 agents

## 推薦組合

### 獨立開發者
- frontend-developer
- ui-designer
- rapid-prototyper

### 新創團隊
- frontend-developer
- backend-architect
- growth-hacker
- content-creator

### 企業團隊
- frontend-developer
- backend-architect
- devops-automator
- test-writer-fixer
- legal-compliance-checker

### 設計團隊
- ui-designer
- ux-researcher
- brand-guardian
- visual-storyteller

### 行銷團隊
- content-creator
- growth-hacker
- tiktok-strategist
- instagram-curator
- twitter-engager

## 提示技巧

### ✅ 好的提示

- 明確具體：「創建一個響應式的導航列，支援行動裝置和桌面版本」
- 包含上下文：「根據現有的設計系統 #file:theme.ts」
- 分步驟：「第一步：設計 UI，第二步：實作」
- 提供範例：「類似 Stripe 的定價頁面」

### ❌ 避免的提示

- 太模糊：「做一個網站」
- 缺乏上下文：「修復這個」
- 太複雜：「建立一個完整的電商平台」
- 沒有目標：「改進程式碼」

## 效能追蹤

建議追蹤：
- 任務完成時間
- 程式碼品質改善
- 學習新技術的速度
- 團隊協作效率

開始享受 AI 輔助開發的樂趣吧！🚀
