---
title: '在Adobe Analytics使用跟踪单页应用程序(SPA)的最佳实践 '
description: 在此文档中，我们将介绍您在使用Adobe Analytics跟踪单页应用程序(SPA)时应遵循和注意的几种最佳实践。 本文档将重点介绍使用Experience Platform Launch，这是推荐的实现方法。
feature: implementation basics
topics: spa
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
translation-type: tm+mt
source-git-commit: 548ac75589383dfd4da4ae02412de91a0a3b28d6
workflow-type: tm+mt
source-wordcount: '1669'
ht-degree: 0%

---


# 在Adobe Analytics使用跟踪单页应用程序(SPA)的最佳实践 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在此文档中，我们将介绍您在使用Adobe Analytics跟踪单页应用程序(SPA)时应遵循和注意的几种最佳实践。 本文档将重点介绍使用Adobe [!DNL Experience Platform Launch]，这是推荐的实现方法。

初始注释：

* 以下项目将假定您正在使用在 [!DNL Experience Platform Launch] 您的网站上实施。 如果您不使用，则仍会存 [!DNL Experience Platform Launch]在考虑因素，但您需要将其调整为您的实现方法。
* 所有SPA都不同，因此您可能需要调整以下一些项目以最好地满足您的需求，但我们希望与您分享一些最佳实践；在SPA页面上实施Adobe Analytics时需要考虑的事情。

## 在 [!DNL Experience Platform Launch] {#simple-diagram-of-working-with-spas-in-launch}

![在启动中进行分析的spa](assets/spa_for_analyticsinlaunch.png)

**注意：** 如上所述，这是一个简化的图表，说明在Adobe Analytics实施中如何使用SPA页面 [!DNL Experience Platform Launch]。 在本页的下几节中，我们将讨论这些步骤以及您应该仔细考虑或处理的任何问题。

## 设置数据层 {#setting-the-data-layer}

当新内容加载到SPA页面或在SPA页面上执行操作时，您应首先执行的操作之一是更新数据层。 在自定义事件触发并触发规则之前，需要先执行此 [!DNL Experience Platform Launch]操作， [!DNL Experience Platform Launch] 这样才能从数据层获取新值并将其推入Adobe Analytics。

下面是示例数据层，其元素可在视图更改或SPA操作时进行更改。 例如，在全屏／多数屏幕更改中，常常会更改“[!DNL pageName]”元素，以便新元素能够被捕获并发 [!DNL Experience Platform Launch] 送到Adobe Analytics。

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

## 设置自定义事件和监听 [!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}

当页面上加载新内容或站点上执行操作时，您需要通 [!DNL Experience Platform Launch] 知以运行规则并将数据发送到 [!DNL Analytics]。 有几种不同的方法可以实现此目的： [!UICONTROL 直接呼叫][!UICONTROL 规则] 或自定义事件。

* [!UICONTROL 直接呼叫][!UICONTROL 规则]:在中 [!DNL Experience Platform Launch]，您可以设置一 [!UICONTROL 个直接调用规] 则，该规则在从页面直接  调用时执行。 如果页面加载或网站操作非常简单，或者它是唯一的，并且每次都可以执行一组特定指令(设置 [!DNL eVar4] 为X并 [!DNL event2] 每次触发)，则可以使用直 [!UICONTROL 接呼] 叫规则 。 请参 [!DNL Experience Platform Launch] 阅有关创建直接 [!UICONTROL 呼叫规] 则 [!UICONTROL 的文档]。
* 自定义事件:要获得更多功能，并且为了能够动态附加具有不同值的有效负荷，您应设置自定义JavaScript事件并在中侦听它们，在该中，您可以使用有效负荷设置变量并将数据发送到Adobe Analytics。 [!DNL Experience Platform Launch]您更可能需要此功能，因此此选项被视为最佳实践。 但是，站点上的每个功能都可以确定最适合的方法。 我们将在此文档中继续，假定您需要使用此自定义事件方法。

**示例：** 在此 [帮助](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 文档中，有指向已实施的示例SPA站点(和其他 [!DNL Analytics] Experience Cloud解决方案)的链接，以及描述已实施内容的文档。 在这些SPA示例中，已使用以下自定义事件:

* [!DNL event-view-start]:此事件应触发正在加载的视图/状态的视图开始。
* [!DNL event-view-end]:即使发生视图/状态更改且页面上的所有SPA组件已完成加载，也应触发此事件。 这是事件，通常触发呼叫Adobe Analytics。
* [!DNL event-action-trigger]:当页面上发生除视图/状态加载外的任何事件时，此事件应触发。 这可以是单击事件，也可以是内容更改较小而不更改视图。

请参阅上述引用的页面／文档，了解有关如何／何时激发这些页面／文档的更多信息。 您不必使用这些相同的事件名称，但此处列出的功能是建议的最佳实践。 以下视频将显示示例站点以及在 [!DNL Experience Platform Launch] 何处监听自定义事件。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在规则中运行s.t()或s.tl( [!DNL Experience Platform Launch][!UICONTROL )] {#running-s-t-or-s-tl-in-the-launch-rule}

使用SPA时，最需要了解 [!DNL Analytics] 的一件重要事情是 `s.t()` 和 `s.tl()`。 您将在中触发其中一种方 [!DNL Experience Platform Launch] 法来发送数 [!DNL Analytics]据，但您需要知道何时发送每种方法。

* **s.t()** - “t”表示“track”，是普通页面视图。 即使URL可能没有更改，视图是否更改得足 *够* ，您是否将其视为新“页面”? 如果是，请设置s。[!DNL pageName] 变量，并 `s.t()` 用于将调用发送到 [!DNL Analytics]

* **s.tl()** - &quot;tl&quot;表示“跟踪链接”，通常用于跟踪页面上的点击次数或小内容更改，而非全屏更改。 如果页面上的更改很小，因此您不会将其视为全新的“页面”，请使用 `s.tl()` s.pageName变量，并且不要担心设置，因 [!DNL Analytics] 为将忽略它。

**提示：** 一些人使用一般准则，如果屏幕变化超过50%，则应将其视为页面视图并使用 `s.t()`。 如果屏幕更改率低于50%，则使用 `s.tl()`。 但是，这完全取决于您以及您对新“页面”的看法，以及您希望如何跟踪您在Adobe Analytics的网站。

以下视频显示触发或Launch by Adobe `s.t()` 的 `s.tl()` 位置／方法。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除变量 {#clearing-variables}

当您使用Adobe Analytics跟踪您的网站时，您当然只希望在正确的时间将正确的 [!DNL Analytics] 数据发送到正确的位置。 在SPA环境中，在变量中跟踪的 [!DNL Analytics] 值可以保留并重新发送 [!DNL Analytics]到该变量中，当我们不再希望它时。 因此，扩展中有一个函 [!DNL Analytics] 数可清 [!DNL Launch] 除变量，这样运行下一个图像请求并将数据发送到中时，您会得到一个新的状态 [!DNL Analytics]。

在上图中，我们在流程结束时列出了它，在发送点击后 *清* 除变量。 实际上，它可以在发送点击之前或之后执行，但应在规则中保持一致，这样您始终可以在设置变量并发送它们之前 [!DNL Experience Platform Launch] 或之后清除它们。 请记住，如果要在运行前清 *除变量* , `s.t()`请确保先清除变量，然后设置新变量，最后将新数据发送到 [!DNL Analytics]。

**注意：** 运行变量时并不总是需要清 `s.tl()`除变量， `s.tl()` 因为每次都需要使用变量 [!DNL linkTrackVars] 并排，以告知要设置 [!DNL Analytics] 的变量(在后台自动添加 [!DNL Experience Platform Launch])。 这意味着，使用时通常不会引入错误的变 `s.tl()`量，但在SPA环境中使用时，会 `s.t()` 非常推荐这些变量。 所以，我建议将它作为SPA环境中和SPA中使用Clear Variables `s.t()` 函 `s.tl()` 数的最佳实践，仅为确保高质量的数据收集。

以下视频显示了在何处／如何清除变量 [!DNL Launch]。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他注意事项 {#additional-considerations}

### 自定义代码窗口 [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}

在扩展 [!DNL Launch] 中，有两 [!DNL Analytics] 个位置可以插入自定义代码：库管 [!UICONTROL 理部分] ，以及额外的“使用自[!UICONTROL 定义代码配置跟踪器]”部分。

![启动Analytics自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

当SPA页面上初始页面加载发生时，必须知道其中任何一个位置实际上只运行其中的代码一次。 如果您需要在视图更改或站点上的操作上运行代码，则应将其他操作添加到相应 **[!UICONTROL 规则]** (例如，在“页面加载：事件-- [!UICONTROL 视图]-结束”规则)，以便代码每次运行 [!UICONTROL 时执行] 。 在规则中创建该操 [!UICONTROL 作]时， *设置* “扩展” *=“核心”*，并设置“操作类型”=“自定义代码”。

### “混合”SPA/常规站点 {#hybrid-spa-regular-sites}

某些站点是“常规”页面和SPA页面的组合。 在此实例中，您需要使用适用于这两种页面类型的策略。 在站点上配置自定义事件并在中触发规则 [!DNL Experience Platform Launch]时，请注意，页面中没有基于哈希 [!DNL Analytics] 更改等的多次点击。 (如果您选择通过这种方式触发 [!DNL Experience Platform Launch] 规则)。 在这种情况下，您需要禁止其中一个页面视图，这样您就不会在Adobe Analytics发现错误数据。

如果您决定将功能分解为单独的 [!UICONTROL 规则] ，以便能够更好地控制它，请务必记住/文档您已经完成了这一操作，这样，对一个规则  的任何更改也可以对另一个规则 [!UICONTROL 进行更改，从而保护您的][!DNL Analytics] 数据完整性。

### 通过A4T [!DNL Target] 与集成 {#integration-with-target-via-a4t}

这里只有一个快速标注。 如果要与使 [!DNL Target] 用A4T进行集成，请确保同一视图 [!DNL Target] 更改中 [!DNL Analytics] 的请求和请求具有相同的SDID。 这将确保您的数据在解决方案上正确同步。

要查看点击，请使用调试器或数据包嗅探器项目。 您还可以使用Experience Cloud Debugger，即可在此处下载的Chrome扩 [展](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)。 [!DNL Target] 应该首先在页面上触发，因此您还可以在JavaScript控制台或调试器中检查该操作。

## 其他资源 {#additional-resources}

* [Adobe论坛上的SPA讨论](https://forums.adobe.com/thread/2451022)
* [参考体系结构站点，展示如何在Experience Platform Launch中实现SPA](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)