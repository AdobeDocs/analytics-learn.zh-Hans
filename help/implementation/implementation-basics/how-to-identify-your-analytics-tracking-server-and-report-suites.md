---
title: 如何识别分析跟踪服务器和报表包
description: 在设置Adobe Analytics时，或在其他Experience Cloud解决方案中引用它时，通常有帮助甚至有必要了解您使用的Analytics“跟踪服务器”，或者您向其中发送数据的“报告包”。 此视频向您展示如何找到这两个值，无论您是否已实现Adobe Analytics。
feature: implementation basics
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
translation-type: tm+mt
source-git-commit: 60f4ce4f563a990576b3331b01cd87c29d424f43
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# 如何识别分析 [!DNL Tracking Server] 和报 [!UICONTROL 表包] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

在设置Adobe Analytics时，或在其他Experience Cloud解决方案中引用它时，通常有帮助甚至有必要了解您正在使用的 [!DNL Analytics] “[!DNL Tracking Server]”，或者您正在向其发送数据的“[!UICONTROL 报告包]”。 此视频向您展示如何找到这两个值，无论您是否已实现Adobe Analytics。

## 实施后 {#after-implementation}

在网 [!DNL Analytics] 站上实施后，您可以在跟踪 [!DNL tracking server] 信标中 [!DNL report suite ID] 找到相应的和右侧。 信标 [!DNL tracking server] 中的主机名是主机名，因此很容易找到。 报 [!UICONTROL 表包] ID是信标路径名中“/b/ss/”后以逗号分隔的列表。

要查看信标以及所有其他Experience Cloud解决方案 [!DNL Analytics] 的信息，请安装“ [Experience Cloud Debugger”Chrome扩展](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=en)。

## 实施前 {#before-implementation}

**[!DNL Tracking Server]** -如果您尚未开始Adobe Analytics实施，则将为“.sc.omtrdc.net”选择子域 [!DNL tracking server]。 例如，假设我有一个名为“Jim’s Brims”的在线帽子商店。 我只需设置 [!DNL tracking server] 为：

“jimsbrims.sc.omtrdc.net”。

**[!UICONTROL 报表包]** -要查找已创建的报 [!UICONTROL 表包的列表] ，请登录并转到顶部菜单中的“管 [!DNL Analytics] 理员 [!UICONTROL ”>“报]表包”，查看列表报告包的，包括ID和标题。

有关详细信息，请观看以下视频。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12)
