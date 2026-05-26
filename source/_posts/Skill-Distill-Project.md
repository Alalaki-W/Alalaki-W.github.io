---
title: Skill 蒸馏体验全记录
date: 2026-05-26
categories: 技术
tags:
  - AI
  - Skill
  - 蒸馏
  - 女娲
  - 代理
---

## 一、动机

最近在 Claude Code 的生态里发现了一个很有意思的项目：[女娲.skill](https://github.com/alchaincyf/nuwa-skill)（nuwa-skill）。它的口号很有意思——「女娲造人」：输入一个人名、一个主题、甚至只是一段模糊的需求描述，Skill 会自动进行深度调研，提炼出对方的思维框架，最终生成一个可运行的"人物 Skill"。装上之后，你就可以在 Claude Code 里以那个人的视角来思考和对话。

这不就是「蒸馏」吗？把一个人的思维方式、决策模型、表达风格，压缩成一个可复用的 Skill 文件。这个概念让我很兴奋——如果能蒸馏一位游戏/体育类的网红，模拟 TA 的内容判断、选题逻辑、互动风格，会不会很有意思？于是我决定亲自走一遍完整流程，把每个步骤记录下来，写成这篇连载。

目标是蒸馏一位游戏或体育领域的网红（具体人选下一篇再揭晓）。本文作为系列开篇，先搞定动机和环境搭建。

## 二、环境准备

环境准备分两步：代理配置和 Skill 安装。由于我的网络环境需要走代理访问 GitHub，所以先要把代理链路打通。

### 2.1 代理配置

本地 VPN 代理跑在 `7897` 端口，需要让终端、npm 和 git 都走这个端口：

```bash
# 环境变量
export HTTP_PROXY=http://localhost:7897
export HTTPS_PROXY=http://localhost:7897

# npm
npm config set proxy http://localhost:7897
npm config set https-proxy http://localhost:7897

# git
git config --global http.proxy http://localhost:7897
git config --global https.proxy http://localhost:7897
```

配好之后可以用 `curl -I https://github.com` 验证一下代理是否生效，能返回 200 就说明链路通了。

### 2.2 安装女娲.skill

女娲.skill 托管在 [GitHub](https://github.com/alchaincyf/nuwa-skill) 上，安装方式是把仓库 clone 到 Claude Code 的 skills 目录：

```bash
git clone https://github.com/alchaincyf/nuwa-skill.git ~/.claude/skills/nuwa-skill/
```

> 注意目标路径必须在 `~/.claude/skills/` 下，Claude Code 会自动扫描这个目录加载 Skill。

clone 完成后，重新启动 Claude Code 会话，在可用技能列表里就能看到 `nuwa-skill` 了。它的触发词包括：

- 「造skill」
- 「蒸馏XX」
- 「女娲」
- 「造人」
- 「XX的思维方式」

有了这个基础设施，接下来就可以进入正题——选定蒸馏目标。

## 三、选定目标

<!-- TODO -->

## 四、蒸馏实战

<!-- TODO -->

## 五、成果与复盘

<!-- TODO -->
