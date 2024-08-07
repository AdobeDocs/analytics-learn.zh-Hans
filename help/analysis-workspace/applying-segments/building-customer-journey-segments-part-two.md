---
title: 构建客户历程区段 — 第二部分
description: 在第二部分中，了解如何构建购买和保留访问意图区段，以了解客户的购买历程并个性化内容。 使用“Book Now”点击或登录等信号，我们可识别购买和保留意图，以便进行有效分析和有针对性的营销。
feature: Segmentation
role: User
level: Experienced
last-substantial-update: 2023-07-21T00:00:00Z
jira: KT-13476
thumbnail: KT-13476.jpeg
exl-id: 2db73010-5cd0-4454-a4ba-fc1667a50cba
source-git-commit: d95136a21c08312a81baba7673cb7135270af4bd
workflow-type: tm+mt
source-wordcount: '1997'
ht-degree: 0%

---

# 构建客户历程区段 — 第二部分

在第二部分中，了解如何构建购买和保留访问意图区段，以了解客户的购买历程并个性化内容。 使用“Book Now”点击或登录等信号，我们可识别购买和保留意图，以便进行有效分析和有针对性的营销。

## 构建购买和保留访问意图区段

在我们的最后一篇帖子中，我们描述了创建访问意图区段的过程，并构建了我们的第一个访问意图区段 — 一次点击奇迹。 今天，我们将构建购买和保留区段。 我们分割了大约23%的访问，并为剩余的访问意图区段构建了占位符。

![图像1](assets/Image-1.png)

我们正在构建的访问意图区段是构建基于访客的客户历程区段的基础。 在构建访问意图区段后，我们将构建这些基于访客的历程区段。

请记住，构建访问意图区段是一个消除过程。 因此，我们并不按时间顺序构建这些区段。 我们正在构建访问意图区段，以便最轻松地定义，更难以定义：

1. 意图： 0 — 一次点击惊奇
1. 意图：3 — 购买
1. 意图：4 — 保留
1. 意图：2 — 考虑
1. 意图： 1 — 意识

在上一个帖子中，我将“购买”区段称为“预订”，因为我在从事旅游业务。 但以后，我们将它称为“购买”区段，以便更轻松地应用于多个行业。

信号越清晰，构建区段就越容易。 在上一个帖子中，我们构建了“单次点击奇迹”区段，该区段最易于定义，因为它只是跳出流量。 您会发现，购买和保留意图区段也非常易于定义，因为它们基于非常明确的信号。

## 客户历程与购买倾向不同

当我们考虑构建购买意图区段时，请务必记住，识别客户在其历程中的位置与倾向不同。 您可能会有一些购买倾向模型，这些模型会对Web访客进行评分，以预测他们进行购买的可能性。 这些模型非常有用，但它们与我们今天构建的购买意图区段不同。

当倾向模型试图预测访客是否会购买时，我们的访问意图区段试图了解人员在其购买历程中的位置。 使用意图区段了解客户的心态，这有助于我们使内容个性化并定制营销，从而推动适当的流量，充实我们的销售渠道。 因此，我们的购买意图区段会查找表明访客有意购买的明确行为信号。

## 构建购买访问意图区段

购买访问意图区段易于定义。 就我而言，任何点击“Book Now”（立即预订）按钮的人，都表示有某种预定巡航的意图。 这类似于在线零售商单击“结帐”，或媒体上下文中的“订阅”链接。

在决定使用哪个信号来推断购买意图时，您需要做出一些判断。 我们希望购买意向区段包含所有购买，但转化率不应为100%。 因此，我们不希望对此区段使用“购买确认”或“感谢”页面。

同样，查看您的购买页面（或在购买确认之前的任何页面）可能会因为漏斗太低而无法用于分析和定位。

随着漏斗的继续上升，信号是否可用于指示客户打算购买会变得不那么清楚。 在我的例子中，“Book Now”类似于零售业“Checkout”链接，这是我使用的信号。 但在零售上下文中，结帐可能仍然在漏斗下方太远，因此“查看购物车”甚至“添加到购物车”可能更好。

我们可以把它想象成一家杂货店。 如果有人从货架上拿起一件产品，这并不意味着他们打算买它。 即使他们把它放在购物车里，他们也可以马上把它放回货架上。 但是，如果他们把产品放进购物车，然后开始四处走动，很可能就会购买它。 如果他们在结账行里买了那件产品，他们肯定会买的。

我建议使用所访问的页面或其他明确的购买意向信号，并避免使用其他不太直接的信号来识别购买意向。 例如，我不会使用会话数、会话或类似会话中的页面数。 这些间接信号表示考虑事项，而不是购买意图。 请记住，此区段的目的是推断访客的访问意图，而不是其倾向。

### 使用Analytics Workspace识别购买意图信号

流失报表对于识别指示购买意图的良好信号非常有用。 查找逻辑上表示意图的位置。 您可以确认，如果看到某个重要流失进入该步骤，并且随后该步骤的流失通常较小，则表明此步骤的意图。

![图像2](assets/Image-2.png)

查看与网站上各个页面关联的转化率也很有用。 这尤其有助于识别指明购买意向但可能不需要进行购买的页面（例如融资页面、购买配置页面等）。

![图像3](assets/Image-3.png)

最后，务必要将购买开始与购买确认之间的所有页面都包含在您的区段中。 访客可以跳转，在不同时间点重新进入您的购买流程。

### 不包括其他分部

回忆一下我们的第一个帖子，我们的访问意图区段需要相互排斥，并彻底列出所有内容。 这是本系列中经常会听到的说法。

确保您的购买意向区段不包括“一个”和“完成”区段。 您只需排除“一个”和“完成”区段，因为用于购买意图的信号非常具体。

请注意，如果排除“完成”和“完成”区段，则可能会排除从结账页面上重新进入您网站的人员。 这是正常的。“一个”和“完成”的定义本身就是单页面查看，这意味着即使访客在结账页面上进入页面或进行刷新，他们的访问也不会继续，因此不会表达购买意图。

### 区段生成器中的购买意图区段

购买意图的区段定义非常简单。

使用访问容器，包括那些明确指示购买意图的页面或其他操作。 如果您有多个包含条件，请确保将它们放置在通过“And”条件连接的容器中。

向由“And”条件连接的区段添加一个“排除”容器。 将“One Hit Wonders”区段定义（页面查看次数等于1）添加到排除容器。

![图像4](assets/Image-4.png)

作为最佳实践，请确保为容器设置标签。 您会很高兴您这样做了，尤其是因为我们的区段定义变得更加复杂。

现在，我们已经构建了购买意图区段，接下来可以使用访问意图数据质量Workspace来查看我们的购买意图区段与我们的完成区段互斥。

![图像5](assets/Image-5.png)

## 构建保留访问意图区段

在邮轮业务中，很多客人来到我们的网站管理预订，但不一定进行购买。 他们可以来到网站输入旅行信息、查看行程、进行晚餐预订或多项其他活动，而无需购买邮轮。 我们的客人还可以购买岸游或其他改善其体验的设施。 我们将这些增强功能视为维系的一部分，因此将它们与我们的预订区段（在此博客系列中我们将其称为“购买”）分开。

零售客户或许能够退货或管理其忠诚度计划。 媒体或技术订阅者可能正在使用产品。 如果您的访客访问您的网站以管理与您的关系，则属于保留访问，我们应查看这些信号。 如果您提供在线产品，如媒体、技术、在线银行或其他产品，则可能有许多其他类型的访问意图区段，我们将在本系列中不予讨论。

与购买意向区段一样，我们正在寻找非常明确的意向指示。 对我来说，我们网站有一整个区域专门用于管理邮轮，以便轻松识别这些页面。 对于其他企业而言，这可能更为复杂。 查找登录、帐户管理、访问支持页面等信号。

我应该注意，“维系”对于此访问意图来说有点尴尬，因为该访客不在我们的网站上，“因此我可以作为客户保留。” 我们打算保留这次访问。 请记住，同情我们的客户，坚持以客户为中心！

### 使用Analytics Workspace识别保留意图信号

同样，Analytics Workspace可帮助我们识别保留意图。 您可以使用页面、网站区域或自定义区段维度对页面进行分类。 查找购买转化率较低的页面。 在我们的示例中，我们发现，与其他在逻辑上与购物和购买更相关的页面相比，在线登记和岸游(Shorex)页面的转化率相对较低。

![图像6](assets/Image-6.png)

此外，在Workspace中查找高流量页面也是一个不错的主意。 扫描高流量页面的列表，并确定它们是否表示保留意图。

## 不包括其他分部

同样，我们的访问意图区段需要互斥并且完全详尽。 如果你还不厌倦读这本书，你会厌倦的！ 对于我们的保留意图区段，排除购买意图行为至关重要。

对于我们大多数人来说，购买意图和保留意图不是互斥行为。 我们邀请了客人来此网站管理他们即将到来的邮轮，还邀请他们预定下次的旅行（谢谢！）。 如果您是一家餐厅，访客可能会检查其忠诚度积分，然后在线下订单。

即使行为不是相互排斥的，我们的区段必须用于客户历程分析。 我们可以构建其他非常有趣的区段来分析购买和忠诚度行为之间的重叠。 但就我们当前的目标而言，我们需要这些区段相互排斥。

由于产生需求是营销的主要目标之一，因此我们的保留意图区段将排除购买意图。 换言之，如果有人来到我们的网站管理邮轮，但同时表示打算预订新的邮轮，则该访问将转到购买意图部分。

### 区段生成器中的保留意图区段

我们的区段定义正变得更加清晰。 在区段中包含访问次数。 添加保留意图信号。 对我来说，这很简单。 如果页面名称以“bge：”（我们预订的访客页面）开头，则表示您位于区段中。 我添加了大于一个的页面查看次数作为额外度量（但我们仍会排除下面的一个点击奇迹）。

然后，为一次点击奇迹和购买意图访问添加排除容器。 确保将您的容器与“And”条件连接在一起。

![图像7](assets/Image-7.png)

请再次查看您的访问意图数据质量Workspace以确保您的区段相互排斥。 我们的访问意图区段正在成形良好！

![图像8](assets/Image-8.png)

此时，我们已经配置了五个访问意图区段中的三个。 我们看到这些区段是相互排斥的。 在接下来的帖子中，我们将创建最终的“访问意图”区段、“注意事项”和“知晓度”，我们的区段都将非常全面。 设置访问意图区段后，我们会将它们汇总到基于访客的区段中，您会发现这些区段对于分析和个性化非常有用。

## 作者

本文作者：

![Aaron Fossum](assets/aaron-headshot.png)

**Aaron Fossum**，Director，数字分析

Adobe Analytics 负责人
