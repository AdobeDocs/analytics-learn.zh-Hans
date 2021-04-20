---
title: '在Adobe Analytics中跟踪单页应用程序(SPA)时使用最佳实践 '
description: 在此文档中，我们将介绍您在使用Adobe Analytics跟踪单页应用程序(SPA)时应遵循并注意的几个最佳实践。 本文档将重点介绍使用Experience Platform Launch，这是推荐的实现方法。
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: "Developer, Data Engineer"
level: Intermediate
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---


# 在Adobe Analytics {#using-best-practices-when-tracking-spa-in-adobe-analytics}中跟踪单页应用程序(SPA)时使用最佳实践

在此文档中，我们将介绍您在使用Adobe Analytics跟踪单页应用程序(SPA)时应遵循并注意的几个最佳实践。 本文档将重点介绍使用Adobe [!DNL Experience Platform Launch]，这是建议的实现方法。

初始注释：

* 以下项目将假设您使用[!DNL Experience Platform Launch]在您的站点上实施。 如果您不使用[!DNL Experience Platform Launch]，则考虑事项仍然存在，但您需要将它们调整为您的实现方法。
* 所有SPA都不同，因此您可能需要调整以下一些项目以最好地满足您的需求，但我们希望与您分享一些最佳实践；在SPA页面上实施Adobe Analytics时需要考虑的事情。

## 在[!DNL Experience Platform Launch] {#simple-diagram-of-working-with-spas-in-launch}中使用SPA的简单示意图

![在Launch中分析](assets/spa_for_analyticsinlaunch.png)

**注意：** 如上所述，这是一个简化的图表，说明在Adobe Analytics实施中如何使用SPA页面 [!DNL Experience Platform Launch]。在本页的下几节中，我们将讨论您应仔细考虑或处理的步骤和任何问题。

## 设置数据层{#setting-the-data-layer}

当新内容加载到SPA页面或在SPA页面上执行操作时，您首先应该做的事情之一是更新数据层。 这需要在自定义事件在[!DNL Experience Platform Launch]中触发并触发规则之前发生，这样[!DNL Experience Platform Launch]才能从数据层获取新值并将其推入Adobe Analytics。

下面是示例数据层，其元素可在视图更改时更改或在SPA上执行操作时更改。 例如，在全屏/多数屏幕更改中，常常会更改“[!DNL pageName]”元素，以便在[!DNL Experience Platform Launch]中捕获新元素并将其发送到Adobe Analytics。

```JavaScript
<script>
    digitalData = {
        pageInstanceID: "Launch Demo Site",
        page:{
            pageInfo:{
                pageID: '2745374',
                pageName: 'acs demo - product listing page'
            },
            attributes:{
                project: "Experience Platform Launch Project"
            }
        },
        user : [ {
          "profile" : [ {
            "attributes" : {
              "gender" : "male",
              "age" : "35"
            }
          } ]
        }],
        libraries : {
          adobe : {
            launch : {
              state : 0, // 0 = not loaded , 1 = loaded
              domain : "assets.adobedtm.com"
            }
          }
        }

     };
    </script>
```

## 在[!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}中设置自定义事件和侦听

当页面上加载新内容或站点上发生操作时，您需要通知[!DNL Experience Platform Launch]，以便它运行规则并将数据发送到[!DNL Analytics]。 有几种不同的方法可以实现：[!UICONTROL 直接调用] [!UICONTROL 规则]或自定义事件。

* [!UICONTROL 直接] [!UICONTROL 呼叫规则]:在中 [!DNL Experience Platform Launch]，您可以设置一个 [!UICONTROL 直接]  从页面调用时执行的直接callrule。如果您的页面加载或您在站点上的操作非常简单，或者它是唯一的，并且可以每次执行一组特定指令（将[!DNL eVar4]设置为X并每次触发[!DNL event2]），则您可以使用[!UICONTROL 直接调用] [!UICONTROL 规则]。 请参阅有关创建[!UICONTROL 直接调用] [!UICONTROL 规则]的[!DNL Experience Platform Launch]文档。
* 自定义事件:要获得更多功能，并且为了能够动态附加具有不同值的负载，您应设置自定义JavaScript事件并在[!DNL Experience Platform Launch]中侦听它们，在中，您可以使用负载设置变量并将数据发送到Adobe Analytics。 您更可能需要此功能，因此此选项被视为最佳实践。 但是，您网站上的每个功能都可以确定最适合的方法。 我们将在此文档中继续，假设您需要使用此自定义事件方法。

**示例：** 在 [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) THIShelp文档中，有指向已实施的示例SPA站点(和其 [!DNL Analytics] 他Experience Cloud解决方案)的链接，以及描述已实施内容的文档。在这些SPA示例中，已使用以下自定义事件:

* [!DNL event-view-start]:此事件应触发正在加载的视图/状态的视图开始。
* [!DNL event-view-end]:即使发生视图/状态更改且页面上的所有SPA组件已完成加载，也应触发此事件。这是通常触发对Adobe Analytics的调用的事件。
* [!DNL event-action-trigger]:当页面上发生除视图/状态加载外的任何事件时，此事件应触发。这可以是单击事件，也可以是内容更改较小而不更改视图。

请参阅上述引用的页面/文档，了解有关如何/何时触发这些页面/文档的更多信息。 您不必使用这些相同的事件名称，但此处列出的功能是建议的最佳实践。 以下视频将显示一个示例站点以及[!DNL Experience Platform Launch]中用于侦听自定义事件的位置。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在[!DNL Experience Platform Launch] [!UICONTROL 规则] {#running-s-t-or-s-tl-in-the-launch-rule}中运行s.t()或s.tl()

[!DNL Analytics]在使用SPA时需要了解的最重要的一点是`s.t()`和`s.tl()`之间的差异。 您将在[!DNL Experience Platform Launch]中触发其中一种方法，以将数据发送到[!DNL Analytics]，但您需要知道何时发送每种方法。

* **s.t()** - &quot;t&quot;表示&quot;track&quot;，是普通页面视图。即使URL可能不会更改，视图是否会足够更改，以便您&#x200B;*考虑*&#x200B;将其视为新的“页面”？ 如果是，请设置s.[!DNL pageName]变量并使用`s.t()`将调用发送到[!DNL Analytics]

* **s.tl()** - &quot;tl&quot;表示“跟踪链接”，通常用于跟踪页面上的点击次数或小内容更改，而非全屏更改。如果页面上的更改较小，因此您不会将其视为全新的“page”，请使用`s.tl()`并且不必担心设置s.pageName变量，因为[!DNL Analytics]将忽略该变量。

**提示：** 一些人使用一个一般的指导原则，即如果屏幕更改超过50%，应将其视为页面视图并使用 `s.t()`。如果对屏幕的更改小于50%，请使用`s.tl()`。 但是，这完全取决于您以及您认为的新“页面”以及您希望如何跟踪Adobe Analytics中的站点。

以下视频显示了在Launch by Adobe中触发`s.t()`或`s.tl()`的位置/方法。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除变量{#clearing-variables}

使用Adobe Analytics跟踪您的站点时，您当然只希望在正确的时间将正确的数据发送到[!DNL Analytics]。 在SPA环境中，在[!DNL Analytics]变量中跟踪的值可以持续存在，并可能在我们不再希望它存在时重新发送到[!DNL Analytics]中。 因此，[!DNL Analytics] [!DNL Launch]扩展中有一个用于清除变量的函数，因此，当您运行下一个图像请求并将数据发送到[!DNL Analytics]时，您将获得一个新的清单。

在上图中，我们在流程的末尾列出了它，清除在发送点击后&#x200B;*的变量*。 实际上，在发送点击之前或之后都可以执行，但应在[!DNL Experience Platform Launch]规则中保持一致，以便您始终在设置变量并发送变量之前或之后清除变量。 请记住，如果要在运行`s.t()`之前清除变量&#x200B;*，请确保先清除变量，然后设置新变量，最后将新数据发送到[!DNL Analytics]。*

**注意：** 运行时并不总是需要清除变 `s.tl()`量，因 `s.tl()` 为每次都需要 [!DNL linkTrackVars] 使用变量并排，以告 [!DNL Analytics] 知要设置哪些变量（在后台自动添加） [!DNL Experience Platform Launch]。这意味着，使用`s.tl()`时通常不会引入错误的变量，但在SPA环境中使用`s.t()`时，非常建议使用该变量。 总而言之，我建议将Clear Variables函数用于SPA环境中的`s.t()`和`s.tl()`，以确保数据收集质量，作为最佳实践。

以下视频显示了在[!DNL Launch]中清除变量的位置/方法。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他注意事项 {#additional-considerations}

### [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}中的自定义代码窗口

在[!DNL Launch] [!DNL Analytics]扩展中，有两个位置可以插入自定义代码：[!UICONTROL 库管理]部分和额外的“[!UICONTROL 使用自定义代码配置跟踪器]”部分。

![启动Analytics自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

当SPA页面上初始页面加载发生时，必须知道其中任何一个位置实际上只运行其中的代码一次。 如果您需要在视图更改或站点上的操作上运行代码，则应在相应的&#x200B;**[!UICONTROL 规则]**&#x200B;中添加一个额外的操作(例如，在“页面加载：事件-视图-end&quot; [!UICONTROL rule])，以便每次运行[!UICONTROL rule]时代码都执行。 在[!UICONTROL 规则]中创建该操作时，请设置&#x200B;*扩展=核心*&#x200B;和&#x200B;*操作类型=自定义代码*。

### &quot;Hybrid&quot; SPA/常规站点{#hybrid-spa-regular-sites}

某些站点是“常规”页面和SPA页面的组合。 在此实例中，您需要使用适用于这两种页面类型的策略。 在站点上配置自定义事件并触发[!DNL Experience Platform Launch]中的规则时，请务必注意，页面中没有基于哈希更改而进入[!DNL Analytics]的多次点击。 （如果您选择触发[!DNL Experience Platform Launch]规则的方式）。 在这种情况下，您需要禁止其中一个页面视图，以便它不会为您提供Adobe Analytics中的错误数据。

如果您决定将功能拆分为单独的[!UICONTROL 规则]，以便您能够更好地控制它，请务必记住/文档您已经这样做，以便对一个[!UICONTROL 规则]的任何更改也可以对另一个[!UICONTROL 规则]进行，保护您的[!DNL Analytics]数据完整性。

### 通过A4T {#integration-with-target-via-a4t}与[!DNL Target]集成

这里只有一个快速标注。 如果要使用A4T与[!DNL Target]集成，请确保同一视图更改上的[!DNL Target]请求和[!DNL Analytics]请求具有相同的SDID。 这将确保您的数据正确同步到解决方案。

要查看点击量，请使用调试器或数据包嗅探器项目。 您还可以使用Experience Cloud Debugger，即可下载[HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)的Chrome扩展。 [!DNL Target] 应首先在页面上触发，因此您也可以在JavaScript控制台或调试器中检查。

## 其他资源{#additional-resources}

* [SPA在Adobe论坛上的讨论](https://forums.adobe.com/thread/2451022)
* [参考体系结构站点，以说明如何在Experience Platform Launch中实现SPA](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)