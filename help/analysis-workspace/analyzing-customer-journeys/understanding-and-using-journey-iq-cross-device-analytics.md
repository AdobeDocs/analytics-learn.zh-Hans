---
title: 了解和使用历程 IQ — 跨设备分析
description: 当用户与您的品牌互动时，他们会以多种方式在多种设备上进行互动。 跨设备分析与Adobe Experience Platform Identity Service集成，以确定设备如何映射到人。 然后，它利用这一智能创建用户行为的跨设备视图。 这使得能够在人而不是设备上进行分析。
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 6%

---


# 了解和使用[!DNL Journey IQ] — 跨设备分析

当用户与您的品牌互动时，他们会以多种方式在多种设备上进行互动。 跨设备分析与[!DNL Adobe Experience Platform Identity Service]集成，以确定设备如何映射到人。 然后，它利用这一智能创建用户行为的跨设备视图。 这使得能够在人而不是设备上进行分析。

## 跨设备分析概述

### 我不是我的设备

当用户与您的品牌互动时，他们会以多种方式在多个“界面”或“设备”上进行互动。 他们可能在PC或移动设备上使用Web浏览器，也可能使用移动应用程序。 在传统的数字分析中，每个表面都被表示为独特的“访客”。 这意味着您的每个用户都被表示为多个唯一访客。

这里有个例子。 假设Isabelle通过以下方式与您的品牌互动：

*Isabelle有三个访*
![客传统分析历程](assets/cda-isabelle-journey-traditional-analytics.png)

伊莎贝尔的旅程通过传统分析分为三部分。 她以三个独特的访客来表示，每个任务都使用不同的设备执行隔离的操作。 我们需要的是对伊莎贝尔互动的统一、跨设备视图。 [!DNL Journey IQ: Cross-Device Analytics] 提供此视图。

*Isabelle是Cross*
![Device Analytics历程](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨设备视图提供更好的分析

以人为中心、跨设备视图Isabelle的行为可以显着改变分析。 例如，传统的基于访客的方法无法全面了解营销渠道的有效性。 让我们再次看看伊莎贝尔的旅程，重点是哪位渠道因其产品视图和购买而获得了信用。 我们将使用[!UICONTROL last-touch]归因来实现简单性，但当您将Isabelle的行为分为不同的访客时，使用任何归因模型都会出现同样的问题。 使用传统的基于访客的世界视图会产生非常不同甚至误导的结果：

*传统分析与跨设备分析渠道*
![归因](assets/channel-attribution.png)

请注意，通过跨设备视图，电子邮件渠道将收到产品视图和购买的信用，这更准确地反映了Isabelle的真实体验。

继续阅读，了解：

* [!DNL Cross-Device Analytics]的工作方式
* [!DNL Cross-Device Analytics]的先决条件
* 解释跨设备数据
* 在Analysis Workspace中分析跨设备数据

## [!DNL Cross-Device Analytics]的工作方式

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 与集成， [!DNL Adobe Experience Platform Identity Service]利用或 [[!DNL Co-op Graph]](https://docs.adobe.com/content/help/zh-Hans/device-co-op/using/home.html) 识 [!DNL Private Graph] 别设备如何映射到人。然后，它利用这一智能创建用户行为的跨设备视图。 CDA包含无与伦比的功能和工具，可帮助您的企业了解多设备使用情况以及跨这些设备与品牌互动的客户体验。 它位于Analysis Workspace下方的一个层，可以使用诸如[!UICONTROL Flous]、[!DNL Flow]、[!DNL Cohort]、[!DNL Segment IQ]和[!DNL Attribution IQ]等强大工具，深入洞察基于人的受众分析和跨设备归因、细分和旅程分析。

### [!DNL Cross-Device Virtual Report Suite]

CDA通过一种特殊的跨设备[[!UICONTROL 虚拟报表包]](https://docs.adobe.com/content/help/zh-Hans/analytics/components/virtual-report-suites/vrs-about.html)来呈现。 这样，在组织中引入跨设备分析时，您可以继续使用原始的基于设备的报表包。 设置CDA VRS很简单。

在VRS生成器的步骤之一中，选择已由Adobe配置为启用CDA的[!UICONTROL 报表包]:

*选择启用CDA的基本（源）报表包虚 [!UICONTROL 拟报]*
![[!UICONTROL 表包] 步骤1](assets/cda-vrs-step-one.png)

然后打开[!UICONTROL 报表时间处理]并启用[!UICONTROL 跨设备拼接]:

*启用 [!UICONTROL 报表时处] 理和 [!UICONTROL 跨设备拼接虚]*
![[!UICONTROL 拟报表包] 步骤二](assets/cda-vrs-step-two.png)

完成VRS设置并保存。 CDA VRS将在Analysis Workspace中显示，其旁边有一个特殊图标，如下所示：

*在分析 Workspace中选择CDA VRS虚拟*
![[!UICONTROL 报表包] 步骤三](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以在启用CDA的基础[!UICONTROL 报表包]上创建任意数量的CDA [!UICONTROL 虚拟报表包]。

### 恢复历史

有时，用户需要一段时间才能登录，[!DNL Co-op Graph]或[!DNL Private Graph]才能识别他们并将他们的设备映射到一起。 CDA利用30天的回顾窗口，允许其将先前未识别的访客重新声明为过去最多30天的人。

这有什么帮助？ 回想一下Isabelle从上述讨论中的用户旅程：

![[!DNL Cross-Device Analytics] 历程](assets/cda-isabelle-journey-cross-device-analytics.png)

Isabelle可能直到购买前才登录，[!DNL Co-op Graph]或[!DNL Private Graph]在购买后的某个时间才将Isabelle的设备映射到一起。 但CDA的30天回顾使CDA能够从个人层面重新陈述伊莎贝尔过去的行为，为您提供她旅程的跨设备视图，这是您需要的。

>[!NOTE]
>
>由于历史记录可以重述，这意味着您的数据可能会随着时间的推移在启用CDA的[!UICONTROL 虚拟报表包]中发生更改。 当您通过基于CDA的分析交流洞察时，请牢记这一点。

## [!UICONTROL 跨设备分析]的先决条件

CDA随[[!DNL Analytics Ultimate]](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)提供。 从2019年9月开始，[!DNL Analytics Ultimate]符合以下所列先决条件的客户有资格使用CDA。 CDA的先决条件如下：

* 您的公司必须是[!DNL Adobe Experience Platform Identity Service] [[!DNL Co-op Graph]](https://docs.adobe.com/content/help/en/device-co-op/using/home.html)的成员，或使用[!DNL Adobe Experience Platform Identity Service Private Graph]。
* 您必须实现[!DNL Co-op Graph]或[!DNL Private Graph]所需的一切，包括[Experience CloudID(ECID)](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html)和与图形同步的ID。 请注意，除技术要求外，[!DNL Co-op Graph]还有其他法律和合同要求。
* 目前无法将两个IMS组织与单个[!DNL Private Graph]一起使用，因此您必须在单个IMS组织上实现标准化。 在某些情况下，具有多个IMS组织的客户可以将[!DNL Co-op Graph]与CDA结合使用。
* [!DNL Co-op graph]和[!DNL Private Graph]以及CDA的某些组件都托管在[!DNL Microsoft Azure]中。 这意味着[!DNL Analytics]Adobe在Adobe的数据处理中心和数据在[!DNL Microsoft Azure]中的存在之间来回复制。 某些[!DNL Analytics]数据将存储在[!DNL Azure]中。 您的公司必须同意此安排。
* CDA需要“跨设备”[!UICONTROL 报表包]。 即，用于CDA的[!UICONTROL 报表包]必须包含来自多种不同设备类型或“界面”（如桌面Web、移动Web和移动应用程序）的数据。 自2019年9月起，此[!UICONTROL 报表包]的服务器调用卷必须为100MM/天或更少。 （服务器调用量限制将在未来几个月内增加。）
* 自2019年9月起，[!DNL Co-op Graph]和[!DNL Private Graph]仅在北美提供。 未来将宣布在EMEA和APAC建立图形存在计划。 如果您位于这些区域，我们建议您立即开始查看这些先决条件，以便您在图形可用时可以开始使用。

## 解释跨设备数据

### 人非访客

在CDA [!UICONTROL 虚拟报表包]中，您将看到一些更改。 例如，[!UICONTROL 唯一访客]量度由两个新量度替换：[!UICONTROL 人员]和[!UICONTROL 唯一设备]。 这些新量度可让您更好地了解受众大小。

*人员和独特设*
![备CDA人 [!UICONTROL 员量度]](assets/cda-people-metric.png)

在[[!UICONTROL 区段生成器]](https://docs.adobe.com/content/help/zh-Hans/analytics/components/segmentation/segmentation-workflow/seg-build.html)中，[!UICONTROL 访客]区段容器已被[!UICONTROL 人员]区段容器替换。 使用CDA VRS，您可以创建跨设备区段，例如：

* 使用多个设备的用户
* 在移动设备上开始旅程，然后在桌面设备上购买的人
* 访问用户使用多台设备完成任务

*人员级别的*
![[!DNL Segment Builder]  segmentsPersonContainer](assets/cda-segment-builder-person-container.png)

### Dimension持久性

在CDA VRS中，[!DNL eVars]等尺寸现在会自动跨设备保留。 例如，[!DNL eVar]配置为：

* 分配：最近（最后）
* 在以下情况下过期：购买

现在，将自动在一台设备之间保留，直到触发购买事件。

## 在Analysis Workspace中分析跨设备数据

### 基于人的受众分析

您是否曾想过有多少人在与您的品牌互动？ 您是否想了解他们使用了多少种设备以及何种设备？ 它们的使用如何重叠？ 使用CDA VRS，可以创建跨设备[维恩图](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/venn.html)和每人设备[直方图](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/histogram.html)。

*基于人的受众分*
![析维恩和直方图](assets/cda-venn-and-histogram.png)

### 跨设备[!DNL Flow]

通过CDA和Analysis Workspace，您可以在[[!DNL Flow visualization]](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)中显示人们在一段时间内从一个设备移动到另一个设备的方式。 你可以看到他们在旅程中的下落，以及他们的继续。

*[!DNL Flow]与CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 跨设备[!DNL Fallout]

您可能使用多个[[!DNL Fallout visualizations]](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html)来分析用户在成功前通过一系列步骤取得的成效。 您是否知道使用传统的基于设备的分析时，您对这些[!DNL Fallout visualizations]的视图有限？ 要成功“落后”，下一步必须与上一步在同一个浏览器或应用程序中执行。 在基于设备的分析中，您会忽视在其他设备上成功完成下一步的人员。

别担心，CDA已经帮了你。 CDA创建跨设备视图，使[!DNL Fallout visualizations]更有用。 毕竟，真正重要的是这个人最终是否在某处成功了任务。

*[!DNL Fallout]与CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

由于CDA在Analysis Workspace下面创建了一层跨设备数据，因此您的所有分析都将采用跨设备视角进行调味。 一个强大的示例是通过[[!DNL Attribution IQ]](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)。 [!DNL Attribution IQ] 在Analysis Workspace中，您可以并排比较多个归因模型。将此功能与CDA结合使用，您现在可以比较不同设备对成功的贡献。

例如，假设您想要了解手机是交互中第一个最终导致成功的设备的频率。 这代表移动电话的“获取率”。 CDA + [!DNL Attribution IQ]允许您执行以下分析:

*[!DNL Attribution IQ]与CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

有关详细信息，请参阅[[!DNL Cross-Device Analytics] 帮助文档](https://docs.adobe.com/content/help/zh-Hans/analytics/components/cda/cda-home.html)。
