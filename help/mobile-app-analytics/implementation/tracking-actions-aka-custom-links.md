---
title: 用 Experience Platform SDK 跟踪移动应用程序中的行为（又称自定义链接）
description: '行为是在移动应用程序中发生的事件。在此视频中，了解如何使用 trackAction API 跟踪和度量某种行为。 '
feature: Mobile SDK
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: 移动设备
role: '"开发人员、数据工程师"'
level: 熟练
translation-type: ht
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: ht
source-wordcount: '181'
ht-degree: 100%

---


# 用 Experience Platform SDK 跟踪移动应用程序中的行为（又称自定义链接）{#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

行为是在移动应用程序中发生的事件。在此视频中，了解如何使用 trackAction API 跟踪和度量某种行为。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12)

应使用此 API 跟踪您的网站上所有非屏幕加载行为。如果屏幕即将出现，则使用 trackState，它触发一次页面查看点击。否则，请使用 trackAction 发送与正在发生的行为相关的变量。

这些数据采用 `contextData` 的形式，这还意味着您随后需要使用[!UICONTROL 处理规则]从这些 `contextData` 变量取得移动数据并将其映射到 Adobe Analytics 中的 [!DNL eVars]、[!DNL Props]、事件等等。

有关 trackAction 的详细信息，请参阅[文档](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference)。
