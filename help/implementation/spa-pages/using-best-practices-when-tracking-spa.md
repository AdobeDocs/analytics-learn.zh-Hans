---
title: '在 Adobe Analytics 中跟踪单页面应用程序 (SPA) 时使用最佳实践 '
description: 在本文档中，我们将描述您在使用 Adobe Analytics 跟踪单页面应用程序 (SPA) 时应遵循和注意的几个最佳实践。 本文档将重点介绍如何使用 Experience Platform Launch（这是推荐的实施方法）。
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
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: ht
source-wordcount: '1669'
ht-degree: 100%

---

# 在 Adobe Analytics 中跟踪单页面应用程序 (SPA) 时使用最佳实践 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在本文档中，我们将描述您在使用 Adobe Analytics 跟踪单页面应用程序 (SPA) 时应遵循和注意的几个最佳实践。 本文档将重点介绍如何使用 Adobe [!DNL Experience Platform Launch]（这是推荐的实施方法）。

初始说明：

* 以下项目将假设您使用 [!DNL Experience Platform Launch] 在您的网站上实施。如果您未使用 [!DNL Experience Platform Launch]，则这些注意事项仍然存在，但您需要根据实施方法调整它们。
* 所有 SPA 都是不同的，因此您可能需要调整下面的一些项目以最好地满足您的需求，但我们想与您分享一些最佳实践；在 SPA 页面上实施 Adobe Analytics 时需要考虑的事项。

## 在 [!DNL Experience Platform Launch] 中使用 SPA 的简单图表 {#simple-diagram-of-working-with-spas-in-launch}

![Launch 中的 SPA for Analytics](assets/spa_for_analyticsinlaunch.png)

**注意：**&#x200B;如前所述，这是一个简化的图表，说明了如何在 Adobe Analytics 实施中使用 [!DNL Experience Platform Launch] 处理 SPA 页面。 在本页面的以下部分中，我们将讨论您应仔细考虑或采取行动的步骤和任何问题。

## 设置数据层 {#setting-the-data-layer}

在 SPA 页面上加载新内容或在 SPA 页面上执行操作时，您首先要执行的操作之一是更新数据层。 此操作需要在自定义事件触发 [!DNL Experience Platform Launch] 中的规则之前执行，以便 [!DNL Experience Platform Launch] 能够从数据层中获取新值并将它们推送到 Adobe Analytics 中。

下面是一个示例数据层，其元素可以根据您的 SPA 上的视图更改或操作进行更改。 例如，在进行所有/大多数屏幕更改时，通常会更改“[!DNL pageName]”元素，以便在 [!DNL Experience Platform Launch] 中捕获新元素并将其发送到 Adobe Analytics 中。

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

## 在 [!DNL Experience Platform Launch] 中设置自定义事件和监听 {#setting-custom-events-and-listening-in-launch}

在页面上加载新内容或在网站上执行操作时，您将需要通知 [!DNL Experience Platform Launch]，以便它能运行规则并将数据发送到 [!DNL Analytics]。 可通过几种不同的方法做到这一点：[!UICONTROL 直接调用][!UICONTROL 规则]或自定义事件。

* [!UICONTROL 直接调用][!UICONTROL 规则]：在 [!DNL Experience Platform Launch] 中，您可以设置[!UICONTROL 直接调用][!UICONTROL 规则]，此规则将在直接从页面调用时执行。 如果网站上的页面加载或操作非常简单，或如果它是唯一的并且每次都会执行一组特定的指令（每次将 [!DNL eVar4] 设置为 X 并触发 [!DNL event2]），则可以使用[!UICONTROL 直接调用][!UICONTROL 规则]。 请参阅有关创建[!UICONTROL 直接调用][!UICONTROL 规则]的 [!DNL Experience Platform Launch] 文档。
* 自定义事件：要获得更多功能以及动态附加具有不同值的负载的能力，您应设置自定义 JavaScript 事件并在 [!DNL Experience Platform Launch]（您可以在其中使用负载设置变量并将数据发送到 Adobe Analytics 中）中监听这些事件。 您更有可能需要此功能，因此该选项被视为最佳实践。 但您网站上的每项功能均能确定哪种方法最合适。 假设您将需要使用此自定义事件方法，我们将继续浏览本文档。

**示例：**[本](https://helpx.adobe.com/cn/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)帮助文档包含已实施 [!DNL Analytics]（以及其他 Experience Cloud 解决方案）的示例 SPA 网站以及描述已实施项目的文档的链接。 在这些 SPA 示例中，使用了以下自定义事件：

* [!DNL event-view-start]：此事件将在正在加载的视图/状态的视图开始时触发。
* [!DNL event-view-end]：即使视图/状态发生更改并且页面上的所有 SPA 组件都已完成加载，也将触发此事件。 这是通常触发对 Adobe Analytics 的调用的事件。
* [!DNL event-action-trigger]：此事件将在页面上发生除视图/状态加载之外的任何事件时触发。 这可能是点击事件或较小内容更改而没有视图更改。

有关如何/何时触发这些事件的更多信息，请参阅上面引用的页面/文档。 您不必使用这些相同的事件名称，此处列出的功能是推荐的最佳实践。 以下视频介绍了示例网站以及 [!DNL Experience Platform Launch] 中用于监听自定义事件的位置。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在 [!DNL Experience Platform Launch] [!UICONTROL 规则]中运行 s.t() 或 s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

在使用 SPA 时应了解的 [!DNL Analytics] 的最重要事项之一是 `s.t()` 和 `s.tl()` 之间的差异。 您将触发 [!DNL Experience Platform Launch] 中的这些方法之一来将数据发送到 [!DNL Analytics] 中，但您需要知道何时发送每个数据。

* **s.t()** —“t”表示“跟踪”，即一般页面查看。 即使 URL 可能不会发生改变，视图变更是否足以让您将它&#x200B;*视为*&#x200B;一个新的“页面”？ 如果是这样的话，请设置 s.[!DNL pageName] 变量并使用 `s.t()` 将调用发送到 [!DNL Analytics] 中

* **s.tl()** —“tl”表示“跟踪链接”，通常用于跟踪页面上的点击或少量内容变更，而不是全屏变更。 如果页面更改较少，以使您不会将它视为一个全新“页面”，可使用 `s.tl()` 且无需设置 s.pageName 变量，因为 [!DNL Analytics] 将忽略它。

**提示：**&#x200B;一些人员使用以下一般准则：如果屏幕变更超过 50%，则应将它视为页面查看并使用 `s.t()`。 如果屏幕变更不到 50%，则使用 `s.tl()`。 但是，这完全取决于您以及您视为新“页面”的内容以及您希望如何在 Adobe Analytics 中跟踪您的网站。

以下视频说明在何处以及如何在 Adobe Launch 中触发 `s.t()` 或 `s.tl()`。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除变量 {#clearing-variables}

在使用 Adobe Analytics 跟踪网站时，您只需在正确的时间将相应数据发送到 [!DNL Analytics] 中。 在 SPA 环境中，[!DNL Analytics] 变量中跟踪的值可以持续存在，并且可能在我们不再需要时重新发送到 [!DNL Analytics] 中。 出于这个原因，[!DNL Analytics] [!DNL Launch] 扩展包含了一个用于清除变量的函数，这样当您运行下一个图像请求并将数据发送到 [!DNL Analytics] 中时，就有了一个全新的状态。

在上面的图表中，我们在流程结束时列出了它，并在您在点击中发送&#x200B;*后*&#x200B;清除变量。 实际上，它可以在发送点击之前或之后完成，但应在您的 [!DNL Experience Platform Launch] 规则中保持一致，以便您始终在设置并发送变量之前或之后清除。 请记住，如果您将在运行 `s.t()` *之前*&#x200B;清除变量，请确保先清除变量，然后设置新变量，最后再将新数据发送到 [!DNL Analytics] 中。

**注意：**&#x200B;运行 `s.tl()` 时并不总是需要清除变量，因为 `s.tl()` 要求每次都使用 [!DNL linkTrackVars] 变量以告知 [!DNL Analytics] 将设置哪些变量（自动在 [!DNL Experience Platform Launch] 中的场景后添加）。 这意味着，在使用 `s.tl()` 时通常不会出现错误的变量，但在 SPA 环境中使用 `s.t()` 时强烈建议这样做。 正如一开始所讲的，我想推荐它作为最佳实践，在 SPA 环境中对 `s.t()` 和 `s.tl()` 使用“清除变量”函数以确保收集高质量数据。

以下视频说明在何处以及如何在 [!DNL Launch] 中清除变量。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他注意事项 {#additional-considerations}

### [!DNL Experience Platform Launch] 中的自定义代码窗口 {#custom-code-windows-in-launch}

在 [!DNL Launch] [!DNL Analytics] 扩展中，可以在以下两个位置插入自定义代码：[!UICONTROL 库管理]部分和额外的“[!UICONTROL 使用自定义代码配置跟踪程序]”部分。

![Launch Analytics 自定义代码窗口](assets/launch_analyticscustomcodewindows.png)

务必知道的一点是，在 SPA 页面上进行初始页面加载时，这些位置中的任一位置实际上只会在其中运行一次代码。 如果您需要对视图变更或网站上的操作运行代码，则应将其他操作添加到适当的&#x200B;**[!UICONTROL 规则]**（例如，在“page load: event-view-end”[!UICONTROL 规则]中），以使代码在[!UICONTROL 规则]运行时执行。 在[!UICONTROL 规则]中创建该操作时，请将&#x200B;*扩展设置为核心*，并将&#x200B;*操作类型设置为自定义代码*。

### “混合”SPA/常规网站 {#hybrid-spa-regular-sites}

一些网站是“常规”页面和 SPA 页面的组合。 在此情况下，您将需要使用适用于两种页面类型的策略。 在网站上配置自定义事件并触发 [!DNL Experience Platform Launch] 中的规则时，请注意，根据哈希更改等，页面上不会有两次点击进入 [!DNL Analytics]。（如果这是您选择用于触发 [!DNL Experience Platform Launch] 规则的方式）。 在这种情况下，您将需要禁止其中一个页面查看，这样它就不会在 Adobe Analytics 中为您提供错误数据。

如果您决定将功能分解为单独的[!UICONTROL 规则]，以便您能够更好地控制它，请务必记住/记录您已完成此操作，以便对一条[!UICONTROL 规则]的所做的任何更改同样适用于另一条[!UICONTROL 规则]，并保护 [!DNL Analytics] 数据完整性。

### 通过 A4T 与 [!DNL Target] 集成 {#integration-with-target-via-a4t}

这里只是一个简单的标注。 如果使用 A4T 与 [!DNL Target] 集成，请确保对同一视图变更的 [!DNL Target] 请求和 [!DNL Analytics] 请求具有相同的 SDID。 这将确保您的数据在解决方案上正确地同步。

要查看点击数，请使用调试程序或数据包嗅探器程序。 您也可以使用 Experience Cloud Debugger，它是一个 Chrome 扩展，可从[此处](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)下载。 页面上第一个触发的是 [!DNL Target]，因此您也可以在 JavaScript 控制台或调试程序中检查它。

## 其他资源 {#additional-resources}

* [Adobe 论坛上的 SPA 讨论](https://forums.adobe.com/thread/2451022)
* [参考架构站点，该站点说明如何在 Experience Platform Launch 中实施 SPA](https://helpx.adobe.com/cn/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
