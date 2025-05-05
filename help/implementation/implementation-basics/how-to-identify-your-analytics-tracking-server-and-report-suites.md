---
title: 如何标识分析跟踪服务器和报告包 ID
description: 在设置 Adobe Analytics 或在其他 Experience Cloud 解决方案中引用它时，了解您所使用的 Analytics“跟踪服务器”或您将数据发送到其中的“报告包”一般都很有帮助，甚至必须这样做。此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。
feature: Implementation Basics
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
role: Developer, Data Engineer
level: Beginner
exl-id: 3925026f-69f1-4425-b3a9-6fef26375fed
source-git-commit: 42bf16df9585d1f41206b81bf509a72c10f1d7f2
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---

# 如何标识 Analytics [!DNL tracking server]和[!UICONTROL 报告包 ID] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

在设置 Adobe Analytics 或在其他 Experience Cloud 解决方案中引用它时，了解您所使用的 Analytics“跟踪服务器”或您将数据发送到其中的[!UICONTROL 报告包]一般都很有帮助，甚至必须这样做。此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。

>[!IMPORTANT]
>
>本文和视频适用于 Adobe Analytics 的“AppMeasurement”实施，而不是使用 Web SDK 的实施。

## 实施之后 {#after-implementation}

在网站上实施 Analytics 之后，即可直接在跟踪信标中找到 [!DNL tracking server] 和 [!DNL report suite ID]。[!DNL tracking server] 就是信标中的主机名，因此很方便就能找到。[!UICONTROL 报告包] ID 是信标的路径名称中紧接在“/b/ss/”后面的一个用逗号分隔的列表。

要查看信标以及发往 Analytics 和其他 Experience Cloud 解决方案的所有其他信息，请安装[“Experience Cloud Debugger”Chrome 扩展](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=zh-Hans)。

## 实施之前 {#before-implementation}

**[!DNL Tracking server]** - 如果尚未开始使用您的 Adobe Analytics 实施，则您将为“.sc.omtrdc.net”[!DNL tracking server]选择一个子域。例如，我有一个在线帽子商店，称为“Jim&#39;s Brims”。我就可以将 [!DNL tracking server] 设置为：

“jimsbrims.sc.omtrdc.net”。

**[!UICONTROL 报告包]** - 要查找您已创建的[!UICONTROL 报告包]的列表，请登录到 [!DNL Analytics]，然后在顶部菜单中转到[!UICONTROL “管理员”]>[!UICONTROL “报告包”]，查看[!UICONTROL 报告包]的列表，包括其 ID 和标题。

有关详细信息，请观看下方的视频。

>[!VIDEO](https://video.tv.adobe.com/v/40898/?quality=12&learn=on&captions=chi_hans)
