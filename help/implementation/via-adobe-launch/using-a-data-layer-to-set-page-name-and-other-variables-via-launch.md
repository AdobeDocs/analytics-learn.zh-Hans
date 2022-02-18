---
title: 使用数据层通过 Launch 在 Adobe Analytics 中设置页面名称和其他变量
description: 将数据层用于 Analytics 和其他 Experience Cloud 解决方案被视为最佳实践。 在本视频中，您将了解如何从数据层中提取值并在 Launch 中使用它们来填充 Adobe Analytics 中的变量。
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
workflow-type: ht
source-wordcount: '365'
ht-degree: 100%

---

# 使用数据层通过 [!DNL Experience Platform Launch] 设置页面名称和其他变量 {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

将数据层用于 [!DNL Analytics] 和其他 Experience Cloud 解决方案被视为最佳实践。 在本视频中，您将了解如何从数据层中提取值并在 [!DNL Experience Platform Launch] 中使用它们来填充 Adobe Analytics 中的变量。

## 数据层 {#data-layers}

最佳实践是，在您的网站和 Adobe Experience Cloud 解决方案（尤其是 Adobe Analytics）中处理数据时使用数据层。 _数据层_&#x200B;是指开发人员插入页面的一种 JavaScript 对象框架。 数据层可供跟踪工具（包括诸如 [!DNL Experience Platform Launch] 之类的标记管理系统）用来填充报表。 在 [Experience Cloud 文档](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hans)或 [W3C 站点](https://www.w3.org/)中查找有关数据层的其他信息。

此外，请参阅博客[数据层：从热词到最佳实践](https://theblog.adobe.com/data-layers-buzzword-best-practice/)，其中为您提供了有关数据层的一些重要信息以及几个示例。

## 数据层、[!DNL Experience Platform Launch] 和 Adobe Analytics{#data-layers-launch-and-adobe-analytics-oh-my}

1. 创建一个数据层标准以在您的站点上使用，[!DNL Experience Platform Launch] 可参考此标准。

   1. 在调用 [!DNL Experience Platform Launch] 之前，将此数据层放在页面顶部尽可能高的位置，以便 [!DNL Launch] 和需要在页面上方的 Adobe 解决方案（如 Adobe Target）能够立即使用这些值。

1. 在数据层中填充数据。
1. 在 [!DNL Experience Platform Launch] 中，创建“[!UICONTROL 数据元素]”，这些元素引用数据层中的数据点，并且可在 [!DNL Experience Platform Launch] 中的 [!UICONTROL 规则]、[!UICONTROL 扩展]等中使用。
1. 在 [!DNL Analytics] 扩展全局变量或规则中使用[!UICONTROL 数据元素]，并将在 [!UICONTROL props]、[!UICONTROL eVars]、[!UICONTROL pageName] 或其他 [!DNL Analytics] 变量中指定值。
1. 触发将数据发送到 [!DNL Analytics] 中的信标。

以下视频将引导您完成此过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
