---
title: '在Adobe Analytics中使用跟踪单页应用程序(SPA)的最佳实践 '
description: 在本文档中，我们将介绍在使用Adobe Analytics跟踪单页应用程序(SPA)时，您应遵循并注意的一些最佳实践。 本文档将重点介绍如何使用Experience Platform Launch，这是推荐的实施方法。
feature: 实施基础
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: Developer, Data Engineer
level: Intermediate
exl-id: 8fe63dd1-9629-437f-ae07-fe1c5a05fa42
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 0%

---

# 在Adobe Analytics中使用跟踪单页应用程序(SPA)的最佳实践 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在本文档中，我们将介绍在使用Adobe Analytics跟踪单页应用程序(SPA)时，您应遵循并注意的一些最佳实践。 本文档将重点介绍如何使用Adobe[!DNL Experience Platform Launch]，这是推荐的实施方法。

初始说明：

* 以下项目假定您使用[!DNL Experience Platform Launch]在网站上实施。 如果您没有使用[!DNL Experience Platform Launch]，但需要根据实施方法调整这些注意事项，则这些注意事项仍会存在。
* 所有SPA都不同，因此您可能需要调整以下一些项目以最好地满足您的需求，但我们希望与您分享一些最佳实践；在SPA页面上实施Adobe Analytics时需要考虑的事项。

## [!DNL Experience Platform Launch]中使用SPA的简单图表 {#simple-diagram-of-working-with-spas-in-launch}

![launch中的analytics spa](assets/spa_for_analyticsinlaunch.png)

**注意：** 如上所述，这是一个简化的图表，用于说明在Adobe Analytics实施中如何使用处理SPA页面 [!DNL Experience Platform Launch]。在本页的以下部分中，我们将讨论步骤以及您应当仔细考虑或处理的任何问题。

## 设置数据层 {#setting-the-data-layer}

当在SPA页面上加载新内容，或在SPA页面上执行操作时，您首先应该执行的一项操作是更新数据层。 在自定义事件触发并触发[!DNL Experience Platform Launch]中的规则之前，需要执行此操作，以便[!DNL Experience Platform Launch]可以从数据层提取新值并将其推送到Adobe Analytics。

以下是一个示例数据层，其元素可在视图更改或对SPA执行操作时进行更改。 例如，在全屏/多数屏幕更改时，通常会更改“[!DNL pageName]”元素，以便能够在[!DNL Experience Platform Launch]中捕获新元素并将其发送到Adobe Analytics。

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

## 在[!DNL Experience Platform Launch]中设置自定义事件和侦听 {#setting-custom-events-and-listening-in-launch}

当页面上加载新内容或在网站上执行操作时，您将需要通知[!DNL Experience Platform Launch]，以便它运行规则并将数据发送到[!DNL Analytics]。 可以使用以下几种不同的方法来执行此操作：[!UICONTROL 直接调用] [!UICONTROL 规则]或自定义事件。

* [!UICONTROL 直接] [!UICONTROL 调用规则]:在中， [!DNL Experience Platform Launch]您可以设置一个直接 [!UICONTROL 调]  用规则，该规则在从页面直接调用时执行。如果您的页面加载或您在网站上的操作非常简单，或者它是唯一的，并且可以每次执行一组特定指令（将[!DNL eVar4]设置为X，并每次触发[!DNL event2]），则可以使用[!UICONTROL 直接调用] [!UICONTROL 规则]。 请参阅[!DNL Experience Platform Launch]有关创建[!UICONTROL 直接调用] [!UICONTROL 规则]的文档。
* 自定义事件：要获取更多功能，并且为了能够动态附加具有不同值的有效负载，您应该设置自定义JavaScript事件并在[!DNL Experience Platform Launch]中侦听它们，您可以在其中使用有效负载设置变量并将数据发送到Adobe Analytics。 您更可能需要此功能，因此此选项被视为最佳实践。 但是，您网站上的每个函数都可以确定最合适的方法。 在本文档中，我们将假定您需要使用此自定义事件方法。

**示例：** 在此 [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 帮助文档中，有指向已实施的示例SPA站点(和其 [!DNL Analytics] 他Experience Cloud解决方案)的链接，以及描述已实施内容的文档。在这些SPA示例中，使用了以下自定义事件：

* [!DNL event-view-start]:此事件应在正在加载的视图/状态的视图开始时触发。
* [!DNL event-view-end]:即使发生视图/状态更改，并且页面上的所有SPA组件都已完成加载，也应触发此事件。此事件通常会触发对Adobe Analytics的调用。
* [!DNL event-action-trigger]:当页面上发生除视图/状态加载之外的任何事件时，应触发此事件。这可以是点击事件，也可以是内容在没有视图更改的情况下进行较小更改。

有关如何/何时触发的更多信息，请参阅上述页面/文档。 您不必使用这些相同的事件名称，但建议使用此处列出的功能作为最佳实践。 以下视频将显示一个示例网站以及在[!DNL Experience Platform Launch]中监听自定义事件的位置。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在[!DNL Experience Platform Launch] [!UICONTROL Rule]中运行s.t()或s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

使用SPA时，[!DNL Analytics]最需要了解的一点是`s.t()`和`s.tl()`之间的差异。 您将在[!DNL Experience Platform Launch]中触发以下方法之一，以将数据发送到[!DNL Analytics]，但您需要知道何时发送每个方法。

* **s.t()**  - &quot;t&quot;表示“track”，是正常的页面查看。即使URL可能不会更改，视图是否会发生足够的更改，以致您&#x200B;*考虑将*&#x200B;视为新的“page”？ 如果存在，请设置s.[!DNL pageName]变量，然后使用`s.t()`将调用发送到[!DNL Analytics]

* **s.tl()**  - “tl”表示“跟踪链接”，通常用于跟踪页面上的点击次数或小内容更改，而不是全屏更改。如果页面上的更改很小，为此您不会将其视为全新的“page”，请使用`s.tl()`并且不要担心设置s.pageName变量，因为[!DNL Analytics]将忽略该变量。

**提示：** 有些人遵循一般准则，即如果屏幕更改超过50%，则应将其视为页面查看和使用 `s.t()`。如果屏幕变化小于50%，则使用`s.tl()`。 但是，这完全取决于您以及您认为的新“页面”以及您希望如何跟踪Adobe Analytics中的网站。

以下视频演示了在何处触发`s.t()`或`s.tl()`的Launch by Adobe。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除变量 {#clearing-variables}

使用Adobe Analytics跟踪您的网站时，您当然只希望在正确的时间将正确的数据发送到[!DNL Analytics]。 在SPA环境中， [!DNL Analytics]变量中跟踪的值可以持续存在，并可能会在我们不再希望时被重新发送到[!DNL Analytics]中。 因此，[!DNL Analytics] [!DNL Launch]扩展中有一个用于清除变量的函数，这样在运行下一个图像请求并将数据发送到[!DNL Analytics]时，您就可以重新创建。

在上图中，我们在流程末尾列出了该变量，清除了您在点击中发送&#x200B;*之后的变量*。 实际上，它可以在发送点击之前或之后执行，但应在[!DNL Experience Platform Launch]规则中保持一致，以便始终在设置变量并发送变量之前或之后清除。 请记住，如果要在&#x200B;*运行`s.t()`之前清除变量*，请确保先清除变量，然后设置新变量，最后将新数据发送到[!DNL Analytics]。

**注意：** 运行时并不总是需要清除变量，因 `s.tl()`为每次都需 `s.tl()` 要同时使用变量来告 [!DNL linkTrackVars] 诉要设置的变量(在中的后台自动添加 [!DNL Analytics]  [!DNL Experience Platform Launch])。这意味着使用`s.tl()`时，通常不会输入错误的变量，但在SPA环境中使用`s.t()`时，强烈建议使用此变量。 话虽如此，我建议将此函数作为最佳实践，在SPA环境中同时使用`s.t()`和`s.tl()`的Clear Variables函数，以确保数据收集的质量。

以下视频显示在[!DNL Launch]中清除变量的位置/方法。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他注意事项 {#additional-considerations}

### [!DNL Experience Platform Launch]中的自定义代码窗口 {#custom-code-windows-in-launch}

在[!DNL Launch] [!DNL Analytics]扩展中，可以在以下两个位置插入自定义代码：[!UICONTROL 库管理]部分和额外的“[!UICONTROL 使用自定义代码配置跟踪器]”部分。

![启动Analytics自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

当SPA页面上发生初始页面加载时，务必要知道，其中任一位置实际上只会在其中运行一次代码。 如果您需要在视图更改或网站上的操作中运行代码，则应当向相应的&#x200B;**[!UICONTROL 规则]**&#x200B;添加一个额外的操作(例如，在“页面加载：event-view-end&quot; [!UICONTROL rule])，以便代码在每次运行[!UICONTROL rule]时都执行。 在[!UICONTROL 规则]中创建该操作时，请设置&#x200B;*Extension = Core*&#x200B;和&#x200B;*Action Type = Custom Code*。

### “混合”SPA/常规网站 {#hybrid-spa-regular-sites}

某些网站由“常规”页面和SPA页面组合而成。 在此实例中，您将需要使用适用于这两种页面类型的策略。 在网站上配置自定义事件并触发[!DNL Experience Platform Launch]中的规则时，请务必注意，页面中没有基于哈希更改等的两次点击进入[!DNL Analytics]。 （如果您选择触发[!DNL Experience Platform Launch]规则的方式）。 在这种情况下，您需要禁止其中一次页面查看，以便它不会在Adobe Analytics中提供错误数据。

如果您决定将功能划分为单独的[!UICONTROL rules]，以便您能够更好地控制该功能，请务必记住/记录您已经完成了此操作，以便对一个[!UICONTROL rule]的任何更改也可以对另一个[!UICONTROL rule]进行，从而保护[!DNL Analytics]数据完整性。

### 通过A4T与[!DNL Target]集成 {#integration-with-target-via-a4t}

这里就是一个快速标注。 如果您要使用A4T与[!DNL Target]集成，请确保同一视图上的[!DNL Target]请求和[!DNL Analytics]请求具有相同的SDID。 这将确保您的数据在解决方案上正确同步。

要查看点击量，请使用调试器或数据包探查程序。 您还可以使用Experience Cloud Debugger，该扩展是Chrome扩展，可下载到[HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)。 [!DNL Target] 应该首先在页面上触发，以便您也可以在JavaScript控制台或调试器中检查该事件。

## 其他资源 {#additional-resources}

* [SPA在Adobe论坛上的讨论](https://forums.adobe.com/thread/2451022)
* [引用架构站点以显示如何在Experience Platform Launch中实施SPA](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
