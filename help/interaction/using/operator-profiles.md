---
title: 操作员配置文件
seo-title: 操作员配置文件
description: 操作员配置文件
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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 操作员配置文件{#operator-profiles}

使用交互的操作符有两种类型：选件经理和交付经理。 他们每个人都具有特定权限，这些权限仅允许他们访问树和平台的某些部分。

* **[!UICONTROL Offer manager]** :创建和维护选件
* **[!UICONTROL Delivery manager]** :批准和使用优惠

创建特定于“交互”的运算符的步骤与创建平台上所有其他运算符的步骤相同。 如需详细信息，请参阅[此部分](../../platform/using/access-management.md#creating-an-operator)。权限在操作员创建过程中进行配置。

## 优惠经理 {#offer-manager}

1. 创建新运算符。
1. 转到窗 **[!UICONTROL Groups and named rights]** 口，单击并 **[!UICONTROL Add]** 选择 **[!UICONTROL Offer manager]** 组。

   ![](assets/offer_operators_create_001.png)

分配给选件管理者的权限使他们能够执行以下任务：

* 修改 **[!UICONTROL Design]** 环境。
* 查看 **[!UICONTROL Live]** 环境。
* 配置管理功能（预定义的空格和过滤器）。
* 创建和更改类别。
* 创建选件。
* 配置选件资格。
* 批准选件。

   >[!NOTE]
   >
   >在两种情况下，选件管理者只能批准选件。 第一个是，如果没有人特别指定作为审阅者，第二个是，如果负责创建模板（有权分配审阅者）的操作员在选件所基于的选件模板中指定他／她作为审阅者。

## 交付管理器 {#delivery-manager}

1. 创建新运算符。
1. 转到窗 **[!UICONTROL Groups and named rights]** 口，单击并 **[!UICONTROL Add]** 选择 **[!UICONTROL Delivery manager]** 组。

   ![](assets/offer_operators_create_002.png)

分配给交付管理者的权限是／允许他们执行以下任务：

* 显示 **[!UICONTROL Live]** 环境。
* 显示和修改选件类别。
* 如果指定其审阅者之一批准选件。

   >[!NOTE]
   >
   >只有在选件配置过程中已将其定义为审阅人，交付管理者才能批准选件。

## 经营者权利重述 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>选件管理器（编辑）</strong><br /> </td> 
   <td> <strong>选件管理器（实时）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的选件／实时选件<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人——环境<br /> </td> 
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
   <td> 预定义的选件过滤器<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 读／写<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 排版规则<br /> </td> 
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
   <td> <strong>交付管理器（编辑）</strong><br /> </td> 
   <td> <strong>交付管理器（实时）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的选件／实时选件<br /> </td> 
   <td> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人——环境<br /> </td> 
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
   <td> 预定义的选件过滤器<br /> </td> 
   <td> 阅读<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 阅读<br /> </td> 
   <td> 阅读<br /> </td> 
  </tr> 
  <tr> 
   <td> 排版规则<br /> </td> 
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

