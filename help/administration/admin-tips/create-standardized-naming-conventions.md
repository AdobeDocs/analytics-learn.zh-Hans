---
title: 创建标准化的命名约定
description: 标准化命名约定适用于在AA管理员UI中启用变量名称本身以及传递到维度的值。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10531.jpg
kt: 10531
source-git-commit: 160df6c23acb67f1b07f2fcd25f1eca96eb6dee7
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 创建标准化的命名约定

**什么：** 标准化的命名约定适用于在Adobe Analytics(AA)管理员UI中启用变量名称本身，以及传递到维度的值。 (即，页面名称将为“页面名称(v1)”作为变量名称，传入的页面名称值应一致，并遵循特定结构/层次结构，如“sitename|homepage”或“sitename|search|searchresults”)。

**原因：** 命名约定是保持所有内容均匀、使界面易于用户理解的绝佳方式。 如果您从头开始创建这些代码，并在平台和代码中强制执行这些代码，则这些代码会更便于扩展。

**操作方法：** 界面和标记文档应与“名称”和“描述”匹配 — 这样，用户就无需提取Excel文档，而可以直接在界面中了解您的数据。 还建议将所有内容保留为小写，以保持一致性。

最好始终保持平台中的页面名称（或应用程序的屏幕名称）一致。 例如，您可以设置“property”:section:子部分：子部分：唯一页面名称”添加到变量/维度中。 如果所有这些字段都是数据层中的单独字段，您甚至可以直接在JS文件/Launch中构建页面名称。 将所有这些元素都设置在其自己的维度中，还可以帮助您更轻松地划分网站/应用程序的特定属性或区域，并更好地了解流量和流量。

任何能够让用户更轻松地查找和了解数据（包括诸如命名惯例之类的简单数据）的内容，都将提高Adobe Analytics的使用率，并为业务提供更好的洞察。

## 作者

本文档由以下人员共同编写：

![克里斯特尔·吉登](assets/Christel-Headshot-150.png)

Christel Guidon，NortonLifeLock Adobe Analytics Champion的Digital Analytics平台经理

![瑞秋·芬威克](assets/Rachel-Fenwick-150.png)

Rachel Fenwick，Adobe高级顾问
