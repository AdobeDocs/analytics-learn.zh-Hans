---
title: 如何识别 Analytics Tracking Server 和报告包
description: 在设置 Adobe Analytics 或在其他 Experience Cloud 解决方案中引用它时，了解您所使用的 Analytics“Tracking Server”或您将数据发送到其中的“报告包”一般都很有帮助，甚至必须这样做。此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。
feature: 实施基础
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
role: “开发人员、数据工程师”
level: 初学者
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 98%

---


# 如何识别 Analytics [!DNL Tracking Server] 和[!UICONTROL 报告包]{#how-to-identify-your-analytics-tracking-server-and-report-suites}

在设置 Adobe Analytics 或在其他 Experience Cloud 解决方案中引用它时，了解您所使用的 [!DNL Analytics]“[!DNL Tracking Server]”或您将数据发送到其中的“[!UICONTROL 报告包]”一般都很有帮助，甚至必须这样做。此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。

## 实施 之后 {#after-implementation}

在网站上实施 [!DNL Analytics] 之后，即可直接在跟踪信标中找到 [!DNL tracking server] 和 [!DNL report suite ID]。[!DNL tracking server] 就是信标中的主机名，因此很方便就能找到。[!UICONTROL 报告包] ID 是信标的路径名称中紧接在“/b/ss/”后面的一个用逗号分隔的列表。

要查看信标以及发往 [!DNL Analytics] 和其他 Experience Cloud 解决方案的所有其他信息，请安装[“Experience Cloud Debugger”Chrome 扩展](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=en)。

## 实施 之前 {#before-implementation}

**[!DNL Tracking Server]** - 如果尚未开始使用您的 Adobe Analytics 实施，则您将为“.sc.omtrdc.net”选择一个子域[!DNL tracking server]。例如，我有一个在线帽子商店，称为“Jim’s Brims”。我就可以将 [!DNL tracking server] 设置为：

“jimsbrims.sc.omtrdc.net”。

**[!UICONTROL 报告包]** - 要查找您已创建的[!UICONTROL 报告包]的列表，请登录到 [!DNL Analytics]，然后在顶部菜单中转到[!UICONTROL “管理员”]>[!UICONTROL “报告包”]以查看[!UICONTROL 报告包]的列表，包括其 ID 和标题。

有关详细信息，请观看下方的视频。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12)
