---
title: 构建客户历程区段
description: 了解如何在Adobe Analytics中创建基于行为的客户历程区段，并通过遵循此分步指南改善客户在Adobe Experience Cloud中的体验。
feature: Segmentation
role: User
level: Experienced
doc-type: Article
last-substantial-update: 2023-05-02T00:00:00Z
jira: KT-13180
thumbnail: KT-13180.jpeg
exl-id: c06afc7b-e997-404d-82a4-e7ec5d5ba44d
source-git-commit: d95136a21c08312a81baba7673cb7135270af4bd
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 1%

---

# 构建客户历程区段

了解如何在Adobe Analytics中创建基于行为的客户历程区段，并通过遵循此分步指南改善客户在Adobe Experience Cloud中的体验。

让我们创建更好的客户历程区段！ 在本系列中，我们将使用Adobe Analytics定义基于行为的区段，估计受众规模并跟踪用户移动。 最终，您将能够个性化媒体并改善客户在Adobe Experience Cloud中的体验。 请记住，这些区段是活动的，应随着您进一步了解客户而更新。 尽管报告可能会带来一些挑战，但请不要担心，我将引导您完成报告！ 我们先创建第一组客户历程区段，从“单次点击奇迹”区段开始。

今天，我们将为第一组客户历程区段创建占位符，构建一个Adobe Analytics Workspace来帮助我们定义区段，并定义我们的第一个区段“一击奇迹”。

观看本系列后，您将能够根据行为信号在Adobe Analytics中创建客户历程区段。 您将能够估计历程中每个阶段每个受众的大小，并了解用户在这些阶段之间的移动速率。 并且您可以将这些客户历程受众导出到Adobe Experience Cloud以启用个性化和媒体定位。

每个业务都不一样，这意味着您的客户历程区段看起来将与我的不同。 因此，不要为您的区段规定特定的公式，而是建议一些要查看的内容以及构建这些区段的整体过程。

此外，请注意，您的客户历程区段将是活动区段，这一点也很重要。 这不是一个一劳永逸的过程。 随着您进一步了解您的客户，您将更新这些区段。 这给报告带来了一些挑战。 人们希望报表保持一致，如果我们的区段定义发生更改，则报表中的数字也会发生更改。

## 访问意图区段快速入门

构建客户历程区段的第一步是，使用行为信号和（如果可用）客户声音数据推断访客出现在您网站上的原因。 我们将构建一组访问意图区段，以对网站上的所有访问进行分类。 此时，我们的访问意图区段需要相互排斥，并且完全详尽。 每次访问应属于一个（且仅属于一个）访问意图区段。

访问意图区段描述了访问，因此我们将在区段定义中使用访问容器。

我的初始访问意图区段集包括：

* 一次点击奇迹
* 意识
* 注意事项
* 预订（购买）
* 保留（管理预订/购买）

为了使我的访问意图区段易于使用，我为区段名称添加了“意图”前缀，为它们提供了用于启用排序的数字，并将它们标记为“意图”。 我的区段与下图相似。

![意图区段](assets/intent-segments.png)

**使用带有页面查看次数>= 1占位符定义的访问容器创建访问意图区段。**

如我们所见，构建这些区段是一个反复的、相互关联的过程。 我将在以后的帖子中描述构建这些区段的过程。

## 访问意图区段数据质量Workspace

![访问意图工作区](assets/visit-intent-workspace.png)

我使用了一个简单的工作区，以确保我妥善定义了访问意图区段。 请记住，每次访问只属于一个访问意图区段。 我设置的工作区可确保计入所有访问，并且区段之间不重叠。

我使用标记“数据质量”、“访问意图”和“客户历程”将此工作区命名为“数据质量：访问意图区段”。 稍后，我们将构建一个“访问意图仪表板”，以便前缀“数据质量”表示此工作区用于设置和维护区段。 它是一个管理仪表板，几乎没有业务洞察，但对于确保区段的维护很重要。 最好定期返回此仪表板或设置警报，以确保您的区段保持正确定义。

此工作区中最重要的可视化图表是左中角的区段重叠自由格式可视化图表。 使用访问量度，为每个“访问意图”区段创建列过滤器，并在最右侧列中创建所有访问区段。 在左侧为每个访问意图区段创建行。 您现在将拥有跨选项卡可视化图表。 正确配置区段后，每个访问意图区段与其自身的交叉点处仅有一列和一行中的数据。

接下来最重要的可视化图表是左上角的摘要量度。 分段访问概要从紧接下方的区段重叠可视化图表中的所有访问列中获得其值。 所有访问摘要有其自己的隐藏表格。

![所有访问](assets/all-visits.png)

在右上角，我向每个区段添加了其他指标，以便为区段的形成提供一些“风格”。 具体来说，由于这些区段相互排斥，我仅希望看到预订意图区段的预订(担心不会，当我们基于访客生成这些访问意图区段时，我们会获得转化率。

请记住，我们刚刚创建了占位符区段。 因此，您的工作区最初看起来会很奇怪。 您的所有访问意图区段都将重叠100%，因为它们具有相同的定义。 这是正确的，而且正是您在此过程中希望看到的内容。 在我们构建区段定义时，您会开始看到这些区段开始成型。

![访问意图区段定义](assets/visit-intent-segment-defs.png)

## 构建您的第一个访问意图区段

定义访问意图区段有点像一个消除过程，并且它们之间存在大量相互依赖关系。 所以我没有按照历程的顺序来构建这些区段，而是按照从最容易定义到最具挑战性的顺序来构建。 这给了我这个命令：

1. 意图： 0 — 一次点击惊奇
1. 意图： 3 — 预订
1. 意图：4 — 保留
1. 意图：2 — 考虑
1. 意图： 1 — 意识

很随意，是吗？ 定义这些访问意图区段是一个反复的过程，通常对一个区段的调整需要更新其他区段。 随着我描述如何定义每个区段，这一点将变得更加清晰。

今天，我们将定义第一个也是最简单的单次点击奇迹区段

## 构建“单次点击奇迹”区段

我的第一个区段“One Hit Wonders”很容易定义。 它只是任何仅有一个页面查看的访问。 我们真的不知道为什么那个用户会出现在网站上，因为他们退了回去。 我想我们可以根据他们的登入页面猜测一个意图，但只看一个页面，信息不足以让他们对意图做出有根据的猜测。

![区段定义](assets/segment-def.png)

定义此区段后，您将开始看到您的访问意图Workspace成形。

![更多区段定义](assets/more-segment-defs.png)

使用Adobe Analytics构建客户历程区段是一个具有挑战性但很有价值的过程。 通过创建基于行为的区段、估计受众规模并跟踪用户移动，企业可以个性化媒体并改善客户体验。 每个业务都是独一无二的，没有用于创建区段的特定公式，但需要遵循指南和流程。 随着企业进一步了解其客户，应更新区段，这将带来报告挑战。 通过遵循构建访问意图区段的过程，企业可以改善整体客户体验。

## 作者

本文作者：

![Aaron Fossum](assets/aaron-headshot.png)

**Aaron Fossum**，Director，数字分析

Adobe Analytics 负责人
