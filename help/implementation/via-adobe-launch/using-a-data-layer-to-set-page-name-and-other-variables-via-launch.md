---
title: 使用数据层通过 Tags 设置 Analytics 变量
description: 了解如何使用数据层来获取 Analytics 数据和其他 Experience Cloud 解决方案。
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: 8fc641743bc9e07b838a22ca64ccc15344d52764
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# 使用数据层通过 [!DNL Tags] 设置 Analytics 变量 {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

最佳实践就是将数据层用于 [!DNL Analytics] 和其他 Experience Cloud 解决方案。 在本视频中，您将了解如何从数据层中提取值，并用于在 [!DNL Experience Platform Tags] 中填充 Adobe Analytics 中的变量。

## 数据层 {#data-layers}

_数据层_&#x200B;是开发人员添加到数字网页的 JavaScript 对象框架。 Analytics 解决方案最终使用数据层填充报告。 Tag Management 系统，包括 [!DNL Experience Platform Tags] 是读取数据层、将值映射到变量并将数据发送到数字体验解决方案的中介。

在 [Experience Cloud 文档](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hans)和博文[数据层：从 Buzzword 到最佳实践](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice)中查看有关数据层的其他信息。

## 数据层、[!DNL Experience Platform Tags] 和 Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 定义或确定要在站点上使用的数据层标准。

   1. 在调用 [!DNL Experience Platform Tags] 之前，请将数据层放置在页面头部尽可能高的位置。这样可以确保 [!DNL Tags] 以及需要显示在页面上较高位置的 Adobe 解决方案（如 Adobe Target）可以立即访问这些值。

1. 在数据层中填充数据。
1. 在 [!DNL Experience Platform Tags]中， 创建“[!UICONTROL 数据元素]”映射数据层中的数据点。 这些数据元素在整个 [!DNL Experience Platform Tags] 的[!UICONTROL 规则]和[!UICONTROL 扩展]中使用。
1. 在 [!DNL Analytics] 扩展的全局变量部分或 [!DNL Tags rule] 中，将[!UICONTROL 数据元素]中的值分配给 [!UICONTROL props]、[!UICONTROL eVars]、[!UICONTROL pageName] 和其他 [!DNL Analytics] 变量。
1. 触发将数据发送到 [!DNL Analytics] 中的信标。

以下视频将引导您完成此过程。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12&learn=on)

>[!NOTE]
>
>本视频中使用的特定数据层可能不被视为您组织的最佳实践。 使用数据层将重要数据呈现给数字营销解决方案的概念属于最佳实践。