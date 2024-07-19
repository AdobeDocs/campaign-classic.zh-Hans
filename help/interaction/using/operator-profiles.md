---
product: campaign
title: 操作员用户档案
description: 操作员用户档案
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---

# 操作员用户档案{#operator-profiles}



有两种类型的操作员使用交互：优惠经理和投放经理。 每个用户都具有特定的权限，这些权限仅允许他们访问树的某些部分和平台。

* **[!UICONTROL Offer manager]** ：创建和维护优惠。 请注意，如果在工作流中使用选件，则运算符需要位于&#x200B;**[!UICONTROL Administrator]**&#x200B;或&#x200B;**[!UICONTROL Offer managers]**&#x200B;运算符组中才能执行工作流。
* **[!UICONTROL Delivery manager]** ：批准和使用优惠

创建特定于交互的运算符的步骤与创建平台上所有其他运算符的步骤相同。 有关详细信息，请参阅[此部分](../../platform/using/access-management.md)。 权限是在创建操作员期间配置的。

## 选件管理器 {#offer-manager}

1. 创建新运算符。
1. 转到&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择&#x200B;**[!UICONTROL Offer manager]**&#x200B;组。

   ![](assets/offer_operators_create_001.png)

分配给选件管理器的权限允许他们执行以下任务：

* 修改&#x200B;**[!UICONTROL Design]**&#x200B;环境。
* 查看&#x200B;**[!UICONTROL Live]**&#x200B;环境。
* 配置管理函数（预定义空格和过滤器）。
* 创建和更改类别。
* 创建选件。
* 配置优惠资格。
* 批准选件。

  >[!NOTE]
  >
  >优惠经理只能在两种特定情况下批准优惠。 第一种情况是，如果具体没有指定任何人为审核者，第二种情况是，负责创建模板（有权指定审核者）的操作员在选件所依据的选件模板中将他们指定为审核者。

## 投放管理器 {#delivery-manager}

1. 创建新运算符。
1. 转到&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择&#x200B;**[!UICONTROL Delivery manager]**&#x200B;组。

   ![](assets/offer_operators_create_002.png)

分配给投放经理的权限允许他们执行以下任务：

* 显示&#x200B;**[!UICONTROL Live]**&#x200B;环境。
* 显示和修改优惠类别。
* 批准选件（如果将此投放管理器指定为其审阅者之一）。

  >[!NOTE]
  >
  >仅当在选件配置期间已将投放经理定义为审阅者时，他们才能批准选件。

## 根据操作员回顾权限 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>选件管理器（正在编辑）</strong><br /> </td> 
   <td> <strong>选件管理器（启动）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的优惠/实时优惠<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人 — 环境<br /> </td> 
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
   <td> 预定义优惠过滤器<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型<br /> </td> 
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
   <td> 优惠类别<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>投放管理器（正在编辑）</strong><br /> </td> 
   <td> <strong>投放管理器（启动）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>树结构级别</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在编辑的优惠/实时优惠<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人 — 环境<br /> </td> 
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
   <td> 预定义优惠过滤器<br /> </td> 
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型<br /> </td> 
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
   <td> 优惠类别<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
  </tr> 
 </tbody> 
</table>
