---
title: 使用数据层通过“标记”设置Analytics变量
description: 了解如何使用数据层来源补充Analytics数据和其他Experience Cloud解决方案。
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 9%

---

# 使用数据层通过 [!DNL Tags] {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

使用数据层 [!DNL Analytics] 而其他Experience Cloud解决方案则是最佳实践。 在此视频中，了解如何从数据层提取值并在 [!DNL Experience Platform Tags] 以在Adobe Analytics中填充变量。

## 数据层 {#data-layers}

A _数据层_ 是开发人员添加到数字网页的JavaScript对象框架。 Analytics解决方案最终会使用数据层来填充报表。 标签管理系统，包括 [!DNL Experience Platform Tags])是读取数据层、将值映射到变量，并将该数据发送到数字体验解决方案的中介。

在 [Experience Cloud文档](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hans) 和博客 [数据层：从流行词汇到最佳实践](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice).

## 数据层、 [!DNL Experience Platform Tags]和Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 定义或识别要在网站上使用的数据层标准。

   1. 在调用之前，将数据层尽可能放在页面的标题部分中 [!DNL Experience Platform Tags]. 这可确保值被 [!DNL Tags] 以及需要在页面上显示较高位置的Adobe解决方案，例如Adobe Target。

1. 在数据层中填充数据。
1. 在 [!DNL Experience Platform Tags]，创建&quot;[!UICONTROL 数据元素]”来映射数据层中的数据点。 这些数据元素在整个 [!DNL Experience Platform Tags] in [!UICONTROL 规则] 和 [!UICONTROL 扩展].
1. 在 [!DNL Analytics] 扩展的全局变量部分或 [!DNL Tags rule]，在中分配值 [!UICONTROL 数据元素] to [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName]，等等 [!DNL Analytics] 变量。
1. 触发将数据发送到 [!DNL Analytics] 中的信标。

以下视频将引导您完成此过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)

>[!NOTE]
>
>此视频中使用的特定数据层可能不被视为贵组织的“最佳实践”。 最佳做法是使用数据层向您的数字营销解决方案显示重要数据。