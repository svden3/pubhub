# Claude 配置系统说明

本目录包含所有 Claude Code AI 辅助的配置和规则，确保 AI 始终以最高质量标准协助项目。

---

## 📁 目录结构

```
.claude/
├── README.md                    # 本文件：配置系统说明
├── settings.json                # 项目核心配置
├── CONTENT_RULES.md            # 内容质量规则
├── STYLE_GUIDE.md              # 代码与文档风格指南
├── commands/                   # AI Agent 命令
│   ├── master-editor.md        # Agent 1: 总编辑
│   ├── annotate.md             # Agent 2: 注疏师
│   ├── ai-parallels.md         # Agent 3: AI战略家
│   ├── proofread.md            # Agent 4: 校对神
│   └── publish.md              # Agent 5: 出书总管
└── prompts/                    # 自定义提示词
    └── system-context.md       # 系统上下文（自动注入）
```

---

## 🎯 配置文件说明

### 1. `settings.json` - 项目核心配置

**作用**: 定义项目的全局配置、上下文规则、AI行为规范

**关键配置**:
- **projectContext**: 7年项目背景、三本书的权威版本
- **aiEraMapping**: 2025-2035年AI时代关键事件和玩家
- **writingStandards**: 每日笔记、周总结、月报告的质量标准
- **agentBehaviorRules**: 5个AI Agent的具体行为规范
- **forbiddenPatterns**: 禁止的语言和内容模式
- **qualityChecklist**: 发布前质量检查清单

**使用方式**:
```javascript
// Node.js脚本中读取配置
const settings = require('../.claude/settings.json');
const minWords = settings.writingStandards.dailyNote.minWords;
```

---

### 2. `CONTENT_RULES.md` - 内容质量规则

**作用**: 详细的内容创作规范，确保所有输出符合最高质量标准

**核心内容**:
- ✅ 4大核心原则（深度优先、原文为本、古今贯通、学术严谨）
- ✅ 每日笔记、周总结、月报告的详细标准
- ✅ 禁止清单（空洞溢美词、AI腔调、虚构事实）
- ✅ 发布前质量检查清单（基础、内容、风格、价值）
- ✅ 优秀案例和反面教材

**使用方式**:
- 写作前阅读相关章节
- 使用 `/master-editor` 时自动参考
- 定期复习确保内容质量提升

---

### 3. `STYLE_GUIDE.md` - 代码与文档风格指南

**作用**: 统一项目中所有代码、脚本、文档的格式和风格

**核心内容**:
- 📁 文件命名规范（Markdown、脚本、配置）
- 📝 Markdown文档规范（标题、列表、引用、代码块）
- 💻 JavaScript代码规范（风格、注释、错误处理）
- 🔧 Git提交规范（消息格式、emoji使用）
- 📋 YAML/JSON配置文件规范

**使用方式**:
- 创建新文件时参考命名规范
- 提交代码前检查风格一致性
- 配置编辑器使用Prettier自动格式化

---

### 4. `prompts/system-context.md` - 系统上下文

**作用**: 为所有AI Agent提供项目背景，自动注入到对话中

**核心内容**:
- 📚 项目概览（7年计划、2557天）
- 📖 三本书的权威版本和核心关注点
- 🤖 AI时代背景（主要玩家、关键战场、里程碑事件）
- 🎯 AI行为规范（核心原则、禁止行为、引用规范）
- ✅ 质量标准和特殊指令

**使用方式**:
- 自动加载到所有 `/` 命令中
- 确保AI始终理解项目上下文
- 定期更新AI事件库（新增真实案例）

---

### 5. `commands/` - AI Agent 命令

**5个专业AI Agent**:

#### Agent 1: `/master-editor` - 总编辑
- **任务**: 分析和分类每日笔记，评估质量，提供改进建议
- **输出**: 内容分类、质量评分（1-5分）、改进建议、标签推荐
- **规则**: 客观评估，不过度夸赞，具体可执行

#### Agent 2: `/annotate` - 注疏师
- **任务**: 提供历代注疏、中英对照、关键词解析
- **输出**: 权威原文、历代注疏精华、关键词解析、历史背景
- **规则**: 引用必须可查证，不可杜撰注疏

#### Agent 3: `/ai-parallels` - AI战略家
- **任务**: 将经典智慧映射到2025-2035年AI战例
- **输出**: 核心战略原则、AI时代案例映射、战略推演、实践启示
- **规则**: 只使用真实AI事件，提供时间和来源

#### Agent 4: `/proofread` - 校对神
- **任务**: 中英双语润色、逻辑检查、引文核对
- **输出**: 润色建议、逻辑问题、引文核对、格式问题、最终修改稿
- **规则**: 保持作者原有语言风格，严格核对事实

#### Agent 5: `/publish` - 出书总管
- **任务**: 生成周报、月报、年度书稿
- **输出**: 整合所有素材，发现内在逻辑，生成可出版内容
- **规则**: 注重内在逻辑而非简单拼接，质量优先于数量

---

## 🚀 使用指南

### 日常工作流中使用AI Agent

**第1步：写初稿**
```bash
npm run new-note
# 自己先写一个初稿（300-500字）
```

**第2步：使用总编辑分析**
```
在 Claude Code 中运行：
/master-editor

然后粘贴你的笔记，获取：
- 质量评分（各项1-5分）
- 改进建议（3-5条具体建议）
- 标签推荐
```

**第3步：使用注疏师补充深度**
```
/annotate

告诉AI你需要注疏的章节，获取：
- 权威原文（中英对照）
- 历代注疏精华（可查证）
- 关键词解析
```

**第4步：使用AI战略家映射现代**
```
/ai-parallels

提供你的笔记，AI会：
- 提炼永恒战略原则
- 找到2025年真实AI案例
- 推演未来3-10年
```

**第5步：使用校对神润色**
```
/proofread

提供修改后的笔记，AI会：
- 润色语言（保持你的风格）
- 检查逻辑
- 核对引文
- 规范格式
```

**第6步：发布**
```bash
mv daily-notes/drafts/今天.md daily-notes/published/
git add .
git commit -m "📝 Daily note: 今天"
git push
```

---

### 每周/每月使用出书总管

**生成周总结**:
```
/publish --type weekly

AI会：
1. 读取本周所有已发布笔记
2. 提炼核心主题
3. 精选金句
4. 发现跨书关联
5. 生成1000-2000字周总结草稿
```

**生成月报告**:
```
/publish --type monthly

AI会：
1. 读取本月所有周总结
2. 生成5000字月度专章
3. 三书合论（最重要！）
4. 个人成长反思
```

---

## 🔧 配置更新指南

### 何时更新配置？

**每月更新** (`settings.json`):
- 添加新的真实AI事件到 `aiEraMapping.keyThemes`
- 更新进度里程碑

**每季度更新** (`CONTENT_RULES.md`):
- 根据写作经验调整质量标准
- 添加新的优秀案例和反面教材

**每年更新** (`system-context.md`):
- 更新AI时代背景（新玩家、新战场）
- 补充里程碑事件库

### 如何更新配置？

1. 直接编辑相应的 `.md` 或 `.json` 文件
2. 提交更改：
```bash
git add .claude/
git commit -m "🔧 Update Claude configuration: 简短说明"
git push
```

---

## 📊 配置验证

### 检查配置完整性

```bash
# 验证JSON格式
node -e "console.log(JSON.parse(require('fs').readFileSync('.claude/settings.json')))"

# 检查所有必需文件
ls -la .claude/
ls -la .claude/commands/
ls -la .claude/prompts/
```

### 验证AI Agent工作

在Claude Code中依次运行：
```
/master-editor
/annotate
/ai-parallels
/proofread
/publish
```

如果所有命令都能正常显示提示词，说明配置正确。

---

## 🎓 进阶技巧

### 1. 自定义Agent

复制现有Agent命令，修改为你的需求：
```bash
cp .claude/commands/master-editor.md .claude/commands/my-agent.md
# 编辑 my-agent.md
```

在Claude Code中运行：
```
/my-agent
```

### 2. 创建项目特定提示词

在 `.claude/prompts/` 下创建新的提示词文件：
```bash
echo "你的自定义提示词" > .claude/prompts/custom-prompt.md
```

### 3. 批量处理

创建脚本批量调用AI：
```javascript
// scripts/batch-process.js
const { exec } = require('child_process');

// 读取所有未处理的笔记
// 逐个调用 /master-editor
// 保存分析结果
```

---

## 🚨 常见问题

### Q: Agent命令不工作？
A: 确保 `.claude/commands/` 目录存在，文件名正确（`*.md`），在Claude Code中输入 `/` 应该能看到所有命令。

### Q: AI没有遵守规则？
A: 在对话中明确引用规则，如"请按照 `.claude/CONTENT_RULES.md` 中的标准评估"。

### Q: 如何让AI记住项目上下文？
A: `system-context.md` 会自动注入，也可以在每次对话开始时手动引用。

### Q: 配置文件太长，AI读不完？
A: 将长配置拆分为多个小文件，只在需要时引用特定部分。

---

## 📚 相关文档

- [GET_STARTED.md](../GET_STARTED.md) - 系统启动指南
- [QUICK_START.md](../QUICK_START.md) - 快速上手
- [README.md](../README.md) - 项目概览
- [DEPLOYMENT_REPORT.md](../DEPLOYMENT_REPORT.md) - 部署报告

---

## 🎯 配置哲学

这套配置系统的核心理念：

1. **质量至上**: 宁缺毋滥，每篇输出都是精品
2. **规则明确**: AI和人都遵守同样的高标准
3. **持续改进**: 配置随着项目演进而升级
4. **可追溯**: 所有规则可查证，可复现

**记住**: 好的配置让AI成为7年旅程的可靠伙伴。

---

**版本**: v1.0.0
**最后更新**: 2025-11-29
**维护者**: Jim Xiao
