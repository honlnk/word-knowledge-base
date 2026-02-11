# 模板使用说明（AI 友好版本）

本文件夹包含英语单词知识库的所有模板。这些模板使用**注释指令**而非 Templater 动态语法，更适合 AI 辅助编写。

## 📁 模板列表

### 单词笔记模板

1. **word-note.md** - 普通单词笔记（单发音）
   - 适用场景：大部分单词
   - 特点：单一发音、单一词性或多个词性
   - 使用频率：⭐⭐⭐⭐⭐

2. **word-note-heteronym.md** - 异读词笔记（多发音）
   - 适用场景：异读词（拼写相同但发音/含义不同）
   - 特点：多个发音、每个含义独立章节
   - 使用频率：⭐⭐⭐

### 词素笔记模板

3. **prefix-note.md** - 前缀笔记
   - 适用场景：前缀（如 re-, pre-, per-）
   - 特点：多个核心含义、含义对比、前缀关系对比
   - 使用频率：⭐⭐⭐⭐

4. **suffix-note.md** - 后缀笔记
   - 适用场景：后缀（如 -ion, -ment, -ness）
   - 特点：形式多样性、使用条件、判断技巧
   - 使用频率：⭐⭐⭐⭐

5. **root-note.md** - 词根笔记
   - 适用场景：词根（如 mit-/miss-, ten-）
   - 特点：词根变化规律、完整词族、构词分析
   - 使用频率：⭐⭐⭐⭐

---

## 🎯 设计理念

### 为什么不用 Templater 动态语法？

| 方面 | Templater 模板 | AI 友好模板 |
|:-----|:----------------|:-----------|
| **自动化** | ✅ 高度自动化 | ❌ 需要手动填写 |
| **AI 理解** | ❌ 需要理解 Templater 语法 | ✅ 直接理解注释 |
| **人类使用** | ⚠️ 需要运行模板 | ✅ 复制粘贴即可 |
| **灵活性** | ❌ 语法固定 | ✅ 可自由调整 |
| **维护性** | ❌ 需要理解代码 | ✅ 注释清晰 |

### 核心设计原则

1. **分离规则与数据**：
   - 详细 AI 生成规则放在 YAML 之外（HTML 注释）
   - YAML 内部只保留简洁的内联注释
   - 生成笔记时可以去掉外部规则，保持 YAML 整洁

2. **真实示例数据**：
   - 使用现有笔记的真实数据作为示例
   - 不使用 `placeholder` 或 `___` 占位符
   - AI 可以直接参考示例的结构和格式

3. **结构清晰**：
   - 章节结构固定，内容可变
   - YAML 字段格式标准化
   - 支持嵌套结构（如 related_words）

4. **AI 友好**：
   - HTML 注释清晰易懂
   - 注释包含字段格式、可选值、示例
   - AI 能理解规则并生成符合标准的内容

---

## 📖 模板结构说明

### 整体结构（方案A：AI 友好版本）

```
<!--
=====================================================================
AI 生成规则：[笔记类型]（word-note.md / prefix-note.md 等）
=====================================================================

详细规则部分（HTML注释形式）：
- 基本信息：各字段的含义和格式要求
- 标签：必选/可选标签列表
- 关联词：related_words 子字段说明
- 正文结构：必选/可选章节说明

=====================================================================
-->

---
# word: 单词名称（示例数据）
# pronunciation: /发音/（示例数据）
# part_of_speech: 词性（示例数据）
# etymology: 词源（示例数据）
tags:
  - vocabulary
  - # optional-tag  # 简洁注释
related_words:
  forms:              # 词形变化（简洁注释）
    - example_word    # 真实示例数据
    - another_example
  synonyms:           # 同义词（简洁注释）
    - example_synonym
created: 2026-01-31
next_review: 2026-02-14
---

# Markdown 正文内容（包含真实示例）
...

---

### 正文部分

#### 章节结构

所有模板遵循以下章节结构：

**必选章节**：
- 基本信息
- 核心含义 / 核心含义（多个）
- 词源分析 / 词根变化 / 完整词族

**可选章节**：
- 记忆技巧
- 常用搭配
- 练习与自测
- 学习笔记
- 相关链接
- 参考来源

#### 特殊章节（按类型）

**前缀专用**：
- 含义对比与区分
- 与其他前缀对比
- 特殊用法与例外

**后缀专用**：
- 三种形式的区别（如果有多个形式）
- 使用条件
- 判断技巧
- 发音规律

**词根专用**：
- 拉丁语/希腊语动词变位表
- 完整词族列表（按前缀分类）

**异读词专用**：
- 每个含义使用独立的 `## 📖 含义X` 标题
- 包含发音与词性、核心含义

---

## 🚀 使用方法

### 方法1：手动创建（推荐）

1. **复制模板内容**：
   ```bash
   cp templates/word-note.md word-storage/new-word.md
   ```

2. **重命名文件**：
   - 单词：`required.md`
   - 前缀：`re-.md`（注意末尾的 `-`）
   - 后缀：`-ion.md`（注意开头的 `-`）
   - 词根：`mit-miss.md`（多个变体用 `-` 连接）

3. **编辑文件**：
   - 按照 YAML 注释填写字段
   - 替换 `___` 标记的内容
   - 编辑正文章节

### 方法2：AI 辅助生成（最推荐）

直接告诉 AI：

```
请使用 templates/word-note.md 模板生成单词 "required" 的笔记。
发音：/rɪˈkwaɪəd/
词性：adjective
词源：requaerere (Latin)
```

AI 会：
1. 读取模板的注释规则
2. 理解字段格式要求
3. 生成符合标准的完整笔记

---

## 📝 填写指南

### YAML 字段填写

#### word / prefix / suffix / root

- **自动获取**：这些字段应该自动从文件名获取
- 无需手动填写

#### pronunciation

- **格式**：`/IPA发音/`（用斜杠包围）
- **来源**：从 Cambridge Dictionary、Oxford Dictionary 等词典复制
- **示例**：`/rɪˈkwaɪəd/`

#### part_of_speech

- **可选值**：`noun`, `verb`, `adjective`, `adverb`, `pronoun`, `preposition`, `conjunction`, `interjection`
- **多词性**：用 `&` 或 `,` 连接（如 `noun & adjective`）

#### etymology / origin

- **格式**：`源单词 (语言)`
- **示例**：
  - 单词：`requaerere (Latin)`
  - 前缀：`per (Latin)`
  - 后缀：`-ionem (Latin)`
  - 词根：`mittere (Latin)`

#### tags

- **必选**：
  - 单词：`vocabulary`
  - 前缀：`prefix`
  - 后缀：`suffix`
  - 词根：`word-root`

- **可选**（按需添加）：
  - `heteronym`（异读词）
  - `confusion-prone`（易混淆词）
  - `technical-terms`（技术术语）
  - `not-a-prefix-word`（假前缀词）
  - `highly-productive`（高产词素）
  - `etymology`（包含详细词源）
  - `latin-root`（拉丁语词根）
  - `greek-root`（希腊语词根）
  - `noun-formation`（名词构成）
  - `adjective-formation`（形容词构成）

#### related_words（嵌套结构）

```yaml
related_words:
  forms:              # 词形变化
    - require
    - requirement
  synonyms:           # 同义词
    - necessary
    - mandatory
  antonyms:            # 反义词
    - optional
  confusions:          # 易混淆词
    - standard
    - request
  same_root:           # 同词根
    - query
    - question
    - quest
  derivatives:         # 派生词
    - contentment
```

**子字段按需添加**，不需要的可以留空或不写。

#### created / next_review

- **格式**：`YYYY-MM-DD`
- **created**：笔记创建日期
- **next_review**：下次复习时间（建议 created + 14天）

---

## 🎨 占位符说明

### `___` 标记

表示需要填写的内容：

```yaml
pronunciation: /___IPA发音___/
```

填写后：
```yaml
pronunciation: /rɪˈkwaɪəd/
```

### `#` 注释标签

表示可选的字段：

```yaml
tags:
  - vocabulary
  - # confusion-prone  # 取消注释即可使用
```

---

## ✅ 质量检查清单

创建新笔记后，请确认：

### YAML 字段检查

- [ ] word/prefix/suffix/root 已正确填写
- [ ] pronunciation 格式正确（`/发音/`）
- [ ] part_of_speech 使用了标准值
- [ ] etymology 使用详细格式（`单词 (语言)`）
- [ ] tags 至少包含一个分类标签（vocabulary/prefix/suffix/word-root）
- [ ] related_words 按需填写子字段
- [ ] created 和 next_review 日期已填写

### 文件命名检查

- [ ] 单词：`word.md`
- [ ] 前缀：末尾有 `-`（如 `re-.md`）
- [ ] 后缀：开头有 `-`（如 `-ion.md`）
- [ ] 词根：多个变体用 `-` 连接（如 `mit-miss.md`）

### 正文内容检查

- [ ] 包含基本信息章节
- [ ] 包含核心含义章节
- [ ] 包含词源分析章节
- [ ] 一词多义使用独立 ## 标题
- [ ] 相关链接已添加
- [ ] 参考来源已添加

---

## 🔗 相关文档

- [[../format-standard]] - 完整的格式标准文档
- [[../tags-standard]] - 标签标准化定义

---

## 💡 常见问题

### Q1: 为什么不使用 Templater 动态语法？

**A**: 因为大多数笔记将由 AI 生成，Templater 语法会增加 AI 的理解难度。使用注释指令更直接、更清晰。

### Q2: 如何让 AI 使用这些模板？

**A**: 直接告诉 AI 使用模板即可：
```
请使用 templates/word-note.md 模板为单词 "xxx" 生成笔记，
发音是 /xxx/，词性是 xxx，词源是 xxx (xxx)
```

### Q3: `___` 占位符需要手动替换吗？

**A**: 是的，或者在 AI 生成时直接告诉 AI 替换这些占位符。

### Q4: 可选标签（用 `#` 注释的）如何使用？

**A**: 取消注释即可：
```yaml
tags:
  - vocabulary
  - confusion-prone  # 删除行首的 # -
```

### Q5: 相关词的所有子字段都要填写吗？

**A**: 不需要，按需填写。如果某个子字段不适用，可以留空或不写该子字段。

---

**最后更新**: 2026-01-31
**版本**: AI 友好版本 v1.0
