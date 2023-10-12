---
title: 如何识别Analytics跟踪服务器和报表包ID
description: 在设置Adobe Analytics或在其他Experience Cloud解决方案中引用它时，了解您所使用的Analytics“Tracking Server”或您将数据发送到其中的“报表包”一般都很有帮助，甚至必须这样做。 此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。
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
source-wordcount: '330'
ht-degree: 17%

---

# 如何识别您的分析 [!DNL tracking server] 和 [!UICONTROL 报告包ID] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

在设置Adobe Analytics或在其他Experience Cloud解决方案中引用它时，了解您所使用的Analytics“tracking server”或“[!UICONTROL 报告包]”将数据发送到中。 此视频介绍如何找到这两个值，无论您是否已实施了 Adobe Analytics。

>[!IMPORTANT]
>
>本文和视频适用于Adobe Analytics的“AppMeasurement”实施，而不适用于使用Web SDK的实施。

## 实施之后 {#after-implementation}

在网站上实施Analytics后，您可以找到 [!DNL tracking server] 和 [!DNL report suite ID] 就在追踪信标里。 此 [!DNL tracking server] 就是信标中的主机名，因此很方便就能找到。 此 [!UICONTROL 报告包] ID是信标的路径名称中紧接在“/b/ss/”后面的一个以逗号分隔的列表。

要查看信标以及发往Analytics和其他Experience Cloud解决方案的所有其他信息，请安装 [“Experience Cloud Debugger”Chrome扩展](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=zh-Hans).

## 实施之前 {#before-implementation}

**[!DNL Tracking server]**  — 如果尚未开始实施Adobe Analytics，则您将为“.sc.omtrdc.net”选择一个子域 [!DNL tracking server]. 例如，假设我有一家在线帽子商店，名为“Jim’s Brims”。 我就可以将 [!DNL tracking server] 设置为：

“jimsbrims.sc.omtrdc.net”。

**[!UICONTROL 报表包]**  — 查找您的 [!UICONTROL 报表包] 已创建的，请登录 [!DNL Analytics] 并转到 [!UICONTROL 管理员] > [!UICONTROL 报表包] 以查看 [!UICONTROL 报表包]，包括其ID和标题。

有关详细信息，请观看下方的视频。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12&learn=on)
