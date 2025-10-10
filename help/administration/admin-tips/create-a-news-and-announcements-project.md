---
title: 创建新闻和公告项目
description: 在工作区内创建一个以文本为主的新闻和公告项目，并与整个公司共享。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10535.jpg
kt: 10535
exl-id: 1474e117-8668-4f21-ba86-e3fb88d98468
source-git-commit: df00d4fb8cc5093903ed4628dfe12f152294123a
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 100%

---

# 创建新闻和公告项目

**内容：**&#x200B;在工作区内创建一个以文本为主的新闻和公告项目，并与整个公司共享。您不需要强制将此作为登录页提供给用户（但您可以这样做），这是因为每次更新时，它都会浮到用户列表的顶部。

**原因：**&#x200B;您的用户可能不希望每次在 Adobe Analytics 中的某些内容发生更改时就会收到一封电子邮件。期望用户定期查看 Adobe Analytics 内部站点（Confluence 或其他，请参阅[创建 Adobe Analytics 内部站点](create-an-internal-adobe-analytics-site.md)提示）有些困难。相反，您可以利用工作区，这样他们就不必离开界面。每次登录时，他们都会看到新闻和公告仪表板。

**方法：**&#x200B;登录到工作区并创建新项目。确保在项目设置中与组织中的所有人共享此项目。该项目的顶部（描述）可以指向您的 Adobe Analytics 内部站点，并调出最佳联系人或 DL。然后，我建议设置四个基于文本的分区：
1. 新版本和功能：
   * 按年份（如果您有大量数据，则按月份）根据时间顺序排列项目符号，最新的项目位于顶部
   * 这些可能包括 Adobe 的新功能、新变量/事件、新站点/应用程序、正在跟踪的新功能等。
   * 项目符号内应包含日期、受影响的属性（如适用）和少量细节
1. 概述仪表板列表：
   * 强烈建议为您所有的主要属性或其他较大类别的内容设置概述仪表板。通过创建这些仪表板可避免大量的临时报告，并可帮助用户快速全面了解某一属性，而无需寻求其他帮助。这些应与整个公司共享，并标记为“概述仪表板”。我还建议创建一个“所有站点和应用程序的概述”仪表板，以便用户了解整个数字环境，以及特定属性在整个环境内所处的位置。
   * 以简单的项目符号格式列出所有这些内容，并直接链接每个仪表板。
1. 供您查看的精彩报告：
   * 通过展示您最佳的仪表板和 Adobe Analytics 的功能，吸引用户的兴趣。使这些仪表板具备通用性，让更多的受众能够访问。
   * 以项目符号的格式列出这些内容，将用户直接链接到仪表板。对其进行简要地描述也会有所帮助。
1. 已知漏洞、错误和更改：
   * 可以在 Excel 中记录错误和更改信息，但很容易忘记对其进行更新。用户也不会主动检查保存在平台之外的电子表格。将所有内容都保存在界面内有助于更新，也更容易让用户注意到。
   * 这是一个非常简单的解决方案，没有什么特别之处，这也意味着它很容易维护。

## 作者

本文件由以下人员共同编写：

![Christel Guidon](assets/Christel-Headshot-150.png)

NortonLifeLock 数字分析平台经理 Christel Guidon
Adobe Analytics Champion

![Rachel Fenwick](assets/Rachel-Fenwick-150.png)

Adobe 高级顾问 Rachel Fenwick
