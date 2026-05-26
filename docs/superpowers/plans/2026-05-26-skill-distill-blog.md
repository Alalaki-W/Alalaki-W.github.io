# Skill 蒸馏体验 + 博客记录 实现计划

> **面向 AI 代理的工作者：** 必需子技能：使用 superpowers:subagent-driven-development（推荐）或 superpowers:executing-plans 逐任务实现此计划。步骤使用复选框（`- [ ]`）语法来跟踪进度。

**目标：** 协助用户完成蒸馏 Skill 的安装与使用，全程记录到一篇 Hexo 博客文章，最终推送部署。

**架构：** 项目分为两条轨道——用户主导 Skill 实战（安装→选网红→蒸馏→出成果），AI 同步记录到 `source/_posts/` 下的单篇 Markdown 文章中。每完成一个项目阶段，填充对应章节。全部完成后 commit + push 触发 GitHub Actions 部署。

**技术栈：** Hexo 8.x, Bamboo 3.3.12, GitHub Pages, GitHub Actions

---

## 文件结构

| 文件 | 职责 | 操作 |
|------|------|------|
| `source/_posts/Skill-Distill-<target>.md` | 博客文章主体，渐进填充 | 创建 + 多次编辑 |
| （无其他文件变更） | — | — |

文章为唯一的交付物文件。文件命名中的 `<target>` 待蒸馏目标确定后替换。

---

### 任务 1：创建博客文章骨架

**文件：**
- 创建：`source/_posts/Skill-Distill-<target>.md`

- [ ] **步骤 1：确定文件名并创建骨架**

向用户确认蒸馏的 Skill 名称和目标网红后，确定最终文件名。先用占位名 `Skill-Distill-Project.md` 创建骨架：

```bash
npx hexo new post "Skill-Distill-Project"
```

- [ ] **步骤 2：写入文章 Front Matter 和章节框架**

编辑文件，填入 Front Matter（title/categories/tags 初始值，date 用当前日期）和五个章节标题（动机、环境准备、选定目标、蒸馏实战、成果与复盘），每个章节下暂写 `<!-- TODO -->` 占位。

```markdown
---
title: [待填充：项目名称]
date: 2026-05-26
categories: 技术
tags:
  - AI
  - Skill
  - 蒸馏
---

## 一、动机

<!-- TODO -->

## 二、环境准备

<!-- TODO -->

## 三、选定目标

<!-- TODO -->

## 四、蒸馏实战

<!-- TODO -->

## 五、成果与复盘

<!-- TODO -->
```

- [ ] **步骤 3：先不 commit**

骨架暂存，等待后续任务填充内容。

---

### 任务 2：记录「环境准备」阶段

**前置条件：** 用户完成了 Skill 安装。

**文件：**
- 修改：`source/_posts/Skill-Distill-Project.md`

- [ ] **步骤 1：向用户收集安装过程信息**

向用户提问：安装了哪个 Skill？安装命令是什么？遇到了什么问题？如何解决的？

- [ ] **步骤 2：撰写「一、动机」章节**

根据用户回答，写 2-4 段话说明：为什么要做这个项目、想达到什么效果。

- [ ] **步骤 3：撰写「二、环境准备」章节**

记录：Skill 名称和来源、安装命令、环境要求、踩坑与解决方案。包含具体的命令/代码块。

- [ ] **步骤 4：更新文章 Front Matter**

根据 Skill 名称和目标网红，更新 `title` 和 `tags` 字段。

- [ ] **步骤 5：阶段性保存**

```bash
git add source/_posts/Skill-Distill-Project.md
git commit -m "post: add motivation and setup sections"
```

---

### 任务 3：记录「选定目标」阶段

**前置条件：** 用户选定了要蒸馏的游戏/体育网红，并收集了素材。

**文件：**
- 修改：`source/_posts/Skill-Distill-Project.md`

- [ ] **步骤 1：向用户收集选材信息**

向用户提问：选了哪位网红？为什么选 TA？收集了哪些素材（视频/文案/截图）？素材来源？

- [ ] **步骤 2：撰写「三、选定目标」章节**

记录：网红介绍（1-2 句）、选择理由、素材清单与来源。保持叙述有故事感。

- [ ] **步骤 3：Commit**

```bash
git add source/_posts/Skill-Distill-Project.md
git commit -m "post: add target selection section"
```

---

### 任务 4：记录「蒸馏实战」阶段

**前置条件：** 用户完成了蒸馏操作。

**文件：**
- 修改：`source/_posts/Skill-Distill-Project.md`

- [ ] **步骤 1：向用户收集实战过程信息**

向用户提问：蒸馏的具体步骤是什么？用了什么参数？中间有调优/重试吗？关键截图有吗？

- [ ] **步骤 2：撰写「四、蒸馏实战」章节**

按时间线记录：关键命令、参数选择理由、遇到的意外情况、关键截图（如有）。风格为实操教程向，让读者能复现。

步骤必须展示实际使用的命令和参数。

- [ ] **步骤 3：Commit**

```bash
git add source/_posts/Skill-Distill-Project.md
git commit -m "post: add distillation process section"
```

---

### 任务 5：记录「成果与复盘」并部署

**前置条件：** 用户确认项目完成。

**文件：**
- 修改：`source/_posts/Skill-Distill-Project.md`

- [ ] **步骤 1：向用户收集最终成果**

向用户提问：最终产出是什么？效果如何？和预期一致吗？后续还想做什么？

- [ ] **步骤 2：撰写「五、成果与复盘」章节**

记录：最终产出展示、效果评价、经验教训、下一步计划。

- [ ] **步骤 3：全文润色**

通读全文，修正表述不连贯的地方，统一语气风格，确保五章之间逻辑流畅。

- [ ] **步骤 4：更新 Front Matter date**

将 `date` 字段更新为最终完成日期。

- [ ] **步骤 5：最终 Commit + Push**

```bash
git add source/_posts/Skill-Distill-Project.md
git commit -m "post: add results and finalize skill distillation article"
git push
```

推送后等待 GitHub Actions 部署完成（约 30 秒），验证 https://Alalaki-W.github.io/ 可见新文章。

---

### 任务 6：验证部署

**文件：** 无（只读检查）

- [ ] **步骤 1：确认 GitHub Actions 运行成功**

```bash
gh run list --repo Alalaki-W/Alalaki-W.github.io --limit 3
```

检查最新 workflow run 状态为 `completed` 且结论为 `success`。

- [ ] **步骤 2：确认文章可访问**

提示用户浏览器访问 https://Alalaki-W.github.io/ 确认新文章在首页可见且内容完整。
