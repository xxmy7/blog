---
title: 科研选题与论文的创新点
date: 2023-12-14 08:43:29
tags: 
    - 科研
    - 论文
categories: 
    - 选题
summary: 有哪几种常见的研究思路？
---

## 1 我的关于科研选题的一些思考

> 作者：一路向北
> 链接：https://zhuanlan.zhihu.com/p/671458670
> 来源：知乎


之后我也一直在思考，其实选题本身也是一个**金字塔**。

- 塔尖是Resnet，MAE，Diffusion这种可以引起整个CV界大地震的工作，属于基础研究DreamWork，做的人少影响力大，但同时也充满曲折，因为你在开创一种新的范式没有之前的工作可以follow，同时也不一定会做出来。
- 塔中是一些较为开创性的工作（相较塔尖，但是能做出这一类的工作也同样是值得称赞的），也就是一些挖坑的工作。比方说把transformer引到视觉领域里，把参数高效微调引导视觉领域里，等等。这些工作背后可以引申出更多的相关工作（也就是俗称的填坑）。做出这类工作一般需要敏锐的科研嗅觉，了解其他领域的最新进展；同时还需要对自己的领域相当熟悉，需要知道怎么才能把其他领域的技术引进来。
- 塔底是一些follow别人工作的研究，做起来更容易（大多数情况都有之前的代码），新手友好。魔改网络，刷点等等。这些工作比较容易上手，但是坏处是你做出来之后关注度比较低，甚至可能因为follow的工作的意义不大而被拒稿。

其实大多数人的科研历程也类似一步步地从塔底走向塔尖的过程。

目前我的目标是既要做一些塔中的工作（锦上添花），也要做一些塔底的工作（雪中送炭）。对应前文叶子要有，花也至少要有一朵拿得出手的。当然在做塔底工作的时候也要尽量做“第二个吃螃蟹的人“。因为一个领域卷烂之后刷点很难，做出来也没有什么人引用你的文章，因为这个领域很难再刷上去了

----

## 2 计算机视觉 | 哥大读博五年总结（全）

> 作者：Mike Shou
> 链接：https://zhuanlan.zhihu.com/p/338193330
> 来源：知乎

### （1）Phd选题

我觉得这段经历，对新手很有参考价值，**很多时候光努力不够，方向更重要。新手如何选博士几年的topic，有两个问题值得思考：**

**能不能快速上手？**有几个简单的评判标准：

- state-of-the-art的paper有没有开源的代码？目的是你能迅速复现baseline，熟悉整体pipeline（如怎样预处理，后处理），加深对实现和细节的理解
- 有没有对这个topic有hands-on经验的师兄，或者community里面approachable的前辈？目的是，当你遇到实现上的细节问题，可以及时咨询和得到反馈
- 这个topic有没有比赛，或者标准的benchmark？目的是，有大家已经定义好的数据，实验setup，评价标准；这样，你有可以直接比较的baseline，outperform baseline的时候也容易被人认可

**能不能有大的impact？**这里我指的是博士期间的大方向，由一系列单项的工作或者paper构成。单篇paper通常有三种类型：（1）First work：开创了一个topic，比如RCNN于object detection（2）Last work：基本解决了一个topic，比如Faster-RCNN，YoLo于object detection（3）Improve类型，介于First和Last之间的。

Last很难，Improve常见但影响力不够深远，对于新手而言，博士的早期工作，在有能力做出来和有impact之间的trade-off比较好的，估计是First了，不一定非要是第一篇，只要是某个topic里面开创性工作的那一批之一，都是不错的。这个早期工作之后，你会对这个问题哪里要改进，有很清楚的认识，因为improvement room大，也会有很多ideas。同样，早期的时候怎么选这样一个topic呢：相关的比赛是这一两年新开的吗，相关的benchmark是这一两年出来的吗，上面的结果提升空间大吗（现在是20%还是已经80%了）？

### （2）单篇Paper选题

前面说的PhD选题是大方向上的，具体到每一篇paper，选择的principle和重点则不太一样。来Facebook后从马爷爷那知道了一个著名的**Heilmeier问题系列**，是指导老师们申项目的，我觉得稍微改改，便很适用于我们考虑，某一篇paper的选题，合不合适：

1. **What are you trying to do?** Articulate your objectives using absolutely no jargon.
2. **How is it done today, and what are the limits of current practice?**
3. **Who cares?** [Support other’s research? Shape research landscape? Power applications in industry?]
4. **What's new in your approach** and why do you think it will be successful?
5. If you're successful, **what difference will it make?** [e.g. Contributions in theory/modeling? Improve accuracy by 5% on dataset A, B, C…?]
6. **What are the risks and the payoffs?** [Further, how would you mitigate the risks? If your proposed method does not work, what could be alternative design? These can end up as discussions such as ablation studies in your paper.]
7. **How much will it cost?** [e.g. How many GPUs do your experiments require? How long is each training process? How about data storage?]
8. **How long will it take?** [How many hours are you going to work on this per week? When is the submission DDL? Can you make it?]
9. **What are the midterm and final "exams" to check for success?**

---

## 3 AI论文如何找到创新点

> 作者：四块二学长
>
> 链接：【AI论文如何找到创新点】 https://www.bilibili.com/video/BV1Fa4y1m7Bu/?share_source=copy_web&vd_source=994cbda57e25e37f615fa663eee69db5
>
> 来源：哔哩哔哩

### 创新点来源

1. 老文章用新框架（深度框架）重新做（强创新）

    传统方法改深度学习方法：明确学习目标，输入输出，损失函数

2. A+B（蒸馏、NAS、重参数化repvgg）（弱创新）

3. 输入输出新角度（看实现难度）

4. 有监督改无监督（强创新）

例如可变形卷积的概念和应用。建议关注该领域的最新概念并寻找结合自己任务的机会。
