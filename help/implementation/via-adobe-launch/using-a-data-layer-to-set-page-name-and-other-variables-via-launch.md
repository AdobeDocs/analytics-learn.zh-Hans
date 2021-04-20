---
title: 在Adobe Analytics中通过Launch使用数据层设置页面名称和其他变量
description: 将数据层用于Analytics和其他Experience Cloud解决方案被视为最佳实践。 在此视频中，您将了解如何从数据层中提取值并在Launch中使用它们来填充Adobe Analytics中的变量。
feature: Launch Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: "Developer, Data Engineer"
level: Beginner
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 7%

---


# 使用数据层通过 设置页码和其他变量[!DNL Experience Platform Launch]{#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

将数据层用于[!DNL Analytics]和其他Experience Cloud解决方案被认为是最佳实践。 在此视频中，您将了解如何从数据层中提取值并在[!DNL Experience Platform Launch]中使用它们来填充Adobe Analytics中的变量。

## 数据层{#data-layers}

使用数据层处理站点和Adobe Experience Cloud解决方案上的数据(尤其是与Adobe Analytics一起使用)是最佳做法。 _数据层_&#x200B;是指开发人员插入页面的一种 JavaScript 对象框架。跟踪工具（包括[!DNL Experience Platform Launch]等标签管理系统）可以使用数据层来填充报表。 在[Experience Cloud文档](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html)或[W3C站点](https://www.w3.org/)中查找有关数据层的其他信息。

此外，请参阅博客[数据层：从Buzzword到最佳实践，](https://theblog.adobe.com/data-layers-buzzword-best-practice/)为您提供有关数据层的一些极好的信息以及几个示例。

## 数据层、[!DNL Experience Platform Launch]和Adobe Analytics(oh my?){#data-layers-launch-and-adobe-analytics-oh-my}

1. 创建可在站点上使用的数据层标准，[!DNL Experience Platform Launch]可引用该标准。

   1. 在调用[!DNL Experience Platform Launch]之前，将此Adobe层尽可能高地放在页面的头中，以便让[!DNL Launch]和页面上需要高的解决方案(如Adobe Target)立即使用这些值。

1. 在数据层中填充数据。
1. 在[!DNL Experience Platform Launch]中，创建引用数据层中数据点的“[!UICONTROL 数据元素]”，可在[!UICONTROL 规则]、[!UICONTROL 扩展]等的[!DNL Experience Platform Launch]中使用。
1. 在[!DNL Analytics]扩展全局变量或规则中使用[!UICONTROL 数据元素]，将值分配到[!UICONTROL props]、[!UICONTROL  eVars]、[!UICONTROL pageName]或其他[!DNL Analytics]变量中。
1. 触发将数据发送到[!DNL Analytics]的信标。

以下视频将指导您完成该过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
