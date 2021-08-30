---
title: 使用数据层通过Launch在Adobe Analytics中设置页面名称和其他变量
description: 将数据层用于Analytics和其他Experience Cloud解决方案被视为最佳实践。 在此视频中，您将了解如何从数据层中提取值，并在Launch中使用它们来填充Adobe Analytics中的变量。
feature: Launch Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: Developer, Data Engineer
level: Beginner
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 7%

---

# 使用数据层通过 设置页码和其他变量[!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

将数据层用于[!DNL Analytics]和其他Experience Cloud解决方案被视为最佳实践。 在此视频中，您将了解如何从数据层中提取值，并在[!DNL Experience Platform Launch]中使用它们来填充Adobe Analytics中的变量。

## 数据层 {#data-layers}

在处理网站上的数据以及Adobe Experience Cloud解决方案(特别是与Adobe Analytics一起使用)时，最好使用数据层。 _数据层_&#x200B;是指开发人员插入页面的一种 JavaScript 对象框架。数据层可供跟踪工具（包括[!DNL Experience Platform Launch]等标签管理系统）用来填充报表。 在[Experience Cloud文档](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=en)或在[W3C站点](https://www.w3.org/)上查找有关数据层的其他信息。

此外，请参阅博客[数据层：从Buzzword到最佳实践，](https://theblog.adobe.com/data-layers-buzzword-best-practice/)，它为您提供了一些有关数据层的重要信息以及几个示例。

## 数据层、 [!DNL Experience Platform Launch]和Adobe Analytics（哦，my？）{#data-layers-launch-and-adobe-analytics-oh-my}

1. 创建要在您的网站上使用的数据层标准，[!DNL Experience Platform Launch]可引用该标准。

   1. 在调用[!DNL Experience Platform Launch]之前，将此数据层尽可能放置在页面标题中的较高位置，以便[!DNL Launch]和需要在页面上显示较高值的Adobe解决方案(如Adobe Target)可以立即使用这些值。

1. 在数据层中填充数据。
1. 在[!DNL Experience Platform Launch]中，创建引用数据层中数据点的“[!UICONTROL 数据元素]”，该数据元素可在[!UICONTROL 规则]、[!UICONTROL 扩展]等的整个[!DNL Experience Platform Launch]中使用。
1. 在[!DNL Analytics]扩展全局变量或规则中使用[!UICONTROL 数据元素]，将值分配到[!UICONTROL props]、[!UICONTROL eVars]、[!UICONTROL pageName]或其他[!DNL Analytics]变量中。
1. 触发将数据发送到[!DNL Analytics]的信标。

以下视频将指导您完成该过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
