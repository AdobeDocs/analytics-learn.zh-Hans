---
title: 使用Experience PlatformSDK在移动应用程序中跟踪操作（AKA自定义链接）
description: '操作是在您的移动应用程序中发生的事件。 在此视频中，了解如何使用trackAction API跟踪和衡量操作。 '
feature: mobile sdk
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
translation-type: tm+mt
source-git-commit: a42658cfd4bae7b077ddd48b4cf5c7db54e35c98
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# 使用Experience PlatformSDK在移动应用程序中跟踪操作（AKA自定义链接） {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

操作是在您的移动应用程序中发生的事件。 在此视频中，了解如何使用trackAction API跟踪和衡量操作。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12)

这是您应用来跟踪站点上所有非屏幕加载操作的API。 如果屏幕出现，则使用trackState，它触发页面视图点击。 否则，请使用trackAction发送与正在执行的操作关联的变量。

此数据的 `contextData`引入也意味着您随后需要使用处理 [!UICONTROL 规则] ，从这些变量中提取移动 `contextData` 数据并将其映射 [!DNL eVars]到、 [!DNL Props]事件等。 adobe analytics。

有关trackAction的更多信息，请参阅 [文档](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference)。
