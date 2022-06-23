---
title: 创建标准的命名惯例
description: 标准命名惯例既适用于在 AA Admin UI 中启用的变量名称本身，也适用于传递到维度中的值。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10531.jpg
kt: 10531
exl-id: 0fe3b981-0d9b-4f12-a6ca-63a4140f4baf
source-git-commit: df00d4fb8cc5093903ed4628dfe12f152294123a
workflow-type: ht
source-wordcount: '339'
ht-degree: 100%

---

# 创建标准的命名惯例

**内容：**&#x200B;标准命名惯例既适用于在 Adobe Analytics (AA) Admin UI 中启用的变量名称本身，也适用于传递到维度中的值。（即，页面名称将“页面名称 (v1)作为变量名称，传入的页面名称值应统一一致，并遵循特定的结构/层级结构，如“站点名称 | 主页”或“站点名称 | 搜索 | 搜索结果”）。

**原因：**&#x200B;命名惯例是一种保持所有内容统一一致的好方法，可使界面易于用户理解。如果您从一开始就创建这些惯例，并在平台和代码中进行实施，则会更容易扩展。

**方法：**&#x200B;界面和标记文档应与“名称”和“描述”匹配，这样用户就不必调出 Excel 文档，并且可以直接在界面中理解您的数据。为了保持一致性，还建议将所有内容保持小写。

最好在整个平台上保持页面名称（或应用程序的屏幕名称）一致。例如，可以将“property :section:sub section:sub sub section:unique page name”设置为变量/维度。如果所有这些都是数据层中的单独字段，那么您甚至可以直接在 JS 文件/Launch 中生成页面名称。将所有这些元素设置为其各自的维度，可以帮助您更轻松地分解站点/应用程序的特定属性或区域，并更好地了解流量和流程。

任何有助于用户查找和理解数据的内容（包括一些简单的命名惯例）都会增加对 Adobe Analytics 的使用，并为商业提供更优质的洞察。

## 作者

本文件由以下人员共同编写：

![Christel Guidon](assets/Christel-Headshot-150.png)

NortonLifeLock 数字分析平台经理 Christel Guidon
Adobe Analytics Champion

![Rachel Fenwick](assets/Rachel-Fenwick-150.png)

Adobe 高级顾问 Rachel Fenwick
