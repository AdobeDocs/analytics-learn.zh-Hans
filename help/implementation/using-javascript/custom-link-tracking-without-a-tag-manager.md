---
title: 在不使用标签管理器的情况下进行自定义链接跟踪
description: 对于页面上的许多操作，不应将跟踪视为页面视图。 在此视频中，您将学习如果未使用标签管理器(如Experience Platform Launch)，如何将链接跟踪信标编码到Analytics。 查看代码，以及学习重要提示。
feature: Appmeasurement实施
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: “开发人员、数据工程师”
level: 中间
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 8%

---


# 在不使用标签管理器的情况下进行自定义链接跟踪 {#custom-link-tracking-without-a-tag-manager}

对于页面上的许多操作，不应将跟踪视为页面视图。 在此视频中，您将学习如果未使用标签管理器(如Adobe [!DNL Experience Platform Launch])，如何将链接跟踪信标编码为Analytics。 查看代码，以及学习重要提示。

## 发送s.tl()信标{#sending-an-s-tl-beacon}

将数据发送到Adobe Analytics有两个功能：

1. s.t() — “跟踪”信标，即页面视图点击，为给定页面名称增加页面视图，并设置其他变量
1. s.tl()- “跟踪链接”信标，通常称为“自定义链接”点击/信标，不会增加页面视图，并会忽略pageName变量。 这通常用于跟踪页面上未加载新页面/屏幕的较小操作，或不导致新页面加载的其他操作。

>[!NOTE]
>
>在此视频中，我们将向您介绍当您未使用标签管理器(如Adobe [!DNL Experience Platform Launch])时如何编码自定义链接点击。 我们建议您使用[!DNL Experience Platform Launch]（我们的实施最佳实践建议）。 但是，如果您需要在`s.tl()`中编码，则下面将介绍如何执行该操作。

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12)

## 示例代码 {#sample-code}

以下是视频中自定义链接上使用的示例代码：

```JavaScript
<a href="#" onclick="
    s.linkTrackVars='events,eVar2,prop2';
    s.linkTrackEvents=s.events='event2';
    s.eVar2='facebook share';
    s.prop2='facebook share';
    s.tl(this,'o','Social Share');
    s.manageVars('clearVars',s.linkTrackVars,1);">
    Click here to share on FaceBook
</a>
```

有关自定义链接的详细信息，请参阅[文档](https://marketing.adobe.com/resources/help/zh_CN/sc/implement/function_tl.html)。