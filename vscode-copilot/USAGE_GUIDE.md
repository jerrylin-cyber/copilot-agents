# VS Code Copilot Agents 使用指南

## 快速開始

### 1. 安裝步驟

#### 選項 A: 專案級別（推薦）

在你的專案中使用特定的 agents：

```bash
# 1. 在專案根目錄創建 .github 資料夾
mkdir -p .github

# 2. 複製你需要的 agent 指令
cp vscode-copilot/agents/frontend-developer.md .github/copilot-instructions.md

# 3. 如果需要多個 agents，可以合併它們
cat vscode-copilot/agents/ui-designer.md >> .github/copilot-instructions.md
cat vscode-copilot/agents/content-creator.md >> .github/copilot-instructions.md
```

#### 選項 B: 使用者級別（全域）

讓所有專案都能使用這些 agents：

```bash
# macOS/Linux
mkdir -p ~/.config/Code/User/copilot
cp vscode-copilot/agents/*.md ~/.config/Code/User/copilot/

# Windows (PowerShell)
New-Item -ItemType Directory -Force -Path "$env:APPDATA\Code\User\copilot"
Copy-Item vscode-copilot\agents\*.md "$env:APPDATA\Code\User\copilot\"
```

### 2. 重新載入 VS Code

安裝後，重新載入 VS Code 視窗：
- 按 `Cmd+Shift+P` (macOS) 或 `Ctrl+Shift+P` (Windows/Linux)
- 輸入 "Reload Window"
- 按 Enter

## 使用方式

### 基本對話

直接在 Copilot Chat 中描述你的需求：

```
建立一個響應式的使用者儀表板，包含圖表和資料表格
```

Copilot 會根據載入的 agent 指令自動應用相關的專業知識。

### 使用上下文

#### 參考檔案

```
使用 #file:src/components/Button.tsx 的樣式，創建一個新的 Card 元件
```

#### 參考工作區

```
@workspace 分析整個專案的架構，建議如何重構狀態管理
```

#### 參考終端機

```
#terminalLastCommand 這個錯誤是什麼意思？如何修復？
```

### 特定領域任務

#### 前端開發

```
使用 React 和 Tailwind CSS 建立一個可存取的表單元件，包含驗證
```

```
優化這個元件的效能，它在渲染大型列表時很慢
```

#### UI 設計

```
為這個登入頁面設計一個現代化的 UI，要符合 2024 年的設計趨勢
```

```
創建一個設計系統的色彩方案和字體比例
```

#### 內容創作

```
為我們的新功能撰寫一篇部落格文章，並提供對應的社群媒體貼文
```

```
將這篇文章改寫成 TikTok 影片腳本
```

## 進階技巧

### 1. 組合多個專業領域

```
我需要：
1. 設計一個現代化的產品頁面 UI
2. 使用 React 和 Tailwind 實作
3. 撰寫產品描述和行銷文案
```

### 2. 迭代開發

```
第一步：建立基本的元件結構
```

然後：

```
第二步：添加動畫和互動效果
```

最後：

```
第三步：優化效能和無障礙性
```

### 3. 程式碼審查

```
審查這個 PR 的程式碼，從前端開發和效能優化的角度提供建議
```

### 4. 問題診斷

```
這個元件在行動裝置上顯示不正確，幫我找出問題並修復
```

## 最佳實踐

### 1. 明確的任務描述

❌ 不好的範例：
```
做一個按鈕
```

✅ 好的範例：
```
創建一個主要 CTA 按鈕元件，使用 Tailwind CSS，包含 hover 和 disabled 狀態，符合 WCAG AA 標準
```

### 2. 提供上下文

❌ 不好的範例：
```
這個不能用
```

✅ 好的範例：
```
#file:src/components/Modal.tsx 這個 Modal 元件在行動裝置上無法正確關閉，點擊背景時沒有反應
```

### 3. 分步驟處理複雜任務

❌ 不好的範例：
```
建立一個完整的電商網站
```

✅ 好的範例：
```
第一步：建立產品列表頁面的基本佈局和元件結構
```

### 4. 利用專案知識

```
@workspace 根據現有的程式碼風格和架構，建議如何實作新的功能
```

## 常見使用情境

### 情境 1: 新功能開發

```
我需要在應用程式中添加一個即時通知系統。請：
1. 建議技術方案（WebSocket vs SSE）
2. 設計 UI 元件
3. 提供實作步驟
```

### 情境 2: Bug 修復

```
#file:src/utils/api.ts 這個 API 呼叫在某些情況下會失敗，
請幫我找出問題並提供更健壯的錯誤處理方案
```

### 情境 3: 效能優化

```
@workspace 分析整個應用程式的效能瓶頸，
特別是首次載入時間和互動響應速度
```

### 情境 4: 重構

```
#file:src/components/Dashboard.tsx 這個元件太大了，
請建議如何拆分成更小、更可維護的元件
```

### 情境 5: 文件撰寫

```
為 #file:src/hooks/useAuth.ts 撰寫完整的 JSDoc 文件和使用範例
```

## 與 Claude Code 的差異

| 功能 | Claude Code | VS Code Copilot |
|------|-------------|-----------------|
| **Agent 觸發** | 自動根據 YAML 描述和範例 | 透過對話上下文和指令 |
| **多 Agent 協作** | 原生支援，可自動切換 | 需要在對話中明確引導 |
| **工具存取** | 明確定義 (Write, Read, MultiEdit, Bash, Grep, Glob) | 使用 VS Code 內建 API |
| **視覺識別** | 支援顏色標記 | 不支援 |
| **檔案操作** | 可直接讀寫檔案 | 透過建議和程式碼區塊 |
| **上下文管理** | 自動管理 agent 上下文 | 需要使用 @workspace, #file 等 |

## 疑難排解

### 問題 1: Agent 指令沒有生效

**解決方案：**
1. 確認檔案放在正確位置
2. 重新載入 VS Code 視窗
3. 檢查檔案格式是否正確（Markdown）

### 問題 2: 回應不符合預期

**解決方案：**
1. 提供更明確的任務描述
2. 使用 @workspace 或 #file 提供更多上下文
3. 在對話中明確提到你想要的專業領域

### 問題 3: 多個 Agent 衝突

**解決方案：**
1. 將不同領域的 agents 分開使用
2. 在對話中明確指定你需要哪個領域的專業知識
3. 考慮為不同專案使用不同的 agent 組合

## 自訂 Agents

### 修改現有 Agent

1. 編輯對應的 `.md` 檔案
2. 調整系統提示詞以符合你的需求
3. 添加團隊特定的最佳實踐
4. 重新載入 VS Code

### 創建新 Agent

1. 複製現有 agent 作為模板
2. 修改標題和概述
3. 更新核心職責和專業領域
4. 添加具體的回應格式指南
5. 測試並迭代

## 效能追蹤

建議追蹤以下指標來評估 agent 效果：

- **開發速度**：完成任務所需時間
- **程式碼品質**：bug 數量、可維護性
- **學習曲線**：新團隊成員上手速度
- **滿意度**：開發者使用體驗

## 進一步資源

- [GitHub Copilot 官方文件](https://docs.github.com/en/copilot)
- [VS Code Copilot Chat](https://code.visualstudio.com/docs/copilot/copilot-chat)
- [Copilot 最佳實踐](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)
