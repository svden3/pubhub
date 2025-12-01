# 代码与文档风格指南

本指南规范项目中所有代码、脚本、文档的格式和风格。

---

## 📁 文件命名规范

### Markdown 文件
```
每日笔记:   YYYY-MM-DD.md          (如: 2025-11-29.md)
周总结:     YYYY-MM-WN.md          (如: 2025-11-W1.md, N为周数)
月报告:     YYYY-MM.md             (如: 2025-11.md)
书稿草稿:   书名-章节-vX.Y.md      (如: 孙子-始计篇-v1.0.md)
```

### 脚本文件
```
JavaScript:  kebab-case.js         (如: daily-template.js)
Python:      snake_case.py         (如: generate_pdf.py)
Shell:       kebab-case.sh         (如: backup-to-cloud.sh)
```

### 配置文件
```
JSON:        kebab-case.json       (如: settings.json, package.json)
YAML:        kebab-case.yml        (如: weekly-summary.yml)
```

---

## 📝 Markdown 文档规范

### 标题层级
```markdown
# 一级标题 (文档标题，每个文档只有1个)

## 二级标题 (主要章节)

### 三级标题 (子章节)

#### 四级标题 (最多用到这一级)
```

**禁止**:
- ❌ 跳级使用标题（如从 # 直接跳到 ###）
- ❌ 使用五级标题及以下

### 列表格式

**无序列表**:
```markdown
- 第一项
- 第二项
  - 子项（两个空格缩进）
  - 子项
- 第三项
```

**有序列表**:
```markdown
1. 第一步
2. 第二步
3. 第三步
```

**任务列表**:
```markdown
- [ ] 未完成任务
- [x] 已完成任务
```

### 引用块
```markdown
> 单行引用

> **粗体标识**
> 多行引用第一行
> 多行引用第二行
```

### 代码块
````markdown
行内代码用单反引号: `npm run new-note`

代码块用三反引号:
```bash
git add .
git commit -m "message"
git push
```
````

**语言标识**（必须指定）:
- `bash` - Shell命令
- `javascript` - JavaScript代码
- `python` - Python代码
- `markdown` - Markdown示例
- `json` - JSON配置

### 表格格式
```markdown
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 数据1 | 数据2 | 数据3 |
| 数据4 | 数据5 | 数据6 |
```

**对齐方式**:
```markdown
| 左对齐 | 居中对齐 | 右对齐 |
|:-------|:--------:|-------:|
| 内容   |   内容   |   内容 |
```

### 链接格式

**内部链接**:
```markdown
[相对路径](../daily-notes/published/2025-11-29.md)
[绝对路径](/Users/jimxiao/ai/publisher/three-books-publishing/README.md)
```

**外部链接**:
```markdown
[OpenAI官网](https://openai.com)
[Anthropic官网](https://anthropic.com)
```

### 图片格式
```markdown
![替代文本](images/screenshot.png)
![来自URL的图片](https://example.com/image.png)
```

---

## 💻 JavaScript 代码规范

### 基本风格
```javascript
// 使用 const/let，不使用 var
const projectName = 'three-books-publishing';
let counter = 0;

// 函数命名：驼峰式
function generateDailyNote() {
  // 函数体
}

// 箭头函数
const processNotes = (notes) => {
  return notes.map(note => note.content);
};

// 对象和数组
const config = {
  minWords: 300,
  maxWords: 500,
  requiredSections: [
    '今日原文摘要',
    '我的理解与心得'
  ]
};
```

### 注释规范
```javascript
/**
 * 生成每日笔记模板
 * @param {string} date - 日期字符串 (YYYY-MM-DD)
 * @returns {string} 生成的Markdown内容
 */
function generateDailyTemplate(date) {
  // 实现细节...
}

// 单行注释：解释"为什么"而非"是什么"
// 计算本周起始日期（周一）
const monday = new Date(today);
monday.setDate(today.getDate() - dayOfWeek + 1);
```

### 错误处理
```javascript
// 使用 try-catch
try {
  const content = fs.readFileSync(filePath, 'utf-8');
  processContent(content);
} catch (error) {
  console.error(`错误：无法读取文件 ${filePath}`);
  console.error(error.message);
  process.exit(1);
}

// 提供清晰的错误消息
if (!fs.existsSync(outputDir)) {
  console.log('⚠️  输出目录不存在，正在创建...');
  fs.mkdirSync(outputDir, { recursive: true });
}
```

### 控制台输出
```javascript
// 使用emoji和颜色增强可读性
console.log('✅ 已生成今日笔记模板');
console.log('⚠️  警告：文件已存在');
console.log('❌ 错误：无法找到文件');

// 提供清晰的下一步指引
console.log('📝 接下来请:');
console.log('   1. 打开生成的文件');
console.log('   2. 填写心得（300-500字）');
console.log('   3. 运行: git commit');
```

---

## 🔧 Git 提交规范

### 提交消息格式
```
<emoji> <类型>: <简短描述>

<详细说明>（可选）

<Footer>（可选）
```

### Emoji 使用规范
```
📝  Daily note     - 每日笔记
📊  Weekly summary - 周总结
📖  Monthly report - 月报告
🔧  System update  - 系统更新
✨  New feature    - 新功能
🐛  Bug fix        - 修复bug
📚  Documentation  - 文档更新
♻️  Refactor       - 代码重构
🎨  Style          - 格式/样式调整
✅  Tests          - 测试相关
⬆️  Dependencies   - 依赖更新
🎉  Initial commit - 初始提交
```

### 示例
```bash
# 好的提交消息
git commit -m "📝 Daily note: 2025-11-29"

git commit -m "✨ Add AI strategist agent

- 创建 /ai-parallels 命令
- 添加2025-2035年AI案例库
- 整合到主工作流"

# 不好的提交消息
git commit -m "update"              # 太简略
git commit -m "修复了一些bug"       # 不具体
git commit -m "添加了很多新功能..."  # 太宽泛
```

### 提交频率
- ✅ 每篇笔记完成后立即提交
- ✅ 每个功能开发完成后提交
- ✅ 每次重要修改后提交
- ❌ 不要积累太多更改后才提交

### 必须包含的Footer
```bash
git commit -m "📝 Daily note: 2025-11-29

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"
```

---

## 📋 YAML 配置文件规范

### GitHub Actions 工作流
```yaml
name: 每周自动生成周总结草稿  # 清晰的名称

on:
  schedule:
    - cron: '0 0 * * 6'  # 注释说明时间
  workflow_dispatch:      # 允许手动触发

jobs:
  generate-weekly-summary:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository  # 每步都有清晰的名称
        uses: actions/checkout@v4
```

### 缩进规范
- 使用2个空格缩进
- 不使用Tab

---

## 📦 JSON 配置文件规范

### package.json
```json
{
  "name": "three-books-publishing",
  "version": "1.0.0",
  "description": "7年三书精读出版系统",
  "scripts": {
    "new-note": "node scripts/daily-template.js",
    "weekly-summary": "node scripts/weekly-summary.js"
  },
  "private": true
}
```

**规范**:
- 使用2个空格缩进
- 键名使用双引号
- 最后一个元素后不加逗号

### .claude/settings.json
```json
{
  "projectName": "Three Books Publishing System",
  "version": "1.0.0",
  "contextRules": {
    "projectContext": [
      "这是一个7年项目"
    ]
  }
}
```

---

## 📖 文档结构模板

### README 文档
```markdown
# 项目标题

一句话简介

## 目录（可选，长文档必需）

- [快速开始](#快速开始)
- [功能特性](#功能特性)
- [使用指南](#使用指南)

## 快速开始

...

## 功能特性

...

## 许可证

...
```

### API 文档
```markdown
# API 文档

## `functionName(param1, param2)`

**描述**: 函数功能简介

**参数**:
- `param1` (string): 参数1说明
- `param2` (number): 参数2说明

**返回值**: 返回值说明

**示例**:
```javascript
const result = functionName('value', 42);
```

**注意事项**: 特殊情况说明
```

---

## 🎨 格式化工具推荐

### Markdown
- **Prettier**: VS Code扩展，自动格式化
- **markdownlint**: 检查Markdown规范

### JavaScript
- **Prettier**: 代码格式化
- **ESLint**: 代码质量检查

### Git
- **husky**: Git钩子，提交前检查
- **commitlint**: 提交消息格式检查

---

## ✅ 检查清单

### 提交前检查
- [ ] 所有Markdown文件格式正确？
- [ ] 代码有适当注释？
- [ ] Git提交消息符合规范？
- [ ] 没有遗留调试代码？
- [ ] 文件命名符合规范？

### 发布前检查
- [ ] 所有链接有效？
- [ ] 图片能正常显示？
- [ ] 代码块有语言标识？
- [ ] 表格格式正确？
- [ ] 拼写检查通过？

---

**一致的风格让项目更专业，更易维护。**

参考:
- `.claude/settings.json` - 项目配置
- `.claude/CONTENT_RULES.md` - 内容规则
- `.claude/prompts/system-context.md` - 系统上下文
