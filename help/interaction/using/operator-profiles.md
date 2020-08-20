---
title: 操作员用户档案
seo-title: 操作员用户档案
description: 操作员用户档案
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3b752b283a14bc75954fe46da5a21970c1e17fa1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 5%

---


# 操作员用户档案{#operator-profiles}

使用交互的运算符有两种类型：优惠经理和投放经理。 他们每个人都具有特定权限，这些权限仅允许他们访问树和平台的某些部分。

* **[!UICONTROL Offer manager]** :创建和维护优惠。 请注意，如果工作流中使用了优惠，则操作员需要位于或运 **[!UICONTROL Administrator]** 算符组 **[!UICONTROL Offer managers]** 中才能执行工作流。
* **[!UICONTROL Delivery manager]** :批准和使用优惠

创建特定于交互的运算符的步骤与创建平台上所有其他运算符的步骤完全相同。 如需详细信息，请参阅[此部分](../../platform/using/access-management.md#creating-an-operator)。权限在操作员创建过程中进行配置。

## 优惠经理 {#offer-manager}

1. 创建新运算符。
1. 转到窗 **[!UICONTROL Groups and named rights]** 口，单 **[!UICONTROL Add]** 击并选择 **[!UICONTROL Offer manager]** 组。

   ![](assets/offer_operators_create_001.png)

分配给优惠管理者的权限使他们能够执行以下任务:

* 修改 **[!UICONTROL Design]** 环境。
* 视图 **[!UICONTROL Live]** 环境。
* 配置管理功能(预定义的空格和过滤器)。
* 创建和更改类别。
* 创建优惠。
* 配置优惠资格。
* 批准优惠。

   >[!NOTE]
   >
   >优惠经理只能在两种情况下批准优惠。 第一个是，如果没有人特别指定为审阅者，第二个是，负责创建模板（有权分配审阅者）的操作员在优惠模板中指定他／她作为审阅者，优惠基于该模板。

## 投放经理 {#delivery-manager}

1. 创建新运算符。
1. 转到窗 **[!UICONTROL Groups and named rights]** 口，单 **[!UICONTROL Add]** 击并选择 **[!UICONTROL Delivery manager]** 组。

   ![](assets/offer_operators_create_002.png)

分配给投放经理的权限可以／允许他们执行以下任务:

* 显示 **[!UICONTROL Live]** 环境。
* 显示和修改优惠类别。
* 如果指定优惠为其审阅者之一，则批准该审核。

   >[!NOTE]
   >
   >投放管理者只有在优惠配置期间被定义为审核者时才能批准优惠。

## 经营者权利重述 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>优惠管理器（编辑）</strong><br /> </td> 
   <td> <strong>优惠管理器（实时）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的优惠/实时优惠<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人-环境<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 预定义的优惠过滤器<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类规则<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠目录<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠类别<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>投放管理器（编辑）</strong><br /> </td> 
   <td> <strong>投放管理器（实时）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的优惠/实时优惠<br /> </td> 
   <td> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人-环境<br /> </td> 
   <td> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 预定义的优惠过滤器<br /> </td> 
   <td> 阅读<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 阅读<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类规则<br /> </td> 
   <td> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠目录<br /> </td> 
   <td> 阅读<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠类别<br /> </td> 
   <td> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
 </tbody> 
</table>

