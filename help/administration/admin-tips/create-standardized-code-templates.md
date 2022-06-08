---
title: 创建标准化的代码模板
description: '对于基线实施(即您的公司认为所有Adobe Analytics网站必备的KPI)，您的组织应尽可能使用单一的实施方法。 '
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10532.jpg
kt: 10532
source-git-commit: 160df6c23acb67f1b07f2fcd25f1eca96eb6dee7
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 2%

---


# 创建标准化的代码模板

**什么：** 对于“基线”实施(即您的公司认为所有Adobe Analytics网站必备的KPI)，您的组织应尽可能使用单一的实施方法。 例如，在网站中使用相同的数据层结构，并利用相同的标签管理器规则/自定义代码来捕获内部搜索或访客资料信息等内容。

**原因：** 通过实施可重复且可扩展的基线，可以简化、轻松地添加新元素或新站点/应用程序，同时保持实施简洁且易于进行故障诊断。 使用统一的方法还可以让新管理员/开发人员更轻松地联机并了解他们正在处理的工作。

**操作方法：** 当新网站或标记增强功能联机时，可采用单格式模板将内容分发给开发人员。 通常，单词doc在可以概述以下项目的位置非常有用：

* 正在实施的变量、其用途以及设置时间。 例如：

| AA变量 | 描述 | 设置时间/位置 | 如何设置 |
|--- |--- |--- |--- |
| eVar8 | 内部搜索关键词 | 在登录内部搜索结果页面时 | 数据层 |
| event8 | 内部搜索计数 | 在登录内部搜索结果页面时 | 启动规则 |

* 详细介绍如何设置。 您可以在此处指定所需的任何数据层对象及其语法，以及需要配置的任何TMS规则和规则设置的详细信息。
* QA中涵盖了确保在成功测试用例中能够看到的测试用例以及所有变量。 概述在开发人员测试此增强功能时，成功实施应包括哪些内容。

理想情况下，您只需在下一个站点中调整本文档，以更新属性名称、页面命名约定等基础知识。 无需每次都重新设计轮子，您可以节省更多时间。

## 作者

本文档由以下人员共同编写：

![克里斯特尔·吉登](assets/Christel-Headshot-150.png)

Christel Guidon，NortonLifeLock Adobe Analytics Champion的Digital Analytics平台经理

![瑞秋·芬威克](assets/Rachel-Fenwick-150.png)

Rachel Fenwick，Adobe高级顾问
