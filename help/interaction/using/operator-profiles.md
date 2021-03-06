---
product: campaign
title: 操作员用户档案
description: 操作员用户档案
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 5%

---

# 操作员用户档案{#operator-profiles}

![](../../assets/v7-only.svg)

使用交互的运算符有两种类型：选件经理和投放经理。 它们各自具有特定权限，仅允许它们访问树和平台的某些部分。

* **[!UICONTROL Offer manager]** :创建和维护选件。 请注意，如果在工作流中使用了选件，则运算符将需要位于 **[!UICONTROL Administrator]** 或 **[!UICONTROL Offer managers]** 操作员组。
* **[!UICONTROL Delivery manager]** :批准和使用选件

创建特定于交互的运算符的步骤与创建平台上所有其他运算符的步骤相同。 如需详细信息，请参阅[此部分](../../platform/using/access-management.md)。权限在操作员创建期间进行配置。

## 选件管理器 {#offer-manager}

1. 创建新运算符。
1. 转到 **[!UICONTROL Groups and named rights]** 窗口，单击 **[!UICONTROL Add]** ，然后选择 **[!UICONTROL Offer manager]** 群组。

   ![](assets/offer_operators_create_001.png)

分配给选件管理器的权限允许他们执行以下任务：

* 修改 **[!UICONTROL Design]** 环境。
* 查看 **[!UICONTROL Live]** 环境。
* 配置管理功能（预定义空格和过滤器）。
* 创建和更改类别。
* 创建选件。
* 配置选件资格。
* 批准选件。

   >[!NOTE]
   >
   >在两种情况下，选件管理器只能批准选件。 第一个是，如果没有人特别指定为审阅者，第二个是，如果负责创建模板（具有指定审阅者的权限）的操作员在选件所依据的选件模板中将他们指定为审阅者。

## 投放管理器 {#delivery-manager}

1. 创建新运算符。
1. 转到 **[!UICONTROL Groups and named rights]** 窗口，单击 **[!UICONTROL Add]** ，然后选择 **[!UICONTROL Delivery manager]** 群组。

   ![](assets/offer_operators_create_002.png)

分配给投放管理器的权限，使他们能够执行以下任务：

* 显示 **[!UICONTROL Live]** 环境。
* 显示和修改选件类别。
* 如果将此投放管理器指定为其审阅者之一，则批准选件。

   >[!NOTE]
   >
   >只有在选件配置期间被定义为审阅者时，投放管理器才能批准选件。

## 根据运营者重新评估权利 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>选件管理器（编辑）</strong><br /> </td> 
   <td> <strong>选件管理器（正式启用）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的选件/实时选件<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipient — 环境<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 空间<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 预定义选件过滤器<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型规则<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠目录<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 选件类别<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
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
   <td> 正在编辑的选件/实时选件<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipient — 环境<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 空间<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 预定义选件过滤器<br /> </td> 
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类<br /> </td> 
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型规则<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠目录<br /> </td> 
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 选件类别<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
 </tbody> 
</table>
