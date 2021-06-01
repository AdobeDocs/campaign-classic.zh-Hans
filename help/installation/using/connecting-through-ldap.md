---
product: campaign
title: 通过 LDAP 连接
description: '了解如何使用LDAP登录Campaign '
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---

# 通过 LDAP 连接{#connecting-through-ldap}

## 配置Campaign和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP配置仅可用于内部部署或混合安装。

LDAP配置在部署向导中执行。 在第一个配置步骤中必须选择&#x200B;**[!UICONTROL LDAP integration]**&#x200B;选项。 请参阅[部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

利用窗口，可通过指定的LDAP目录配置Adobe Campaign用户的标识。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 在&#x200B;**[!UICONTROL LDAP server]**&#x200B;字段中指定LDAP服务器的地址。 您可以添加端口号。 默认情况下，使用的端口为389。
* 在下拉列表中，为用户选择身份验证方法：

   * 加密密码(**md5**)

      默认模式。

   * 纯文本密码+ SSL(**TLS**)

      整个身份验证过程（包括密码）已加密。 安全端口636不得在此模式下使用：Adobe Campaign会自动切换到安全模式。

      使用此身份验证模式时，在Linux中，证书由openLDAP客户端库验证。 我们建议使用有效的SSL证书，以便对身份验证过程进行加密。 否则，信息将以纯文本形式显示。

      证书也在Windows中验证。

   * Windows NT LAN管理器(**NTLM**)

      专有的Windows身份验证。 **[!UICONTROL Unique identifier]**&#x200B;仅用于域名。

   * 分布式密码身份验证(**DPA**)

      专有的Windows身份验证。 **[!UICONTROL Unique identifier]**&#x200B;仅用于域名(domain.com)。

   * 纯文本密码

      无加密（仅用于测试阶段）。

* 选择用户身份验证模式：**[!UICONTROL Automatically compute the unique user identifier]**（请参阅步骤[可分辨名称计算](#distinguished-name-calculation)）或&#x200B;**[!UICONTROL Search the unique user identifier in the directory]**（请参阅步骤[搜索标识符](#searching-for-identifiers)）。

## 兼容性 {#compatibility}

兼容的系统取决于所选的身份验证机制。 以下是操作系统和LDAP服务器的兼容性矩阵。

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows， Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows， Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM和DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 纯文本<br /> </td> 
   <td> Windows， Linux<br /> </td> 
   <td> Windows， Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 可分辨名称计算{#distinguished-name-calculation}

如果要计算可分辨名称(DN)标识符，则部署向导的下一步允许您配置计算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在&#x200B;**[!UICONTROL Distinguished Name]**&#x200B;字段的目录（可分辨名称 — DN）中指定用户的唯一标识符。

   **[!UICONTROL (login)]** 将替换为Adobe Campaign运算符的标识符。

   >[!CAUTION]
   >
   >**[!UICONTROL dc]**&#x200B;设置必须小写。

* 选择选项&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;以同步LDAP目录中的组和用户关联以及Adobe Campaign中的组和用户关联。

   选择此选项时，将启用&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**。

   如果填充这两个字段，Adobe Campaign将使用其自己的登录名和密码连接到LDAP服务器。 如果它们为空，Adobe Campaign将匿名连接到服务器。

## 搜索标识符{#searching-for-identifiers}

如果选择搜索标识符，则部署向导允许您配置搜索。

* 在&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**&#x200B;字段中，提供Adobe Campaign将连接以搜索标识符的标识符和密码。 如果它们为空，Adobe Campaign将匿名连接到服务器。
* 指定&#x200B;**[!UICONTROL Base identifier]**&#x200B;和&#x200B;**[!UICONTROL Search scope]**&#x200B;字段，以确定要从中开始搜索的LDAP目录的子集。

   在下拉列表中选择所需的模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      从给定级别开始，将以完整方式搜索LDAP目录。

   1. **[!UICONTROL Limited to the base]**.

      搜索中包含所有属性。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      将对目录的所有属性执行搜索，并从属性的第一级开始执行搜索。

* 使用&#x200B;**[!UICONTROL Filter]**&#x200B;字段，可指定元素以优化搜索范围。

## 配置LDAP授权{#configuring-ldap-authorizations}

选择&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项时，将显示此窗口。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必须指定多个参数才能找到用户所属的组或组及其相应权限，例如：

* **[!UICONTROL Database identifier]**&#x200B;字段，
* **[!UICONTROL Search scope]**&#x200B;字段，

   >[!NOTE]
   >
   >如果已选择搜索DN，则可以选择&#x200B;**[!UICONTROL Reuse the DN search parameters]**&#x200B;以结转DN的选定值和从上一屏幕搜索范围。

* **[!UICONTROL Rights search filter]**&#x200B;字段，根据登录名和用户的可分辨名称，
* **[!UICONTROL Attribute containing the group or authorization name]**&#x200B;字段，
* **[!UICONTROL Association mask]**&#x200B;字段，用于在Adobe Campaign中提取组名称及其关联权限。 您可以使用正则表达式来搜索名称。
* 选择&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**，以便自动向用户授予连接的访问权限。

单击&#x200B;**[!UICONTROL Save]**&#x200B;以完成实例的配置。

## 管理运算符{#managing-operators}

确认配置后，必须定义通过LDAP目录管理的Adobe Campaign运算符。

要使用LDAP目录来验证操作员的身份，请编辑相应的配置文件并单击&#x200B;**[!UICONTROL Edit the access parameters]**&#x200B;链接。 选择&#x200B;**[!UICONTROL Use LDAP for authentication]**&#x200B;选项：此运算符的&#x200B;**[!UICONTROL Password]**&#x200B;字段呈灰显状态。

![](assets/s_ncs_install_operator_in_ldap.png)

## 用例 {#use-cases}

本节提供了一些简单的用例，帮助您根据需要实现最合适的配置。

1. 已在LDAP目录中创建用户，但未在Adobe Campaign中创建。

   可以配置Adobe Campaign，以便用户通过其LDAP身份验证访问平台。 Adobe Campaign需要能够控制LDAP目录中ID/密码组合的有效性，以便能够在Adobe Campaign中即时创建运算符。 要执行此操作，请选中&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**&#x200B;选项。 在这种情况下，还需要配置组同步：需要选择&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项。

1. 用户已在Adobe Campaign中创建，但未在LDAP目录中创建。

   他们无法登录Adobe Campaign。

1. LDAP目录中有一个组在Adobe Campaign中不存在。

   此组将不会在Adobe Campaign中创建。 您需要创建组并同步这些组，才能通过&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项启用匹配。

1. 组存在于Adobe Campaign中，并且LDAP目录将在事件后激活：Adobe Campaign中的用户组不会自动替换为LDAP组的内容。 同样，如果组仅存在于Adobe Campaign中，则在LDAP中创建并同步该组之前，不能向其添加LDAP用户。

   无论是通过Adobe Campaign还是LDAP，从不会动态创建组。 需要在Adobe Campaign和LDAP目录中单独创建它们。

   LDAP目录中的组名称需要与Adobe Campaign组的名称一致。 其关联掩码在部署向导的最后一个配置阶段中定义：Adobe Campaign_(.*)。
