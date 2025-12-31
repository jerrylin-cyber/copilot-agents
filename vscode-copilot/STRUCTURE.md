# VS Code Copilot Agents 結構說明

## 目錄結構

所有 agents 按照功能分類組織，保持與原始 Claude Code agents 相同的結構：

```
vscode-copilot/
├── engineering/          # 工程開發 (7 個)
├── design/              # 設計 (5 個)
├── marketing/           # 行銷 (7 個)
├── product/             # 產品 (3 個)
├── project-management/  # 專案管理 (3 個)
├── studio-operations/   # 營運 (5 個)
├── testing/             # 測試 (5 個)
└── bonus/               # 額外 (2 個)
```

## 檔案格式

每個 agent 檔案都包含：

### YAML Frontmatter
```yaml
---
name: agent-name
description: Agent 的描述和使用情境
---
```

### 系統提示詞
完整的 agent 專業知識、職責和最佳實踐

### 回應格式指南
標準化的回應流程指引

## 與 Claude Code 的差異

### 保留的內容
- ✅ `name` metadata
- ✅ `description` metadata（已清理 XML 標籤）
- ✅ `tools` metadata（供參考，VS Code Copilot 使用內建工具）
- ✅ `color` metadata（供參考，VS Code Copilot 不顯示顏色）
- ✅ 完整的系統提示詞
- ✅ 所有專業知識和最佳實踐

### 移除的內容
- ❌ XML 格式的範例標籤（`<example>`, `<commentary>`）

### 新增的內容
- ✅ 標準化的回應格式指南
- ✅ 每個目錄的 README.md 索引檔案

## 使用方式

### 1. 單一 Agent
```bash
# 複製單一 agent
cp vscode-copilot/engineering/frontend-developer.md .github/copilot-instructions.md
```

### 2. 多個 Agents
```bash
# 合併多個 agents
cp vscode-copilot/engineering/frontend-developer.md .github/copilot-instructions.md
cat vscode-copilot/design/ui-designer.md >> .github/copilot-instructions.md
cat vscode-copilot/engineering/test-writer-fixer.md >> .github/copilot-instructions.md
```

### 3. 整個類別
```bash
# 複製整個類別的所有 agents
cat vscode-copilot/engineering/*.md > .github/copilot-instructions.md
```

### 4. 使用安裝腳本
```bash
# 互動式安裝
./install-vscode-agents.sh

# 指定預設組合
./install-vscode-agents.sh --project --frontend
./install-vscode-agents.sh --project --fullstack
./install-vscode-agents.sh --project --design
./install-vscode-agents.sh --project --marketing
```

## 目錄索引

每個目錄都包含一個 `README.md` 檔案，列出該類別的所有 agents：

- [engineering/README.md](engineering/README.md)
- [design/README.md](design/README.md)
- [marketing/README.md](marketing/README.md)
- [product/README.md](product/README.md)
- [project-management/README.md](project-management/README.md)
- [studio-operations/README.md](studio-operations/README.md)
- [testing/README.md](testing/README.md)
- [bonus/README.md](bonus/README.md)

## Metadata 說明

### name
Agent 的唯一識別符，使用 kebab-case 格式。

範例：
```yaml
name: frontend-developer
name: ui-designer
name: content-creator
```

### description
Agent 的描述，說明何時使用此 agent 以及其專長領域。

範例：
```yaml
description: Use this agent when building user interfaces, implementing React/Vue/Angular components, handling state management, or optimizing frontend performance. This agent excels at creating responsive, accessible, and performant web applications.
```

### tools
Agent 可以使用的工具列表（保留自 Claude Code，供參考）。

常見工具：
- `Write` - 寫入檔案
- `Read` - 讀取檔案
- `MultiEdit` - 批次編輯
- `Bash` - 執行命令
- `Grep` - 搜尋內容
- `Glob` - 檔案匹配
- `WebSearch` - 網路搜尋
- `WebFetch` - 獲取網頁內容

範例：
```yaml
tools: Write, Read, MultiEdit, Bash, Grep, Glob
```

**注意**：VS Code Copilot 使用自己的內建工具系統，此欄位主要供參考和文件用途。

### color
Agent 的視覺識別顏色（保留自 Claude Code，供參考）。

範例：
```yaml
color: blue
color: magenta
color: cyan
```

**注意**：VS Code Copilot 目前不支援顏色標記，此欄位主要供參考和文件用途。

## 轉換品質保證

### ✅ 已驗證
- 所有 37 個 agents 成功轉換
- YAML frontmatter 格式正確
- Metadata 完整保留（name, description, tools, color）
- 系統提示詞內容完整
- 目錄結構與原始相同
- 所有檔案使用 UTF-8 編碼

### 📊 轉換統計
- **總 Agents**: 37
- **成功率**: 100%
- **保留 Metadata**: name, description, tools, color
- **移除內容**: XML 範例標籤
- **新增內容**: 回應格式指南、目錄索引

## 最佳實踐

### 選擇 Agents
1. **專案初期**：選擇核心開發 agents（frontend, backend）
2. **功能開發**：根據需求添加特定 agents（ui-designer, content-creator）
3. **優化階段**：添加測試和效能 agents（test-writer-fixer, performance-benchmarker）

### 組合建議

**獨立開發者**（3-4 個）：
- frontend-developer
- ui-designer
- rapid-prototyper

**小型團隊**（5-7 個）：
- frontend-developer
- backend-architect
- ui-designer
- content-creator
- growth-hacker

**完整團隊**（10+ 個）：
- 所有 engineering agents
- 所有 design agents
- 選擇性的 marketing 和 operations agents

### 效能考量
- 每個 agent 檔案約 5-15 KB
- 建議同時使用不超過 10 個 agents
- 過多的 agents 可能影響 Copilot 的回應品質

## 維護與更新

### 更新 Agent
1. 編輯對應的 `.md` 檔案
2. 保持 YAML frontmatter 格式
3. 重新安裝到專案

### 添加新 Agent
1. 在適當的目錄創建新檔案
2. 使用現有 agent 作為模板
3. 包含完整的 YAML frontmatter
4. 更新目錄的 README.md

### 版本控制
建議將 `.github/copilot-instructions.md` 加入版本控制：
```bash
git add .github/copilot-instructions.md
git commit -m "Add Copilot agents configuration"
```

## 疑難排解

### 問題：Metadata 沒有被識別
**解決方案**：
- 確認 YAML frontmatter 格式正確（三個破折號）
- 檢查檔案編碼為 UTF-8
- 重新載入 VS Code 視窗

### 問題：找不到特定 Agent
**解決方案**：
- 檢查 agent 名稱拼寫
- 確認 agent 在正確的目錄中
- 使用 `find vscode-copilot -name "*.md"` 列出所有 agents

### 問題：多個 Agents 衝突
**解決方案**：
- 選擇互補而非重疊的 agents
- 在提示中明確指定需要的專業領域
- 考慮為不同專案使用不同的 agent 組合

## 進一步資源

- [README.md](README.md) - 主要說明文件
- [QUICK_START.md](QUICK_START.md) - 快速開始指南
- [USAGE_GUIDE.md](USAGE_GUIDE.md) - 完整使用指南
- [CONVERSION_NOTES.md](CONVERSION_NOTES.md) - 轉換技術說明
- [SUMMARY.md](SUMMARY.md) - 轉換總結

---

**最後更新**: 2025-12-31  
**版本**: 1.0.0  
**總 Agents**: 37  
**目錄數**: 8
