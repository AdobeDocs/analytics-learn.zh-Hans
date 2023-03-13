---
title: 在不使用标签管理器的情况下进行自定义链接跟踪
description: 对于页面上的许多操作，不应将跟踪视为页面查看。 在本视频中，您将了解如何在不使用标签管理器（如 Experience Platform Launch）的情况下将链接跟踪信标编码到 Analytics。 查看代码并了解重要提示。
feature: Appmeasurement Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: Developer, Data Engineer
level: Intermediate
exl-id: e4567b1c-414e-44ad-982f-52b0150e7eda
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 100%

---

# 在不使用标签管理器的情况下进行自定义链接跟踪 {#custom-link-tracking-without-a-tag-manager}

对于页面上的许多操作，不应将跟踪视为页面查看。 在本视频中，您将了解如何在不使用标签管理器（如 Adobe [!DNL Experience Platform Launch]）的情况下将链接跟踪信标编码到 Analytics。 查看代码并了解重要提示。

## 发送 s.tl() 信标 {#sending-an-s-tl-beacon}

以下两个函数可将数据发送到 Adobe Analytics 中：

1. s.t() — 一个“跟踪”信标，它是一个页面查看点击，可增加给定页面名称的页面查看次数并设置其他变量
1. s.tl() — 一个“跟踪链接”信标，它通常称为“自定义链接”点击/信标，不会增加页面查看次数，并且将忽略 pageName 变量。 这通常用于跟踪页面上不会加载新页面/屏幕的少量操作，或不会导致新页面加载的其他操作。

>[!NOTE]
>
>在本视频中，我们将向您说明如何在不使用标签管理器（如 Adobe [!DNL Experience Platform Launch]）的情况下为自定义链接点击编码。 我们建议您使用 [!DNL Experience Platform Launch]（面向实施的最佳实践建议）。 不过，如果您需要在 `s.tl()` 中进行编码，请使用以下方式。

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12)

## 示例代码 {#sample-code}

以下是视频中的自定义链接上使用的示例代码：

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
