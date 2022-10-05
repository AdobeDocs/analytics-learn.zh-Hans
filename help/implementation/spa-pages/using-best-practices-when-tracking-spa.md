---
title: 单页应用程序(SPA)的实施最佳实践
description: 了解在单页应用程序(SPA)上实施Adobe Analytics的一些最佳实践。 这包括使用Experience Platform标记，推荐实施方法。
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: Developer, Data Engineer
level: Intermediate
exl-id: 8fe63dd1-9629-437f-ae07-fe1c5a05fa42
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 2%

---

# 单页应用程序(SPA)的实施最佳实践 {#implementation-best-practices-for-single-page-appliations}

了解实施的一些最佳实践 [!DNL Adobe Analytics] (SPA)。 这包括使用 [!DNL Experience Platform Tags]，推荐的实施方法。

初始说明：

* 以下内容引用了 [!DNL Experience Platform Tags] 在您的网站上实施Adobe Analytics。 如果 [!DNL Experience Platform Tags] 因此，您必须将其调整为实施方法。
* SPA中存在差异，因此您应该相应地调整方法以最好地满足您的需求。

## 在 [!DNL Experience Platform Tags] 中使用 SPA 的简单图表 {#simple-diagram-of-working-with-spas-in-tags}

![SPA for analytics用于标记](assets/spa_for_analyticsinlaunch.png)

**注意：** 这是一个简化的图表，用于说明在Adobe Analytics实施中如何使用 [!DNL Experience Platform Tags]. 以下各节确定了要考虑的步骤和问题。

## 设置数据层 {#set-the-data-layer}

加载新内容或在SPA页面上执行操作时， *首先更新数据层*. 这必须发生 **之前** 触发规则的自定义事件在 [!DNL Experience Platform Tags]. 这可确保将数据层中的正确值依次推送到标记和Adobe Analytics。

下面是一个示例数据层。 任何这些元素都可能会根据初始视图进行更改，或者在SPA页面上执行相应操作后对视图进行后续更改。 例如，对于完全视图或大部分视图更改，通常要求在“”中传递[!DNL pageName]值以区分Adobe Analytics报表中的各种视图。

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

## 设置自定义事件，并在 [!DNL Experience Platform Tags] {#setting-custom-events-and-listening-in-tags}

当新内容加载或SPA页面上发生操作时，需要通知Experience Platform标记才能运行将数据发送到的规则 [!DNL Analytics]. 这有几种方法： [!UICONTROL 直接调用规则] 或自定义事件。

* [!UICONTROL 直接调用规则]:设置 [!UICONTROL 直接调用规则] 直接从页面调用时会执行该操作。 如果页面加载或操作简单或唯一，并且每次都可以执行一组特定的指令(例如，设置 [!DNL eVar4] X和触发器 [!DNL event2] )，则此方法是合适的。 请参阅 [!DNL Experience Platform Tags] 有关创建的更多详细信息的文档 [!UICONTROL 直接调用规则].
* 自定义事件：如果您需要为SPA页面上发生的事件动态附加具有唯一值的有效负载，请使用自定义JavaScript事件，并在 [!DNL Experience Platform Tags]. 使用有效负载在标记中设置数据元素和Analytics变量。 此方法被视为最佳实践，因为SPA通常普遍存在这种需求。 以下示例使用自定义事件方法。

**示例：** [在此](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html) 帮助文档中，有指向实施 [!DNL Analytics] 和其他Experience Cloud解决方案。 在这些示例中，使用了以下自定义事件：

* **[!DNL Event-view-start]**:在加载的视图/状态的视图开始时执行。
* **[!DNL Event-view-end]**:当视图/状态发生更改且页面上的所有SPA组件都完成加载时执行。 这是一个事件，通常会将数据发送到Adobe Analytics。
* **[!DNL Event-action-trigger]**:在页面上发生除视图/状态加载之外的任何事件时执行。 例如，点击事件或较小的内容更改，而不进行视图更改。

有关这些事件如何以及何时触发的更多信息，请参阅上面引用的页面和文档。 您无需在实施中使用相同的事件名称。 要了解所用方法的功能用例是每个方法的推荐最佳实践，这一点至关重要。 以下视频演示了中的SPA页面和示例代码 [!DNL Experience Platform Tags] 用于侦听自定义事件。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在 [!DNL Experience Platform Tags] {#running-s-t-or-s-tl-in-the-launch-rule}

一个重要的概念 [!DNL Analytics] 使用SPA时， `s.t()` 和 `s.tl()`. 您的代码会在 [!DNL Experience Platform Tags] 将数据发送到 [!DNL Analytics].

* **s.t()** - &quot;t&quot;表示“track”，它表示页面查看。 如果视图发生足够的更改，  *考虑* 它是新的“页面”，请使用此调用。 将唯一值设置为 [!DNL s.pageName] 变量和使用 `s.t()` 将数据发送到 [!DNL Analytics].

* **s.tl()** - &quot;tl&quot;表示“跟踪链接”，它表示链接点击或小内容更改。 如果视图更改极小，请使用 `s.tl()` 传递有关交互的唯一值到 [!DNL Analytics]. 传入的此变量不是 [!DNL s.pageName]，因为当 `s.tl()` 接收调用。

**提示：** 作为一般准则，如果屏幕的更改超过50%，请使用 `s.t()` 页面查看调用。 否则，请使用 `s.tl()`. 但是，在考虑构成新&quot;页面&quot;的行动以及如何在Adobe Analytics报告中提出时，请作出判断。

以下视频演示了触发位置和方式 `s.t()` 或 `s.tl()` 标记中。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除变量 {#clear-variables}

将正确的数据发送到 [!DNL Analytics] 在正确的时间。 在SPA环境中，存储在 [!DNL Analytics] 变量会持续存在并重新发送到 [!DNL Analytics]，可能是在您不再需要它时。 函数存在于 [!DNL Analytics] [!DNL Tags] 扩展来清除变量，以确保下次调用不会将数据快速发送到 [!DNL Analytics].

上图显示了已清除的变量 *after* 您发送数据。 实际上，这可能发生在调用OR之前，但请在中保持一致 [!DNL Experience Platform Tags] 更简洁的实施规则。 如果清除变量 *之前* 执行 `s.t()`，请在调用后立即设置新变量，然后继续将新数据发送到 [!DNL Analytics].

**注意：** 运行时并非始终需要清除变量 `s.tl()`. 此调用需要使用 [!DNL linkTrackVars] 变量 [!DNL Analytics] 要设置的变量。 这是自动发生的 [!DNL Experience Platform Tags] 通过配置。 它可防止错误的变量与 `s.t()` 调用。 为确保实施最清晰、最可靠，在SPA环境中对这两个调用使用clear variables函数可能会更容易。

以下视频演示了在何处以及如何清除 [!DNL Tags].

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他注意事项 {#additional-considerations}

### 中的“自定义代码”窗口 [!DNL Experience Platform Tags] {#custom-code-windows-in-tags}

在 [!DNL Tags] [!DNL Analytics] 扩展中，可以在两个位置插入自定义代码：“[!UICONTROL 库管理]&quot;和&quot;[!UICONTROL 使用自定义代码配置跟踪器]“ ”部分。

![标记Analytics自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

其中任一位置都会运行其中包含的代码一次，以便初始页面加载您的SPA页面。 如果代码应在视图或操作发生更改时运行，请在相应的 **[!UICONTROL 规则]** (例如，“页面加载：event-view-end”规则)，以确保代码每次执行时都会执行 [!UICONTROL 规则] 运行。 在中创建操作时 [!UICONTROL 规则]，设置 *扩展=核心* 和 *操作类型=自定义代码*.

### “混合”SPA和传统网站 {#hybrid-spa-and-traditional-sites}

某些网站由传统页面和SPA页面组合而成。 在本例中，请使用适用于这两种页面类型的策略。 在网站上配置自定义事件并在 [!DNL Experience Platform Tags]，请确保不会将两次点击发送到 [!DNL Analytics] 基于哈希更改等。 在这种情况下，应禁止其中一个页面查看，以防止将重复数据传递到Adobe Analytics。

如果您决定将功能分隔为唯一 [!UICONTROL 规则] 要获得更多控制权，请记住记录您已完成此操作。 如果你换一个 [!UICONTROL 规则]，则对另一个进行相同的更改 [!UICONTROL 规则].

### 与集成 [!DNL Target] 使用A4T {#integration-with-target-using-a4t}

与集成时 [!DNL Target] 使用A4T，确认 [!DNL Target] 和 [!DNL Analytics] 在同一视图或操作中发送的请求会传递相同的SDID参数值。 这可确保您的数据在后端正确同步。

要查看这些点击量，请使用调试器或数据包监控工具。 Adobe为此提供了Experience Platform调试器。 这是一个Chrome扩展，可以 [下载此处](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en). [!DNL Target] 应该先在页面上执行。 这也可以在调试器中进行验证。

## 其他资源 {#additional-resources}

* [Adobe 论坛上的 SPA 讨论](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [参考架构站点，该站点说明如何在 Experience Platform Launch 中实施 SPA](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
