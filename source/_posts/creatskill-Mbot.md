---
title: Mbot-Agentic技术栈学习-Claude创建skill-日记
date: 2026-05-27
tags: [Claude, Skill, Cursor, Mbot]
categories: 技术笔记
---

# Mbot-Agentic技术栈学习-Claude创建skill-日记

## 创建一个skill

原来都是直接让Cluade给我装skill或者用skill creator引导我创建一个skill,正好今天王哥发了个cursor的实战教程我跟着用Claude做一下。

在某个项目文件夹下新建`.claude`文件夹,正好用之前江科大stm32的资料试试。

![image-20260527185313822](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527185313822.png)在刚刚建好的 `.cursor` 文件夹上右键，继续新建一个文件夹，命名为 `skills`。

![image-20260527185716251](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527185716251.png)

`skills`里再套个文件夹，代表你skill的名字

![image-20260527185911503](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527185911503.png)

里面放`SKILL.md`,里面放的应该就是约束的Prompt。**SKILL不大写不行！**

![image-20260527190150448](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527190150448.png)

打开`SKILL.md`,复制王哥给的提示词

> ### 提示词：
>
> ####  核心目标 (Description)
>
> 你是一个极其严谨的高级系统架构师。你的任务是将用户模糊的需求，转化为高可用、结构清晰的模块化设计，并严格遵循“先设计，后编码”的原则。**严禁在未经用户确认设计前，直接生成大段业务代码。**
>
> #### 当你被触发执行此技能时，必须严格按照以下顺序与用户交互：
>
> ##### 阶段 1：需求拆解与反问 (Analysis)
>
> 1. 深入分析用户的初步需求。
> 2. 列出该需求在实际落地时可能遇到的 2-3 个关键隐性约束（例如：内存占用、并发冲突、异常边界条件处理）。
> 3. 询问用户对于这几个技术难点的偏好。
>
> **（⚠️ 动作要求：在此必须停顿，结束当前回复，等待用户输入确认）**
>
> ##### 阶段 2：系统设计与拓扑 (Design)
>
> 1. 收到用户对阶段 1 的确认后，依然**不要写具体代码**。
> 2. 使用 Markdown 树状图或清晰的列表，画出模块的调用关系图和数据流向。
> 3. 仅提供核心函数/类的接口签名（伪代码即可）。
> 4. 询问用户：“这个架构设计是否符合您的预期？是否可以开始进入具体代码实现阶段？”
>
> **（⚠️ 动作要求：在此必须停顿，结束当前回复，等待用户输入确认）**
>
> ##### 阶段 3：代码实现 (Implementation)
>
> 1. 收到用户对阶段 2 的最终确认后，才开始编写具体的代码。
> 2. 产出的代码必须符合高内聚低耦合原则，并附带核心逻辑的注释。

## 使用skill

在Claude终端里输`/architect`，可以看到skill已经装载了，并且提示词是`Project`。

![image-20260527191250166](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527191250166.png)

试一下调用这个skill看看能不能正常工作，就让他优化一下14-1独立看门狗好了，顺便把注释去掉![image-20260527191602268](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527191602268.png)

![image-20260527191658052](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527191658052.png)

可以看到成功运行skill了，skill先是找到具体项目，然后完整阅读了代码

![image-20260527192018472](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527192018472.png)

这里不知道为什么skill重复了一部分工作，可以看到在识别第一个约束之后又重新识别了

![image-20260527192206189](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527192206189.png)

这里我直接AAA

![image-20260527192530971](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527192530971.png)

继续

![image-20260527192746303](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527192746303.png)

OK改完了，看看效果，注释啥的真没了，代码也明显改掉了

![image-20260527193237076](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527193237076.png)

![image-20260527193301383](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527193301383.png)

![image-20260527193328215](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527193328215.png)

阔以，现在来试试纠下错，我直接复制的王哥的文档，但是明显提示词里有对每个问题停顿而Claude并没有停顿，并且还多次重复了skill，我直接让Cluade自查试试

![image-20260527193718297](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527193718297.png)

对于“没停顿”，原因是skill是一次性加载的，一个文件不会加载一半就不读了，只要有上下文Cluade就会读下去

![image-20260527200305326](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527200305326.png)

而对于“重复”，第一个重复了是因为逻辑重复了，并且skill的语法不对，很可能是cursor语法和claude有不同之处

![image-20260527200634193](C:\Users\吴壮壮\AppData\Roaming\Typora\typora-user-images\image-20260527200634193.png)

还可以噻，感觉学到不少东西