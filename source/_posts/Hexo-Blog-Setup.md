---
title: Hexo 博客搭建记
date: 2026-05-26 15:04:10
categories: 技术
tags:
  - Hexo
  - 博客
  - GitHub Pages
  - Bamboo
---

## 起因

之前用 Hugo 搭了个博客，但总觉得主题不够好看。朋友推荐了 Hexo，一眼看中 Bamboo 主题，决定迁移过来。

<!-- more -->

## 技术栈

- **框架**：Hexo 8.x
- **主题**：Bamboo 3.3.12
- **托管**：GitHub Pages
- **部署**：GitHub Actions 自动构建

## 迁移过程

从 Hugo 切到 Hexo 分了几步走：

1. `hexo init` 初始化项目
2. 安装 Bamboo 主题
3. 把旧文章调整 Front Matter 格式迁过来
4. 配好 GitHub Actions 部署流水线
5. `git push` 上线

整个过程比想象中顺利，Hexo 的 Node.js 生态对前端开发者更友好。

## 写作流程

以后写新文章就三条命令：

```bash
npx hexo new post "文章标题"   # 创建文章骨架
npx hexo server                # 本地预览
git push                       # 推送上��
```

推送后 GitHub Actions 自动部署，30 秒就能在博客看到更新。

## 感想

博客这东西，工具是次要的，坚持写才重要。希望这次能好好写下去。
