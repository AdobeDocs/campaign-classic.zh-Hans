---
title: 高级功能
seo-title: 高级功能
description: 高级功能
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 5%

---


# 高级功能{#advanced-functionalities}

## 添加脚本 {#adding-a-script}

### 脚本活动 {#script-activity}

此活动使您能够处理数据并轻松创建不启用SQL语言的复杂查询。

只需在脚本窗口中输入查询。

该选 **[!UICONTROL Texts]** 项卡允许您定义文本字符串。 然后，可以使用以下语法： **$（标识符）**。 有关使用文本的详细信息， [请参阅添加页眉和页脚](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我们不建议使用JavaScript代码创建聚合。

要创建报表的历史记录，请在JavaScript查询中添加以下代码行以保存存档数据：

```
if( ctx.@_historyId.toString().length == 0 )
```

否则，将显示当前数据。

### 外部脚本 {#external-script}

可以使用将在服务器和／或客户端执行的外部脚本。 操作步骤：

1. 编辑报表属性，然后单击 **[!UICONTROL Scripts]**。
1. 单 **[!UICONTROL Add]** 击并选择要引用的脚本。
1. 然后选择执行模式。

   如果添加多个脚本，请使用工具栏的箭头定义其执行顺序。

   ![](assets/reporting_custom_js.png)

## 调用另一个报告 {#calling-up-another-report}

### 跳转活动 {#jump-activity}

跳转就像没有箭头的过渡:它允许您从一个活动转到另一个报表或访问另一个报表。
