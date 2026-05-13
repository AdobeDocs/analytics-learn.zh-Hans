---
title: 用 Experience Platform SDK 跟踪移动应用程序中的行为（又称自定义链接）
description: 行为是在移动应用程序中发生的事件。 在此视频中，了解如何使用 trackAction API 跟踪和度量某种行为。
feature: Mobile SDK
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: Mobile
role: Developer
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
TQID: https://experienceleague.adobe.com/msvft7mQiNGjLqGEezPIbwruvSbsunPGUIFF1q7vlT0
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 677e5a22dab92be7ff021c8410525b9091975aef
workflow-type: tm+mt
source-wordcount: 184
ht-degree: 91%

---

# 用 Experience Platform SDK 跟踪移动应用程序中的行为（又称自定义链接） {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

行为是在移动应用程序中发生的事件。 在此视频中，了解如何使用 trackAction API 跟踪和度量某种行为。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12&learn=on)

应使用此 API 跟踪您的网站上所有非屏幕加载行为。 如果屏幕即将出现，则使用 trackState，它触发一次页面查看点击。 否则，请使用 trackAction 发送与正在发生的行为相关的变量。

这些数据采用 `contextData` 的形式，这还意味着您随后需要使用[!UICONTROL 处理规则]从这些 `contextData` 变量取得移动数据并将其映射到 Adobe Analytics 中的 [!DNL eVars]、[!DNL Props]、事件等等。

有关 trackAction 的详细信息，请参阅[文档](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/#track-user-actions-for-adobe-analytics)。
