# VS Code Copilot Agents - 單檔案格式

這個資料夾包含所有 agents 的單檔案版本，使用 `.agent.md` 副檔名，方便直接使用。

## 📚 原始來源

這些 agents 轉換自 [Contains Studio AI Agents](https://github.com/contains-studio/agents)，原本為 Claude Code 格式，已轉換為 VS Code Copilot 兼容格式。

本專案維護於：
- **專案網址**: https://github.com/lazyjerry/vscode-copilot-agents
- **原始專案**: https://github.com/contains-studio/agents
- **授權**: 與原始專案相同
- **轉換日期**: 2025-12-31

## 檔案命名格式

```
copilot-{類別}-{agent名稱}.agent.md
```

例如：
- `copilot-engineering-frontend-developer.agent.md`
- `copilot-design-ui-designer.agent.md`
- `copilot-marketing-content-creator.agent.md`

## 使用方式

### 方法 1: 直接複製到專案

```bash
# 創建 agents 目錄
mkdir -p .github/agents

# 複製單一 agent
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/

# 或複製多個 agents
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/
cp vscode-copilot-agents/copilot-design-ui-designer.agent.md .github/agents/
```

### 方法 2: 使用符號連結

```bash
# 創建符號連結
mkdir -p .github/agents
ln -s ../../vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/agents/
```

### 方法 3: 使用安裝腳本

```bash
# 使用提供的安裝腳本
./install-vscode-agents.sh
```
```

## 檔案列表

### Engineering (7 個)
- `copilot-engineering-ai-engineer.agent.md`
- `copilot-engineering-backend-architect.agent.md`
- `copilot-engineering-devops-automator.agent.md`
- `copilot-engineering-frontend-developer.agent.md`
- `copilot-engineering-mobile-app-builder.agent.md`
- `copilot-engineering-rapid-prototyper.agent.md`
- `copilot-engineering-test-writer-fixer.agent.md`

### Design (5 個)
- `copilot-design-brand-guardian.agent.md`
- `copilot-design-ui-designer.agent.md`
- `copilot-design-ux-researcher.agent.md`
- `copilot-design-visual-storyteller.agent.md`
- `copilot-design-whimsy-injector.agent.md`

### Marketing (7 個)
- `copilot-marketing-app-store-optimizer.agent.md`
- `copilot-marketing-content-creator.agent.md`
- `copilot-marketing-growth-hacker.agent.md`
- `copilot-marketing-instagram-curator.agent.md`
- `copilot-marketing-reddit-community-builder.agent.md`
- `copilot-marketing-tiktok-strategist.agent.md`
- `copilot-marketing-twitter-engager.agent.md`

### Product (3 個)
- `copilot-product-feedback-synthesizer.agent.md`
- `copilot-product-sprint-prioritizer.agent.md`
- `copilot-product-trend-researcher.agent.md`

### Project Management (3 個)
- `copilot-project-management-experiment-tracker.agent.md`
- `copilot-project-management-project-shipper.agent.md`
- `copilot-project-management-studio-producer.agent.md`

### Studio Operations (5 個)
- `copilot-studio-operations-analytics-reporter.agent.md`
- `copilot-studio-operations-finance-tracker.agent.md`
- `copilot-studio-operations-infrastructure-maintainer.agent.md`
- `copilot-studio-operations-legal-compliance-checker.agent.md`
- `copilot-studio-operations-support-responder.agent.md`

### Testing (5 個)
- `copilot-testing-api-tester.agent.md`
- `copilot-testing-performance-benchmarker.agent.md`
- `copilot-testing-test-results-analyzer.agent.md`
- `copilot-testing-tool-evaluator.agent.md`
- `copilot-testing-workflow-optimizer.agent.md`

### Bonus (2 個)
- `copilot-bonus-joker.agent.md`
- `copilot-bonus-studio-coach.agent.md`

## 與 vscode-copilot/ 的差異

| 特性 | vscode-copilot/ | vscode-copilot-agents/ |
|------|-----------------|------------------------|
| **結構** | 按類別分資料夾 | 所有檔案在同一層 |
| **命名** | 原始名稱 | 包含類別前綴 |
| **副檔名** | `.md` | `.agent.md` |
| **索引** | 每個資料夾有 README | 單一 README |
| **用途** | 瀏覽和參考 | 直接使用 |

## 快速選擇指南

### 前端開發者
```bash
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-design-ui-designer.agent.md >> .github/copilot-instructions.md
```

### 全端開發者
```bash
cp vscode-copilot-agents/copilot-engineering-frontend-developer.agent.md .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-engineering-backend-architect.agent.md >> .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-engineering-devops-automator.agent.md >> .github/copilot-instructions.md
```

### 設計團隊
```bash
cp vscode-copilot-agents/copilot-design-ui-designer.agent.md .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-design-ux-researcher.agent.md >> .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-design-brand-guardian.agent.md >> .github/copilot-instructions.md
```

### 行銷團隊
```bash
cp vscode-copilot-agents/copilot-marketing-content-creator.agent.md .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-marketing-growth-hacker.agent.md >> .github/copilot-instructions.md
cat vscode-copilot-agents/copilot-marketing-tiktok-strategist.agent.md >> .github/copilot-instructions.md
```

## 搜尋和過濾

### 按類別列出
```bash
# 列出所有工程類 agents
ls vscode-copilot-agents/copilot-engineering-*.agent.md

# 列出所有設計類 agents
ls vscode-copilot-agents/copilot-design-*.agent.md
```

### 搜尋特定功能
```bash
# 搜尋包含特定關鍵字的 agents
grep -l "React" vscode-copilot-agents/*.agent.md

# 搜尋特定工具
grep -l "tools:.*Bash" vscode-copilot-agents/*.agent.md
```

## Metadata 格式

所有 agents 都包含完整的 metadata：

```yaml
---
name: frontend-developer
description: Use this agent when building user interfaces...
tools: Write, Read, MultiEdit, Bash, Grep, Glob
color: blue
---
```

詳細說明請參閱 [../vscode-copilot/METADATA.md](../vscode-copilot/METADATA.md)

## 更新和維護

這個資料夾的檔案是從 `vscode-copilot/` 複製而來。如果需要更新：

```bash
# 重新生成所有 .agent.md 檔案
rm -rf vscode-copilot-agents/*.agent.md

for dir in engineering design marketing product project-management studio-operations testing bonus; do
  for file in vscode-copilot/$dir/*.md; do
    if [ -f "$file" ] && [ "$(basename "$file")" != "README.md" ]; then
      filename=$(basename "$file" .md)
      newname="copilot-${dir}-${filename}.agent.md"
      cp "$file" "vscode-copilot-agents/$newname"
    fi
  done
done
```

## 相關文件

- [本專案](https://github.com/lazyjerry/vscode-copilot-agents) - VS Code Copilot Agents
- [原始專案](https://github.com/contains-studio/agents) - Contains Studio AI Agents
- [../vscode-copilot/README.md](../vscode-copilot/README.md) - 主要說明文件
- [../vscode-copilot/METADATA.md](../vscode-copilot/METADATA.md) - Metadata 說明
- [../vscode-copilot/QUICK_START.md](../vscode-copilot/QUICK_START.md) - 快速開始
- [../vscode-copilot/USAGE_GUIDE.md](../vscode-copilot/USAGE_GUIDE.md) - 使用指南
- [../DIRECTORY_STRUCTURE.md](../DIRECTORY_STRUCTURE.md) - 目錄結構說明

## 貢獻與回饋

如果你發現問題或有改進建議：
- 本專案 Issues: https://github.com/lazyjerry/vscode-copilot-agents/issues
- 本專案 Discussions: https://github.com/lazyjerry/vscode-copilot-agents/discussions
- 原始專案 Issues: https://github.com/contains-studio/agents/issues
- 原始專案 Discussions: https://github.com/contains-studio/agents/discussions

## 致謝

感謝 [Contains Studio](https://github.com/contains-studio) 創建和維護這些優秀的 AI agents。

---

**總檔案數**: 37  
**格式**: `.agent.md`  
**Metadata**: 完整保留  
**最後更新**: 2025-12-31
