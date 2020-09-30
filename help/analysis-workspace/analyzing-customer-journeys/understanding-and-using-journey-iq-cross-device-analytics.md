---
title: 了解和使用旅程IQ —— 跨设备分析
description: 当用户与您的品牌互动时，他们会通过多种方式和多种设备进行互动。 跨设备分析与Adobe Experience Platform身份服务集成，以确定设备如何映射到人。 然后，它利用这种智能创建用户行为的跨设备视图。 这使得能够在人而不是设备上进行分析。
feature: cda
topics: null
audience: all
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
translation-type: tm+mt
source-git-commit: 24ad92b0ccdf1112e3ed4a0968cd47db757598c3
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 6%

---


# 理解和使 [!DNL Journey IQ] 用——跨设备分析

当用户与您的品牌互动时，他们会通过多种方式和多种设备进行互动。 跨设备分析与集成，以 [!DNL Adobe Experience Platform Identity Service] 确定设备如何映射到人。 然后，它利用这种智能创建用户行为的跨设备视图。 这使得能够在人而不是设备上进行分析。

## 跨设备分析概述

### 我不是我的设备

当用户与您的品牌互动时，他们会以多种方式在多个“表面”或“设备”上进行互动。 他们可能在PC或移动设备上使用Web浏览器，也可能使用移动应用程序。 在传统的数字分析中，每个表面都被表示为独特的“访客”。 这意味着您的每个用户都被表示为多个唯一访客。

以下是一个例子。 假设Isabelle通过以下方式与您的品牌互动：

*伊莎贝尔是三个访客*![的传统分析旅程](assets/cda-isabelle-journey-traditional-analytics.png)

伊莎贝尔的旅程分为三部分。 她被表示为三个独特的访客，每个任务使用不同的设备执行隔离的。 我们需要对伊莎贝拉的互动进行统一、跨设备的视图。 [!DNL Journey IQ: Cross-Device Analytics] 提供此视图。

*Isabelle是Cross*![-Device Analytics Journe](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨设备视图提供更好的分析

对伊莎贝拉的行为进行以人为中心、跨设备的视图，可以显着改变分析。 例如，传统的基于访客的方法无法全面了解营销渠道的有效性。 让我们再次看看伊莎贝尔的旅程，重点是渠道为其产品视图和购买产品获得信用。 我们使用最后 [!UICONTROL 一步归因] ，以实现简单性，但是，当您将伊莎贝拉的行为分为不同的访客时，使用任何归因模型都会出现同样的问题。 使用传统的访客视图世界，会产生非常不同甚至误导的结果：

*传统分析与跨设备分析归因*![比较](assets/channel-attribution.png)

请注意，通过跨设备视图，电子邮件渠道将收到产品视图和购买的信用，这更准确地反映了Isabelle的真实体验。

继续阅读以了解：

* How [!DNL Cross-Device Analytics] Works
* 先决条件 [!DNL Cross-Device Analytics]
* 解释跨设备数据
* Analysis Workspace跨设备数据分析

## How [!DNL Cross-Device Analytics] Works

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 集成， [!DNL Adobe Experience Platform Identity Service]利用[! [DNL Co-op Graph]](https://docs.adobe.com/content/help/zh-Hans/device-co-op/using/home.html) ，或 [!DNL Private Graph] 确定设备如何映射到人。 然后，它利用这种智能创建用户行为的跨设备视图。 CDA包含无可匹敌的功能和工具，可帮助您的企业了解多设备使用情况以及这些设备与品牌互动时的客户体验。 它位于Analysis Workspace下方，可以使用Floust、、和等强大工具，深入洞察基于人的受众分析和跨设备归因、细分和旅 [!UICONTROL 程分析][!DNL Flow]，以 [!DNL Cohort]及 [!DNL Segment IQ][!DNL Attribution IQ]。

### The [!DNL Cross-Device Virtual Report Suite]

CDA通过一种特殊的跨设备虚拟报 [[!UICONTROL 告套件来实现]](https://docs.adobe.com/content/help/zh-Hans/analytics/components/virtual-report-suites/vrs-about.html)。 这允许您在组织中引入跨设备分析时继续使用原始的基于设备的报表包。 设置CDA VRS很简单。

在VRS生成器的步骤之一中，选 [!UICONTROL 择Adobe] （已配置为启用CDA）的报表包：

*选择启用CDA的基本（源）报[!UICONTROL 表包]*![[!UICONTROL 虚拟报] 表包步骤1](assets/cda-vrs-step-one.png)

然后打开“ [!UICONTROL 报告时间处理] ”并启 [!UICONTROL 用跨设备拼接]:

*启[!UICONTROL 用报表时处理][!UICONTROL 和跨设备拼接虚]*![ 拟报表包第二步](assets/cda-vrs-step-two.png)

完成VRS设置并保存它。 CDA VRS将在Analysis Workspace显示，旁边有一个特殊图标，如下所示：

*在Analysis Workspace虚拟报告套件*![[!UICONTROL 中选择CDA] VRS第三步](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以在启用CDA [!UICONTROL 的基础报表] 包顶部创建任意数量的CDA虚 [!UICONTROL 拟报表包]。

### 重建历史

有时，您的用户需要一段时间才能登录，或 [!DNL Co-op Graph] 识别 [!DNL Private Graph] 他们并将他们的设备映射到一起。 CDA利用30天的回顾窗口，允许其将之前未识别的访客重新描述为过去长达30天的人。

这有什么用？ 回想一下Isabelle的用户旅程：

![[!DNL Cross-Device Analytics] 旅程](assets/cda-isabelle-journey-cross-device-analytics.png)

伊莎贝尔可能在购买前才登录，购买后 [!DNL Co-op Graph] 才 [!DNL Private Graph] 将Isabelle的设备映射到一起。 但CDA的30天回顾使CDA能够在个人层面重述伊莎贝拉的过去行为，为您提供她旅程的跨设备视图。

>[!NOTE]
>
>由于历史记录可以重述，这意味着您的数据可能会在启用CDA的虚拟报告套件中随 [!UICONTROL 时间而更改]。 当您通过基于CDA的分析交流洞察时，请牢记这一点。

## 跨设备 [!UICONTROL 分析的先决条件]

CDA随[! [DNL Analytics Ultimate]一起提供](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)。 自2019年9月起， [!DNL Analytics Ultimate] 符合以下先决条件的客户有资格使用CDA。 CDA的先决条件如下：

* 您的公司必须是[ [!DNL Adobe Experience Platform Identity Service] !DNL [合作图]的成员](https://docs.adobe.com/content/help/zh-Hans/device-co-op/using/home.html)，或者使用 [!DNL Adobe Experience Platform Identity Service Private Graph]。
* 您必须实现与图形同步 [!DNL Co-op Graph] 或包 [!DNL Private Graph] 括 [Experience CloudID(ECID)](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html) 和ID所需的一切。 请注意，除技术要求外，还有 [!DNL Co-op Graph] 其他法律和合同要求。
* 目前不可能将两个IMS组织用于一个组织， [!DNL Private Graph]因此您必须在一个IMS组织上实现标准化。 在某些情况下，具有多个IMS组织的客户可以将IMS与CDA [!DNL Co-op Graph] 结合使用。
* CDA [!DNL Co-op graph] 的 [!DNL Private Graph]和以及某些组件托管在中 [!DNL Microsoft Azure]。 这意味着 [!DNL Analytics] Adobe的数据处理中心和Adobe在数据中的存在之间来回复制数据 [!DNL Microsoft Azure]。 某些 [!DNL Analytics] 数据将存储在 [!DNL Azure]中。 您的公司必须同意此安排。
* CDA需要“跨设备”报 [!UICONTROL 告套件]。 即，您用于CDA [!UICONTROL 的报表包] ，必须包括来自多种不同设备类型或“界面”（如桌面Web、移动Web和移动应用程序）的数据。 自2019年9月起，此报告套件的服 [!UICONTROL 务器调用] 量必须为100MM/天或更少。 （服务器调用量限制将在未来几个月内增加。）
* 自2019年9月起， [!DNL Co-op Graph] 和仅 [!DNL Private Graph] 在北美提供。 未来将宣布在EMEA和APAC建立图形存在计划。 如果您在这些地区，我们建议您立即开始查看这些先决条件，以便在图形可用时准备好使用。

## 解释跨设备数据

### 非访客

在CDA虚 [!UICONTROL 拟报告套件]，您将看到一些更改。 例如，“唯一 [!UICONTROL 访客] ”量度被两个新量度替换： [!UICONTROL 人和] 独 [!UICONTROL 特设备]。 这些新指标可让您更好地了解受众大小。

*人与独特设备*![CDA人 [!UICONTROL 员指标]](assets/cda-people-metric.png)

在“区 [[!UICONTROL 段构建器]](https://docs.adobe.com/content/help/zh-Hans/analytics/components/segmentation/segmentation-workflow/seg-build.html)”中， [!UICONTROL 访客] 区段容器已被“人 [!UICONTROL 员”区段] 容器替换。 使用CDA VRS，您可以创建跨设备区段，如：

* 使用多个设备的用户
* 在移动设备上开始旅程，然后在桌面设备上购买的人
* 访问用户使用多台设备完成任务

*人员级别细分*![[!DNL Segment Builder][!UICONTROL 人员] 容器](assets/cda-segment-builder-person-container.png)

### Dimension持久性

在CDA VRS中，诸如尺寸现在可 [!DNL eVars] 自动跨设备保留。 例如， [!DNL eVar] 配置为：

* 分配：最近（最后）
* 在以下情况下过期：购买

现在，在触发购买事件之前，将自动在一台设备之间保留。

## Analysis Workspace跨设备数据分析

### 基于人的受众分析

您是否曾想过有多少人在与您的品牌互动？ 您是否想了解他们使用的设备数量和类型？ 它们的使用如何重叠？ 使用CDA VRS，您可以创建跨设备 [维恩图](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/venn.html) 和每人设备直方 [图](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/histogram.html)。

*基于人的受众*![分析源和直方图](assets/cda-venn-and-histogram.png)

### Cross-Device [!DNL Flow]

通过CDA和Analysis Workspace，您可以在[!DNL流可视化]中直观地了解人们如何随着时间的推移从 [一台设备移动到另一台设备](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)。 你可以看到他们在旅程中的下场，以及他们的下场。

*[!DNL Flow]与CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### Cross-Device [!DNL Fallout]

您可能会使 [用多种[!DNL流失可视化]](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html) ，分析用户在成功前通过一系列步骤实现该功能的效果。 您是否知道在使用传统的基 [!DNL Fallout visualizations] 于设备的分析时，您对这些视图的有限？ 要成功“落后”，下一步必须与上一步在同一个浏览器或应用程序中进行。 在基于设备的分析中，您看不到在其他设备上成功完成下一步的人员。

别担心，CDA已经帮你了。 CDA创建跨设备视图，使 [!DNL Fallout visualizations] 其更有用。 毕竟，真正重要的是这个人最终是否在某处成功地任务了。

*[!DNL Fallout]与CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

由于CDA在Analysis Workspace下面创建了一层跨设备数据，您的所有分析都将从跨设备的角度进行调味。 一个强大的示 [例是通过[!DNLAttribution IQ]](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)。 [!DNL Attribution IQ] 在Analysis Workspace，您可以并排比较多个归因模型。 现在，您可以将此功能与CDA结合使用，比较不同设备对成功的贡献。

例如，假设您想要了解手机是交互中第一个最终导致成功的设备的频率。 这代表移动电话的“获取率”。 CDA + [!DNL Attribution IQ] 允许您执行此分析:

*[!DNL Attribution IQ]与CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

For more information, see the [[!DNL Cross-Device Analytics] help documentation](https://docs.adobe.com/content/help/zh-Hans/analytics/components/cda/cda-home.html).
