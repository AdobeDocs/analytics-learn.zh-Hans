---
title: 无标签管理器的自定义链接跟踪
description: 对于页面上的许多操作，跟踪不应被视为页面视图。 在此视频中，您将学习如何编码链接跟踪信标到Analytics（如果您未使用标签管理器）(如Experience Platform Launch)。 查看代码，以及学习重要提示。
feature: appmeasurement implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
translation-type: tm+mt
source-git-commit: 8276828e9e759a1964ca5ea89bb1395e5e78b500
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 4%

---


# 无标签管理器的自定义链接跟踪 {#custom-link-tracking-without-a-tag-manager}

对于页面上的许多操作，跟踪不应被视为页面视图。 在此视频中，您将学习如何编码链接跟踪信标到Analytics（如果您未使用标签管理器）(如Adobe [!DNL Experience Platform Launch])。 查看代码，以及学习重要提示。

## 发送s.tl()信标 {#sending-an-s-tl-beacon}

向Adobe Analytics发送数据有两个功能：

1. s.t()- “跟踪”信标，即页面视图点击、为给定页面名称增加页面视图以及设置其他变量
1. s.tl()-“跟踪链接”信标，通常称为“自定义链接”点击／信标，不会增加页面视图，并忽略pageName变量。 这通常用于跟踪页面上未加载新页面／屏幕的较小操作或不导致加载新页面的其他操作。

>[!NOTE]
>
>在此视频中，我们将向您展示如何在您未使用标签管理器(如Adobe)时编写自定义链接点击代码 [!DNL Experience Platform Launch]。 我们建议您使 [!DNL Experience Platform Launch]用我们的最佳实践建议来实施。 但是，如果您需要在中编 `s.tl()`码，请看如何进行编码。

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

有关自定义链接的详细信息，请参阅 [文档](https://marketing.adobe.com/resources/help/zh_CN/sc/implement/function_tl.html)。