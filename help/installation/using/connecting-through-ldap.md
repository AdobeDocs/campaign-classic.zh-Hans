---
solution: Campaign Classic
product: campaign
title: 通过 LDAP 连接
description: '了解如何使用LDAP登录活动 '
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---


# 通过 LDAP 连接{#connecting-through-ldap}

## 配置活动和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP配置仅可用于内部部署或混合安装。

LDAP配置在部署向导中执行。 在第一个配置步骤中必须选择&#x200B;**[!UICONTROL LDAP integration]**&#x200B;选项。 请参阅[部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

通过该窗口，可以通过指定的LDAP目录配置Adobe Campaign用户的标识。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 在&#x200B;**[!UICONTROL LDAP server]**&#x200B;字段中指定LDAP服务器的地址。 您可以添加端口号。 默认情况下，使用的端口为389。
* 在下拉列表中，为用户选择身份验证方法：

   * 加密密码(**md5**)

      默认模式。

   * 纯文本密码+ SSL(**TLS**)

      整个身份验证过程（包括密码）都经过加密。 安全端口636不能在此模式下使用：Adobe Campaign自动切换到安全模式。

      使用此身份验证模式时，在Linux中，证书由openLDAP客户端库验证。 我们建议使用有效的SSL证书，以加密身份验证过程。 否则，信息将以纯文本形式显示。

      证书也在Windows中验证。

   * Windows NT LAN Manager(**NTLM**)

      专有Windows身份验证。 **[!UICONTROL Unique identifier]**&#x200B;仅用于域名。

   * 分布式密码身份验证(**DPA**)

      专有Windows身份验证。 **[!UICONTROL Unique identifier]**&#x200B;仅用于域名(domain.com)。

   * 纯文本密码

      无加密（仅用于测试阶段）。

* 选择用户身份验证模式：**[!UICONTROL Automatically compute the unique user identifier]**（请参阅步骤[可分辨名称计算](#distinguished-name-calculation)）或&#x200B;**[!UICONTROL Search the unique user identifier in the directory]**（请参阅步骤[搜索标识符](#searching-for-identifiers)）。

## 兼容性{#compatibility}

兼容的系统取决于选定的身份验证机制。 以下是操作系统和LDAP服务器的兼容性矩阵。

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
   <td> Windows、Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM &amp; DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 纯文本<br /> </td> 
   <td> Windows、Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
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
   >**[!UICONTROL dc]**&#x200B;设置必须以小写形式。

* 选择选项&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;以同步LDAP目录中的组和用户关联以及Adobe Campaign中的组和用户关联。

   选择此选项时，将启用&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**。

   如果填充这两个字段，Adobe Campaign将使用自己的登录名和口令连接到LDAP服务器。 如果它们为空，Adobe Campaign将匿名连接到服务器。

## 搜索标识符{#searching-for-identifiers}

如果选择搜索标识符，则部署向导允许您配置搜索。

* 在&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**&#x200B;字段中，提供Adobe Campaign将连接到的标识符和密码以搜索标识符。 如果它们为空，Adobe Campaign将匿名连接到服务器。
* 指定&#x200B;**[!UICONTROL Base identifier]**&#x200B;和&#x200B;**[!UICONTROL Search scope]**&#x200B;字段，以确定要从中开始搜索的LDAP目录子集。

   在下拉列表中选择所需的模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      从给定级别开始，将完整搜索LDAP目录。

   1. **[!UICONTROL Limited to the base]**.

      搜索中包含所有属性。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      从属性的第一级开始，对目录的所有属性执行搜索。

* **[!UICONTROL Filter]**&#x200B;字段允许您指定元素以细化搜索范围。

## 配置LDAP授权{#configuring-ldap-authorizations}

当您选择&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项时，将显示此窗口。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必须指定多个参数才能查找用户所属的组或组及其相应权限，即：

* **[!UICONTROL Database identifier]**&#x200B;字段，
* **[!UICONTROL Search scope]**&#x200B;字段，

   >[!NOTE]
   >
   >如果选择了搜索DN，则可以选择&#x200B;**[!UICONTROL Reuse the DN search parameters]**，以便结转DN的选定值和上一屏幕中的搜索范围。

* **[!UICONTROL Rights search filter]**&#x200B;字段，根据登录名和用户的可分辨名称，
* 关于用户的&#x200B;**[!UICONTROL Attribute containing the group or authorization name]**&#x200B;字段，
* **[!UICONTROL Association mask]**&#x200B;字段允许提取Adobe Campaign中的组名称及其关联权限。 您可以使用常规表达式搜索名称。
* 选择&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**，以便用户在连接时自动获得访问权限。

单击&#x200B;**[!UICONTROL Save]**&#x200B;以完成实例的配置。

## 管理运算符{#managing-operators}

确认配置后，必须定义通过LDAP目录管理的Adobe Campaign运算符。

要使用LDAP目录验证操作符的身份，请编辑相应的用户档案并单击&#x200B;**[!UICONTROL Edit the access parameters]**&#x200B;链接。 选择&#x200B;**[!UICONTROL Use LDAP for authentication]**&#x200B;选项：此运算符的&#x200B;**[!UICONTROL Password]**&#x200B;字段将灰显。

![](assets/s_ncs_install_operator_in_ldap.png)

## 用例 {#use-cases}

本节提供一些简单的使用案例，帮助您根据需要实现最合适的配置。

1. 已在LDAP目录中创建用户，但未在Adobe Campaign中创建。

   Adobe Campaign可以配置，以便用户通过其LDAP身份验证访问平台。 Adobe Campaign需要能够控制LDAP目录中ID/密码组合的有效性，以便能够在Adobe Campaign中动态创建运算符。 要执行此操作，请选中&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**&#x200B;选项。 在这种情况下，还需要配置组同步：需要选择&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项。

1. 用户已在Adobe Campaign中创建，但未在LDAP目录中创建。

   他们无法登录Adobe Campaign。

1. LDAP目录中有一个组，该组在Adobe Campaign中不存在。

   此组不会在Adobe Campaign中创建。 您需要创建组并同步这些组，以通过&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;选项启用匹配。

1. 组存在于Adobe Campaign中，LDAP目录将在事件后激活：Adobe Campaign中的用户组不会自动替换为LDAP用户组的内容。 同样，如果组仅存在于Adobe Campaign中，则在LDAP中创建并同步组之前，不能将LDAP用户添加到该组。

   无论是通过Adobe Campaign还是LDAP，始终不会动态创建组。 它们需要在Adobe Campaign和LDAP目录中单独创建。

   LDAP目录中用户组的名称需要与Adobe Campaign用户组的名称相同。 其关联掩码是在部署向导的最后一个配置阶段定义的：Adobe Campaign_(.*)。

