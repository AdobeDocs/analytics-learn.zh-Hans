---
title: 在不使用标签管理器的情况下进行自定义链接跟踪
description: 对于页面上的许多操作，不应将跟踪视为页面查看。 在此视频中，您将了解如何在未使用标签管理器(如Experience Platform Launch)的情况下，将链接跟踪信标编码到Analytics。 查看代码，以及学习重要提示。
feature: Appmeasurement实施
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: Developer, Data Engineer
level: Intermediate
exl-id: e4567b1c-414e-44ad-982f-52b0150e7eda
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 8%

---

# 在不使用标签管理器的情况下进行自定义链接跟踪 {#custom-link-tracking-without-a-tag-manager}

对于页面上的许多操作，不应将跟踪视为页面查看。 在此视频中，您将学习如何在未使用标签管理器(如Adobe[!DNL Experience Platform Launch])的情况下，将链接跟踪信标编码到Analytics。 查看代码，以及学习重要提示。

## 发送s.tl()信标 {#sending-an-s-tl-beacon}

有两个函数可将数据发送到Adobe Analytics:

1. s.t() — “track”信标，即页面查看点击，用于递增给定页面名称的页面查看次数，以及设置其他变量
1. s.tl() — “跟踪链接”信标，通常称为“自定义链接”点击/信标，不会递增页面查看次数，并会忽略pageName变量。 它通常用于跟踪页面上未加载新页面/屏幕的较小操作，或其他不会导致新页面加载的操作。

>[!NOTE]
>
>在此视频中，我们将向您展示当您未使用标签管理器(如Adobe[!DNL Experience Platform Launch])时如何编码自定义链接点击。 我们建议您使用[!DNL Experience Platform Launch]，这是我们的实施最佳实践建议。 但是，如果您需要在`s.tl()`中进行代码，请参见下面的操作说明。

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

有关自定义链接的更多信息，请参阅[文档](https://marketing.adobe.com/resources/help/zh_CN/sc/implement/function_tl.html)。
