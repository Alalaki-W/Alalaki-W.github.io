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
  - 徐静雨
  - B站
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

配好之后可以用 `curl -I -L https://github.com` 验证一下代理是否生效（`-L` 跟随重定向），只要收到了 HTTP 响应，就说明链路通了。

> 这里 git 用了 `--global`，会对本机所有仓库生效。如果之后不需要代理了，记得 `git config --global --unset http.proxy` 取消。

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

徐静雨是谁？如果你是 B 站用户，大概率刷到过这个东北口音浓重、语速飞快、逻辑自成体系的篮球解说博主。他以「静雨逻辑」闻名——用一种看似荒诞却自洽的推理方式点评 NBA 赛事、球员表现，金句频出，评论区常年被粉丝用「静雨说得对」刷屏。他被网友列入「B 站三大魔头」（另外两位据说是户晨风和峰哥），影响力早已超出篮球圈，跨进了游戏、综艺等多个领域。

选择徐静雨，最初其实经历了一番纠结。我的第一反应是蒸馏户晨风或者峰哥——他们的风格同样鲜明，逻辑也很有特点。但调研后发现，社区里已经有人做过这两位的工作了。这时候一个念头冒出来：**我要做第一个蒸馏徐静雨的人。**

更深一层想，徐静雨真正吸引人的地方，其实不是篮球专业知识，而是他的脑回路——那种清奇的切入角度、极具辨识度的东北腔表达、以及把任何话题都聊出「静雨味」的能力。他属于典型的「人格驱动型」网红：粉丝追的不是内容，是他这个人本身。这种类型恰恰最适合 Skill 蒸馏——因为我们要提取的不是知识库，而是一个人的思维框架和表达模式。

素材主要来自 B 站视频和直播录屏，辅以评论区高赞回复来捕捉粉丝互动风格。

## 四、蒸馏实战

<!-- TODO -->

## 五、成果与复盘

<!-- TODO -->
