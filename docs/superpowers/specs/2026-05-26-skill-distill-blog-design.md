# 蒸馏 Skill 体验项目 + 博客记录

## 目标

安装一个蒸馏类 Skill，用于蒸馏某位游戏/体育类网红，完整记录过程到一篇 Hexo 博客文章中并推送部署。

## 项目工作流

```
[安装 Skill] → [选定网红 + 收集素材] → [蒸馏实战] → [成果展示与复盘]
```

## 博客输出

### 单篇文章，逐步填充

文件：`source/_posts/Skill-Distill-<target>.md`

Front Matter：
- title: 动态确定
- date: 项目完成日期
- categories: 技术
- tags: AI, Skill, 蒸馏, <网红名>

### 文章章节

1. **动机** — 为什么想做这个项目
2. **环境准备** — 安装 Skill 的过程、踩坑记录
3. **选定目标** — 选了哪位网红、为什么
4. **蒸馏实战** — 实际操作过程、关键步骤
5. **成果与复盘** — 最终产出、经验总结

### 写作约定

- 每完成一个项目阶段，根据实际操作记录对应章节
- 所有内容逐步填充到同一篇 `.md` 文件中
- 项目完成 + 文章完成后，一次性 commit + push 触发部署

## 技术要求

- 文章格式：Hexo Markdown（Front Matter + 正文）
- 部署：push 到 `main` 分支 → GitHub Actions 自动构建部署
- 博客框架：Hexo 8.x + Bamboo 3.3.12 + GitHub Pages

## 成功标准

- Skill 成功安装并可用
- 蒸馏产出有实际价值
- 博客文章完整记录全流程
- 文章成功推送并部署到 https://Alalaki-W.github.io/
