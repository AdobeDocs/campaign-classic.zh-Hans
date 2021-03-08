---
solution: Campaign Classic
product: campaign
title: 操作员用户档案
description: 操作员用户档案
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 5%

---


# 操作员用户档案{#operator-profiles}

使用交互的运算符有两种类型：优惠经理和投放经理。 他们每个人都拥有特定的权限，这些权限仅允许他们访问树和平台的某些部分。

* **[!UICONTROL Offer manager]** :创建和维护优惠。请注意，如果工作流中使用了优惠，则运算符需要位于&#x200B;**[!UICONTROL Administrator]**&#x200B;或&#x200B;**[!UICONTROL Offer managers]**&#x200B;运算符组中才能执行工作流。
* **[!UICONTROL Delivery manager]** :批准和使用优惠

创建特定于交互的运算符的步骤与创建平台上所有其他运算符的步骤完全相同。 如需详细信息，请参阅[此部分](../../platform/using/access-management.md)。权限在操作员创建过程中进行配置。

## 优惠管理器{#offer-manager}

1. 创建新运算符。
1. 转到&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择&#x200B;**[!UICONTROL Offer manager]**&#x200B;组。

   ![](assets/offer_operators_create_001.png)

分配给优惠经理的权限使他们能够执行以下任务:

* 修改&#x200B;**[!UICONTROL Design]**&#x200B;环境。
* 视图&#x200B;**[!UICONTROL Live]**&#x200B;环境。
* 配置管理功能(预定义的空格和过滤器)。
* 创建和更改类别。
* 创建优惠。
* 配置优惠资格。
* 批准优惠。

   >[!NOTE]
   >
   >优惠经理只能在两种情况下批准优惠。 第一个是，如果没有人特别指定为审阅者，第二个是，如果负责创建模板（有权分配审阅者）的操作员在优惠所基于的优惠模板中指定他/她为审阅者。

## 投放管理器{#delivery-manager}

1. 创建新运算符。
1. 转到&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择&#x200B;**[!UICONTROL Delivery manager]**&#x200B;组。

   ![](assets/offer_operators_create_002.png)

分配给投放经理的权限可以/允许他们执行以下任务:

* 显示&#x200B;**[!UICONTROL Live]**&#x200B;环境。
* 显示和修改优惠类别。
* 如果指定优惠为审核者之一，则批准审核。

   >[!NOTE]
   >
   >只有在投放配置期间将优惠定义为审阅者，优惠管理器才能批准该。

## 根据运算符{#recap-of-rights-according-to-operator}的权利回顾

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
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人 - 环境<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 预定义的优惠过滤器<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 读/写<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类规则<br /> </td> 
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
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人 - 环境<br /> </td> 
   <td> </td> 
   <td> 读取<br /> </td> 
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
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 类型学<br /> </td> 
   <td> 读取<br /> </td> 
   <td> 读取<br /> </td> 
  </tr> 
  <tr> 
   <td> 分类规则<br /> </td> 
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

