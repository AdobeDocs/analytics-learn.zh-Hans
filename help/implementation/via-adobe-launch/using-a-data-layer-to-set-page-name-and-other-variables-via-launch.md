---
title: 在Adobe Analytics通过Launch使用数据层设置页面名称和其他变量
description: 将数据层用于Analytics和其他Experience Cloud解决方案被视为最佳实践。 在此视频中，您将了解如何从数据层拉出您的值，并在Launch中使用它们来填充Adobe Analytics的变量。
feature: launch implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
translation-type: tm+mt
source-git-commit: ee6c03cff5b051d9293d75965e9fd98f151d7fce
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 4%

---


# 使用数据层通过 [!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

将数据层用于其 [!DNL Analytics] 他Experience Cloud解决方案被视为最佳实践。 在此视频中，您将了解如何从数据层提取您的值并使用它们填充 [!DNL Experience Platform Launch] Adobe Analytics的变量。

## 数据层 {#data-layers}

在处理网站和Adobe Experience Cloud解决方案上的数据时，最好使用数据层，尤其是与Adobe Analytics的数据。 _数据层_&#x200B;是指开发人员插入页面的一种 JavaScript 对象框架。The data layers can be used by tracking tools (including tag management systems like [!DNL Experience Platform Launch]) to populate reports. 在Experience Cloud文档或W3C站点上 [查找有关](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html)[层的其他信息](https://www.w3.org/)。

此外，请参阅博客数 [据层：从Buzzword到最佳实践](https://theblog.adobe.com/data-layers-buzzword-best-practice/)，它为您提供有关数据层的一些极好的信息以及几个示例。

## 数据层 [!DNL Experience Platform Launch]和Adobe Analytics（哦，我的？）{#data-layers-launch-and-adobe-analytics-oh-my}

1. 创建可在站点上使用的数据层标准，该标准可供引用 [!DNL Experience Platform Launch]。

   1. 在调用之前，将此Adobe层尽可能高地放在页面的标题中 [!DNL Experience Platform Launch][!DNL Launch]，这样，这些值可以立即被使用，并通过解决方案使用，这些解决方案需要在页面上高度，如Adobe Target。

1. 在数据层中填充数据。
1. 在中 [!DNL Experience Platform Launch]，创建引[!UICONTROL 用数据层中]数据点的“数据元素”，这些元素可以在规则、扩 [!DNL Experience Platform Launch] 展 等整个 [!UICONTROL 过程中]使用。
1. 在扩 [!UICONTROL 展全局变] 量或规则中使用数据元素 [!DNL Analytics] ，将值分配到 [!UICONTROL prop]、eArs 、PageName [!DNL Analytics] 、或其他变量中。
1. 触发向其发送数据的信标 [!DNL Analytics]。

以下视频将指导您完成该过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
