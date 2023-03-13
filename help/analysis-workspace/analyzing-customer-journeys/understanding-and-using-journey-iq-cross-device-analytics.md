---
title: 了解和使用 Journey IQ — 跨设备分析
description: 当用户与您的品牌互动时，他们可在多种设备上通过多种方式进行。 跨设备分析与 Adobe Experience Platform Identity Service 集成以标识设备与人员的映射方式。 然后，它利用此智能来创建用户行为的跨设备视图。 这使得能够对人员而非设备执行分析。
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: User
level: Intermediate
exl-id: 3748d5d7-d250-4057-8131-afdc66c80200
source-git-commit: 01e6e84f748e359aeb42c9be3afa52088f41018b
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 100%

---

# 了解和使用 [!DNL Journey IQ] — 跨设备分析

当用户与您的品牌互动时，他们可在多种设备上通过多种方式进行。 跨设备分析与 [!DNL Adobe Experience Platform Identity Service] 集成以标识设备与人员的映射方式。 然后，它利用此智能来创建用户行为的跨设备视图。 这使得能够对人员而非设备执行分析。

## 跨设备分析概述

### 我没有使用自己的设备

当用户与您的品牌互动时，他们可在多种“表面”或“设备”上通过多种方式进行。 他们可能会使用 PC 或移动设备上的 Web 浏览器，也可能会使用移动应用程序。 在基于 Cookie 的数据收集中扩展的传统数字分析中，这些表面中的每个表面均表示为一个独特“访客”。 这意味着您的每个人类用户均表示为多个独特访客。

以下是一个示例。 假设 Isabelle 通过以下方式与您的品牌互动：

*Isabelle 是三个访客*
![传统分析历程](assets/cda-isabelle-journey-traditional-analytics.png)

通过使用传统分析，Isabelle 的历程分为三个部分。 她表示为三个独特访客，每个人员均使用不同的设备来执行独立任务。 我们需要的是一个统一的、跨设备的 Isabelle 互动视图。 [!DNL Journey IQ: Cross-Device Analytics] 提供了此视图。

*Isabelle 是一个人员*
![跨设备分析历程](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨设备视图提高了分析质量

Isabelle 行为的以人员为中心的跨设备视图会给您的分析带来显著差异。 例如，传统的基于访客的方法不能让您全面了解营销渠道的有效性。 让我们再次看看 Isabelle 的历程，重点关注哪个渠道因她的产品查看和购买而获得点数。 为简单起见，我们将使用[!UICONTROL 最近联系]归因，但是当您将 Isabelle 的行为划分为单独访客时，使用任何归因模型都会出现同样的问题。 使用传统的基于访客的世界观会产生极为不同甚至是误导性的结果：

*传统分析与跨设备分析*
![渠道归因](assets/channel-attribution.png)

请注意，使用跨设备视图时，电子邮件渠道会获得产品视图和购买的点数，这更准确地表示了 Isabelle 的真实体验。

请继续阅读以了解：

* [!DNL Cross-Device Analytics]的工作原理
* [!DNL Cross-Device Analytics]的前提条件
* 解释跨设备数据
* 分析 Analysis Workspace 中的跨设备数据

## [!DNL Cross-Device Analytics]的工作原理

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 与 [!DNL Adobe Experience Platform Identity Service] 集成，以利用 [!DNL Device Graph] 标识设备与人员的映射方式。 然后，它利用此智能来创建用户行为的跨设备视图。 CDA 包含无与伦比的功能和工具，可帮助您的企业了解多设备使用情况以及这些设备与您的品牌互动时的客户体验。 它是 Analysis Workspace 下方的一个层，借助功能强大的工具（例如[!UICONTROL 流失]、[!DNL Flow]、[!DNL Cohort]、[!DNL Segment IQ] 和 [!DNL Attribution IQ]）来提供对基于人员的受众分析和跨设备归因、分段和历程分析的深入洞察。

### [!DNL Cross-Device Virtual Report Suite]

CDA 通过特殊类型的跨设备[[!UICONTROL 虚拟报表包]](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html)来呈现。 这允许您在将跨设备分析引入组织时继续使用基于设备的原始报表包。 设置 CDA VRS 是一项轻松的工作。

在 VRS 生成器的第一步中，选择已由 Adobe 配置为支持 CDA 的[!UICONTROL 报表包]：

*选择支持 CDA 的基本（源）[!UICONTROL 报表包]*
![[!UICONTROL 虚拟报表包]第一步](assets/cda-vrs-step-one.png)

然后，开启[!UICONTROL 报表时间处理]并启用[!UICONTROL 跨设备拼接]：

*启用[!UICONTROL 报表时间处理]和[!UICONTROL 跨设备拼接]*
![[!UICONTROL 虚拟报表包]第二步](assets/cda-vrs-step-two.png)

完成并保存 VRS 设置。 CDA VRS 将显示在 Analysis Workspace 中，它旁边有一个特殊图标，如下所示：

*选择 Analysis Workspace 中的 CDA VRS*
![[!UICONTROL 虚拟报表包]第三步](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以根据支持 CDA 的基本[!UICONTROL 报表包]创建所需数量的 CDA [!UICONTROL 虚拟报表包]。

### 重述历史记录

有时，您的用户需要一段时间才能登录，然后才能通过 [!DNL Device Graph] 来识别他们并将他们的设备映射到一起。 CDA 使用 30 天的回顾时段，以便能够将之前未识别的访客重述为过去 30 天内的人员。

这有什么用呢？ 回想一下上面讨论中的 Isabelle 的用户历程：

![[!DNL Cross-Device Analytics]历程](assets/cda-isabelle-journey-cross-device-analytics.png)

有可能是 Isabelle 在购买之前没有登录，并且 [!DNL Device Graph] 直到 Isabelle 购买后的某个时间才将其设备映射到一起。不过，CDA 的 30 天回顾允许 CDA 在人员级别重述 Isabelle 过去的行为，并为您提供所需的 Isabelle 历程的跨设备视图。

>[!NOTE]
>
>由于可以重述历史记录，这意味着，您的数据可能会在支持 CDA 的[!UICONTROL 虚拟报表包]中随着时间的推移而发生变化。 在传达来自基于 CDA 的分析的洞察时，请记住这一点。

## [!UICONTROL 跨设备分析]的先决条件

CDA 包含在 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-analytics.html) 中。 从 2019 年 9 月开始，满足下面列出的先决条件的 [!DNL Analytics Ultimate] 客户有资格使用 CDA。 CDA 的先决条件如下所示：

* 您的公司必须使用 [!DNL Adobe Experience Platform Identity Service Device Graph]。
* 您必须实施 [!DNL Device Graph] 所需的一切，包括 [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/id-service/using/home.html) 以及与图表同步的 ID。
* 目前无法将两个 IMS 组织与单个 [!DNL Device Graph] 结合使用，因此您必须在单个 IMS 组织上进行标准化。
* [!DNL Device Graph] 以及某些 CDA 组件托管于 [!DNL Microsoft Azure] 中。这意味着 [!DNL Analytics] 数据在 Adobe 的数据处理中心和 Adobe 在 [!DNL Microsoft Azure] 中的状态之间来回复制。 一些 [!DNL Analytics] 数据将存储在 [!DNL Azure] 中。 您的公司必须同意此安排。
* CDA 需要“跨设备”[!UICONTROL 报表包]。 也就是说，用于 CDA 的[!UICONTROL 报表包]必须包括来自多种不同的设备类型或“表面”的数据，例如桌面 Web、移动 Web 和移动应用程序。 自 2019 年 9 月起，此[!UICONTROL 报表包]的服务器调用量必须等于或少于 100MM 服务器调用数/天。 （服务器调用量限制将在未来几个月内增加。）

## 解释跨设备数据

### 非访客人员

在 CDA [!UICONTROL 虚拟报表包]中，您将看到几项更改。 例如，[!UICONTROL 独特访客]量度已由两个新的量度替换：[!UICONTROL 人员]和[!UICONTROL 独特设备]。 这两个新量度可让您更好地了解受众规模。

*人员和独特设备*
![CDA [!UICONTROL 人员指标]](assets/cda-people-metric.png)

在[[!UICONTROL 区段生成器]](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html)中，[!UICONTROL 访客]区段容器已由[!UICONTROL 人员]区段容器替换。 通过使用 CDA VRS，您可以创建跨设备区段，例如：

* 使用多台设备的人员
* 先在移动设备上开始其历程，而后又在桌面设备上进行购买的人员
* 访问人员使用多台设备完成一项任务的情况

*人员级别区段*
![[!DNL Segment Builder][!UICONTROL 人员]容器](assets/cda-segment-builder-person-container.png)

### 维度持久性

在 CDA VRS 中，维度（例如 [!DNL eVars]）现在自动跨设备保留。 例如，采用以下配置的 [!DNL eVar]：

* 分配：最近（最后）
* 过期时间：购买

现在将自动从一台设备持续到另一台设备，直到触发购买事件。

## 分析 Analysis Workspace 中的跨设备数据

### 基于人员的受众分析

您有没有想过有多少人员在与您的品牌互动？ 您是否想了解他们使用的设备的数量和类型？ 它们的使用如何重叠？ 通过使用 CDA VRS，您可以创建跨设备[维恩图](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html)和每人员设备[直方图](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/histogram.html)。

*基于人员的受众分析*
![维恩图和直方图](assets/cda-venn-and-histogram.png)

### 跨设备[!DNL Flow]

借助 CDA 和 Analysis Workspace，您可以在[[!DNL Flow visualization]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)中直观说明人员如何随着时间的推移从一台设备移动到另一台设备。 您可以查看他们在历程中何时退出，何时继续。

*[!DNL Flow]，带 CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 跨设备[!DNL Fallout]

您可能使用多个[[!DNL Fallout visualizations]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html)来分析用户在获得成功之前通过一系列给定步骤取得的成效。 您是否知道在使用基于设备的传统分析时，您对[!DNL Fallout visualizations]的查看是有限的？ 为了成功“流过”，必须在执行上一步的同一浏览器或应用程序中执行下一步。 在基于设备的分析中，您看不到在另一台设备上成功完成下一步的人员。

不用担心，CDA 为您提供了解决方法。 CDA 创建了跨设备视图，可让[!DNL Fallout visualizations]变得更有用。 毕竟，真正重要的是人员是否最终在某个地方成功地完成了其任务。

*[!DNL Fallout]，带 CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

由于 CDA 在 Analysis Workspace 下创建了一个跨设备数据层，因此您的所有分析都将使用跨设备透视。 一个强有力的示例是通过 [[!DNL Attribution IQ]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)。 Analysis Workspace 中的 [!DNL Attribution IQ] 允许您并排比较多个归因模型。 通过将此功能与 CDA 结合使用，您现在可以比较不同设备对成功的贡献。

例如，假设您想了解在最终促使成功的交互中，手机作为首个使用设备的频率。 这代表了手机的“客户获取率”。 CDA + [!DNL Attribution IQ] 允许您执行此分析：

*[!DNL Attribution IQ]，带 CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

有关更多信息，请参阅[[!DNL Cross-Device Analytics] 帮助文档](https://experienceleague.adobe.com/docs/analytics/components/cda/cda-home.html)。
