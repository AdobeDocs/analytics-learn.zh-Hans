---
title: 从 Excel 转为使用计算指标
description: 通过本文了解在Adobe Analytics中使用计算量度的好处，以及它们如何能为您提供数据的连续、动态视图。
feature: Calculated Metrics
role: User
level: Experienced
doc-type: Article
last-substantial-update: 2023-05-02T00:00:00Z
jira: KT-13178
thumbnail: KT-13178.jpeg
exl-id: d4f69244-6614-41f3-ac48-70adabb8a8e7
source-git-commit: d95136a21c08312a81baba7673cb7135270af4bd
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 2%

---

# 从 Excel 转为使用计算指标

通过本文了解在Adobe Analytics中使用计算量度的好处，以及它们如何能为您提供数据的连续、动态视图。

嘿！ 为什么现在使用Excel？ 我知道为什么。 你必须向合适的人汇报工作。 您正忙于输入Adobe Analytics中的数据，计算转化率，绘制转化率图表，并准备将这些数据全部放入PowerPoint中，然后将其发送给决策者。 我真的希望您至少使用Report Builder来执行此操作，但我知道在座的一些人正在手动将数据从Workspace复制并粘贴到Excel。

为什么？

为什么每个月都要经过一个手动过程？ 为什么每月显示一次静态视图，而不是连续的动态视图？ 为什么要将其复制到PowerPoint中？ 为何不直接在Adobe Analytics中创建计算指标？

## 计算量度功能强大

计算量度功能强大，但即使是最基本的数学函数，与在Excel中进行数学运算相比，也确实很有用处，并且得到了重大改进。 让我们看一看其优势和一些用例：

1. **计算量度为当前和动态**

   当您从Adobe Analytics导出数字时，它们会在某个时间点锁定。 您当然需要了解您的网站或应用程序在上个月时的执行情况，但决策者如何跟踪月中情况的进展呢？ 如果您的转化率突然下降一天，然后在月末恢复为平均值，您知道吗？ 那次暴跌可能是揭示了一个重要的遥测问题（或者更重要的，是访客行为变化）的有价值数据。 通过计算量度，您可以绘制此情况的图表，并查看发生事件的日期，从而随时做出响应。

1. **计算量度为您节省时间**

   我去过那里。 复制/粘贴。 输入公式或向下拖动公式上方的单元格。 单击图表并更改范围，以获取最近的12个月或13个月的数据。 现在复制图表。 现在再来一次。 再来一次。 再来一次。 发送PowerPoint。 这既繁琐又耗时，而且感觉您不得不永远每月都这样做。

   您可以创建一个使用计算量度的Workspace，将“最近12个月”或“13个月”作为日期范围，并在每个月第一天的午夜凌晨自动更新数据和图表。 收件人可以直接访问Workspace。 他们可以在当月的第一天或者在使用文本可视化图表添加您对数据的评论后（您知道，报表的有趣部分），自动通过电子邮件向他们发送PDF副本。

1. **计算量度可应用于大数据集**

   您可以将所有产品名称导出到Excel中，并开始计算每位访客的转化率和收入，但是，如果拥有大约100,000个转化率和收入，这会比较麻烦。 计算量度没有问题。 与往常一样，将您的维度拖放到表中，然后使用计算量度作为量度。 现在，您有一个动态可排序表，当产品或您使用的任何维度添加到目录中时，该表将自动更新。

1. **计算量度防止出错**

   出现Excel错误。 我们都去过那里。 赫克，整个希腊经济以及两位受人尊敬的学者的声誉都因为Excel公式错误而毁了。 你或许不会让欧洲经济依赖你的Excel技能，但肯定会根据你的数字做出一些关于预算的决策。 使用计算量度意味着您可以构建量度，保证它的QA，然后不必再次担心。

### 现在，我们已经了解了使用计算量度的好处，接下来让我们看一看如何将其付诸实施

**用例1：转化率**

大多数转化率只是简单的除法。 转化数除以访客数或访问数。 将漏斗最后一页的页面查看次数除以漏斗第一页的页面查看次数。 将内部营销活动点进次数除以展示次数。 所有这些都可以轻松地作为计算量度完成，并放置在仪表板中，以便享有低数据延迟、更新可视化图表和更好的可共享性。

**用例2：内部搜索**

内部搜索是了解您的网站最重要的工具之一。 网站搜索结果可告知您访客感兴趣的内容，以及他们是否可以通过导航轻松找到这些内容。 您必须能够判断您的网站搜索是否正常运行，使用一些基本的添加和划分功能即可为您提供该答案。

让我们从搜索结果开始。 您希望了解搜索词是获得结果还是不显示任何内容。 这些通常是单独的事件。 是否要经历为添加的所有内部站点搜索获取第三个事件的麻烦？ 取而代之的是，应让您的开发人员休息一下，使用计算量度添加内部搜索：“结果”和“内部搜索：没有结果”来获取内部搜索总数。

有多少百分比的搜索未返回结果？ 将内部搜索除：没有结果除以新的内部搜索总数计算量度。 现在您知道，是否迫切需要创建新内容以匹配这些搜索词，或者您的内容团队是否可以处理更高的优先级。

我们希望了解有多少包含结果的搜索会获得点进次数，并且通常还会为此使用单独的量度。 使用计算量度将点进次数除以该搜索词显示搜索结果的次数，然后以百分比形式显示。 现在，您拥有网站上每个内部搜索词的点击率。 您可以隔离显示无帮助结果的搜索词。 它提供了所有可用的历史数据，因此您可以绘制图表，当您进行改进时，通过观察数据率的上升或下降，您可以轻松查看数据是否有效。

将内部搜索次数除以搜索访客数。 您对每个访客搜索了每个搜索词。 如果这个数字很高（越接近1.0越好），则您可能会遇到以下两个问题。 单击的结果不好，您的访客正在执行多次搜索以找到最佳结果，或者他们无法通过导航找到他们要查找的页面。

如何衡量能否通过导航找到这些关键页面？ 为紧跟搜索结果页面查看的页面查看创建计算度量。 将其除以该页面的总页面查看次数。 现在，您已知道来自搜索结果的页面查看次数的百分比。 如果您的百分比很高，则可能需要在导航方面做一些工作。

### 计算量度功能强大

我希望这已经向你们展示了在计算量度中使用基本数学函数的一些可能性，并且你们将开始自己构建一些函数。 这仅从描述您可以在计算量度中进行的数学运算的可能性开始，即使使用四个简单的函数也是如此。 计算量度可以帮助您了解全新级别的访客行为，一旦您掌握了相关知识，便可以使用更复杂的功能，这些功能也可供您使用。

## 作者

本文作者：

![吉太头像](assets/gittai.png)

**Gitai Ben-Ammi**，Concentrix Catalyst 首席顾问

Adobe Analytics 负责人
