---
title: 单页面应用程序 (SPA) 的实施最佳实践
description: 了解在单页面应用程序 (SPA) 上实施 Adobe Analytics 的一些最佳实践。 这包括使用推荐的实施方法 Experience Platform Tags。
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
source-git-commit: 8fc641743bc9e07b838a22ca64ccc15344d52764
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# 单页面应用程序 (SPA) 的实施最佳实践 {#implementation-best-practices-for-single-page-appliations}

了解在单页面应用程序 (SPA) 上实施 [!DNL Adobe Analytics] 的一些最佳实践。 这包括使用推荐的实施方法 [!DNL Experience Platform Tags]。

初始说明：

* 以下内容参考使用 [!DNL Experience Platform Tags] 在您的网站上实施 Adobe Analytics。 如果不使用 [!DNL Experience Platform Tags]，这些注意事项适用，因此，您必须将其调整为您的实施方法。
* SPA 存在差异，因此，您应该相应调整您的方法，以最好地满足您的需求。

## 在 [!DNL Experience Platform Tags] 中使用 SPA 的简单图表 {#simple-diagram-of-working-with-spas-in-tags}

![Tags 中的分析 SPA](assets/spa_for_analyticsinlaunch.png)

**注意：**&#x200B;这是一个简化的图表，说明了如何在 Adobe Analytics 实施中使用 [!DNL Experience Platform Tags] 处理 SPA 页面。 以下各节确定了需要考虑的步骤和问题。

## 设置数据层 {#set-the-data-layer}

加载新内容或 SPA 页面上发生操作时，*请先更新数据层*。 该操作必须在触发规则的自定义事件在 [!DNL Experience Platform Tags] 中执行&#x200B;**之前**&#x200B;发生。 这可确保将数据层中的正确值推送到 Tags 中，然后推送到 Adobe Analytics 中。

下面是一个示例数据层。 鉴于在您的 SPA 页面上采取的操作，这些元素中的任何一个都可能会根据初始视图或视图的后续更改而更改。 例如，在全部或多数视图更改时，通常要求传入唯一的“[!DNL pageName]”值以区分 Adobe Analytics 报告中的视图值。

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

## 设置自定义事件并在 [!DNL Experience Platform Tags] 中监听这些事件 {#setting-custom-events-and-listening-in-tags}

当加载新内容或 SPA 页面上发生操作时，需要通知 Experience Platform Tags 以运行将数据发送到的规则 [!DNL Analytics]。 可通过几种方法做到这一点：[!UICONTROL 直接调用规则]或自定义事件。

* [!UICONTROL 直接调用规则]：设置[!UICONTROL 直接调用规则]，此规则将在直接从页面调用时执行。 如果页面加载或操作是简单或独特，并且每次都可以执行一组特定的指令（例如，设置[!DNL eVar4] 到 X 且每次都触发 [!DNL event2] ），则此方法适用。有关创建[!UICONTROL 直接调用规则]的更多详细信息，请参阅 [!DNL Experience Platform Tags] 文档。
* 自定义事件：如果需要为 SPA 页面上发生的事件动态附加具有唯一值的有效负载，请使用自定义 JavaScript 事件，并在 [!DNL Experience Platform Tags] 中监听它们。 使用有效负载设置 Tags 中的数据元素和 Analytics 变量。 这种方法被认为是最佳实践，因为这种需求通常适用于 SPA。 下面的示例使用自定义事件方法。

**示例：** [在本](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)帮助文档，有指向实施 [!DNL Analytics] 和其他 Experience Cloud 解决方案的 SPA 示例站点的链接。 在这些示例中，使用了以下自定义事件：

* **[!DNL Event-view-start]**：在加载的视图/状态的视图开始时执行。
* **[!DNL Event-view-end]**：当视图/状态发生更改且页面上的所有 SPA 组件完成加载时执行。 这是通常向 Adobe Analytics 发送数据的事件。
* **[!DNL Event-action-trigger]**：当页面上发生除视图/状态加载以外的任何事件时执行。 例如，单击事件或较小内容更改，而不更改视图。

有关如何以及何时触发这些事件的更多信息，请参阅上面引用的页面和文档。 您不需要在实施中使用相同的事件名称。 所用方法的功能用例对于理解为每种方法的推荐最佳实践至关重要。 以下视频演示了 [!DNL Experience Platform Tags] 中用于监听自定义事件的示例 SPA 页面和示例代码。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12&learn=on)

## 在 [!DNL Experience Platform Tags] 中执行 s.t() 或 s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

在使用 SPA 时应了解的 [!DNL Analytics] 的重要概念是 `s.t()` 和 `s.tl()` 之间的差异。 您的代码触发 [!DNL Experience Platform Tags] 中的一个或另一个方法，将数据发送到 [!DNL Analytics]。

* **s.t()** –“t”表示“跟踪”，即页面查看。 如果视图的变化足以让您&#x200B;*考虑*&#x200B;它是一个新的“页面”，请使用此调用。为 [!DNL s.pageName] 变量设置唯一值，并使用 `s.t()` 将数据发送到 [!DNL Analytics]。

* **s.tl()** –“tl”表示“跟踪链接”，即链接点击或小内容更改。 如果视图更改最小，请使用 `s.tl()` 将关于交互的唯一值传递给 [!DNL Analytics]。传入的变量不是 [!DNL s.pageName]，因为当接收到 `s.tl()` 调用时，Analytics 会忽略此变量。

**提示：**&#x200B;作为一般准则，如果屏幕变化超过 50%，请使用 `s.t()` 页面视图调用。 除此以外，请使用 `s.tl()`。 但是，在考虑构成新“页面”的操作以及如何在 Adobe Analytics 报告中呈现时，请根据您的判断。

以下视频说明在 Tags 中触发 `s.t()` 或 `s.tl()` 的位置和方式。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12&learn=on)

## 清除变量 {#clear-variables}

在正确的时间将正确的数据发送到 [!DNL Analytics]。 在 SPA 环境中，存储在 [!DNL Analytics] 变量中的值会持续存在，并在您不再需要时重新发送到 [!DNL Analytics]。 函数存在于 [!DNL Analytics] [!DNL Tags] 扩展以清除变量，可确保下次调用不会错误地将数据发送到 [!DNL Analytics]。

上图显示了您发送数据&#x200B;*后*&#x200B;清除的变量。 实际上，这可能发生在调用之前或之后，但是，为了实现更干净的实施，[!DNL Experience Platform Tags] 规则是一致的。 如果在执行 `s.t()` *之前*&#x200B;清除变量，则在调用后立即设置新变量，然后继续将新数据发送到 [!DNL Analytics]。

**注意：**&#x200B;运行 `s.tl()` 时并不总是需要清除变量。 此调用需要使用 [!DNL linkTrackVars] 变量来指示 [!DNL Analytics] 要设置哪些变量。 此调用通过配置在 [!DNL Experience Platform Tags] 自动发生。它防止错误变量与 SPA 环境中 `s.t()` 调用的行为形成对比。 为了确保实现最干净和最可靠的实施，在 SPA 环境中为两个调用使用“清除变量”功能可能更容易。

以下视频说明在何处以及如何在 [!DNL Tags] 中清除变量。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12&learn=on)

## 其他注意事项 {#additional-considerations}

### [!DNL Experience Platform Tags] 中的自定义代码窗口 {#custom-code-windows-in-tags}

在 [!DNL Tags] [!DNL Analytics] 扩展中，可以在以下两个位置插入自定义代码：“[!UICONTROL 库管理]”和“[!UICONTROL 使用自定义代码配置跟踪程序]”分区。

![Tags Analytics 自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

这些位置中的任何一个都会运行其中包含的代码一次，以便初始页面加载 SPA 页面。 如果代码应该在视图或操作更改上运行，请在适当的&#x200B;**[!UICONTROL 规则]**（例如，“页面加载：event-view-end”规则）中实施该代码，以确保每次[!UICONTROL 规则]运行时，该代码都会执行。在[!UICONTROL 规则]中创建该操作时，请将&#x200B;*扩展设置为核心*，并将&#x200B;*操作类型设置为自定义代码*。

### “混合”SPA 和传统站点 {#hybrid-spa-and-traditional-sites}

有些网站由传统页面和 SPA 页面组成。 在这种情况下，请使用适用于这两种页面类型的策略。 在站点上配置自定义事件并触发 [!DNL Experience Platform Tags] 中的规则时，请确保根据哈希更改等，页面上不会有两次点击进入 [!DNL Analytics]。 在这种情况下，请抑制其中一个页面视图，以防止重复数据传入 Adobe Analytics。

如果您决定将功能划分为独特的[!UICONTROL 规则]从而获得更多控制权，请记住记录您已完成此操作。 如果你更换[!UICONTROL 规则]，请对另一条[!UICONTROL 规则]进行相同更改。

### 使用 A4T 与 [!DNL Target] 集成 {#integration-with-target-using-a4t}

通过 A4T 与 [!DNL Target] 集成时，请确认 [!DNL Target] 和 [!DNL Analytics] 在同一视图或操作上发送的请求传递相同的 SDID 参数值。 这可以确保数据在后端正确地同步。

要查看这些点击，请使用调试程序或数据包监控的工具。 Adobe 为此提供了 Experience Platform Debugger。 它是一个 Chrome 扩展程序，可以[在此处下载](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en)。[!DNL Target] 应该在首先在页面上执行。 这也可以在调试程序中进行验证。

## 其他资源 {#additional-resources}

* [Adobe 论坛上的 SPA 讨论](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [参考架构站点，该站点说明如何在 Experience Platform Launch 中实施 SPA](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
