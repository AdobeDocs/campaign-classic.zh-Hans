---
title: 通过LDAP连接
seo-title: 通过LDAP连接
description: 通过LDAP连接
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 通过LDAP连接{#connecting-through-ldap}

## 配置Campaign和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP配置仅可用于本地或混合安装。

LDAP配置在部署向导中执行。 在第 **[!UICONTROL LDAP integration]** 一个配置步骤中必须选择该选项。 请参阅部 [署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

通过该窗口，可以通过指定的LDAP目录配置Adobe Campaign用户的标识。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specify the address of the LDAP server in the **[!UICONTROL LDAP server]** field. 您可以添加端口号。 默认情况下，使用的端口为389。
* 在下拉列表中，选择用户的身份验证方法：

   * 加密密码(**md5**)

      默认模式。

   * 纯文本密码+ SSL(**TLS**)

      整个身份验证过程（包括密码）均经过加密。 安全端口636不能在此模式下使用：Adobe Campaign会自动切换到安全模式。

      当您使用此身份验证模式时，在Linux中，证书由openLDAP客户端库验证。 我们建议使用有效的SSL证书，以便加密身份验证过程。 否则，信息将以纯文本形式显示。

      证书也在Windows中进行验证。

   * Windows NT LAN Manager(**NTLM**)

      专有Windows身份验证。 仅 **[!UICONTROL Unique identifier]** 用于域名。

   * 分布式密码身份验证(**DPA**)

      专有Windows身份验证。 仅 **[!UICONTROL Unique identifier]** 用于域名(domain.com)。

   * 纯文本口令

      无加密（仅用于测试阶段）。

* 选择用户身份验证模式：(请参 **[!UICONTROL Automatically compute the unique user identifier]** 阅步骤辨 [别名计算](#distinguished-name-calculation))或(请参 **[!UICONTROL Search the unique user identifier in the directory]** 阅步骤 [搜索标识符](#searching-for-identifiers))。

## 兼容性 {#compatibility}

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
   <td> NTLM和DPA<br /> </td> 
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

## 辨别名计算 {#distinguished-name-calculation}

如果要计算辨别名(DN)标识符，则部署向导的下一步允许您配置计算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在字段的目录（辨别名- DN）中指定用户的唯一标识 **[!UICONTROL Distinguished Name]** 符。

   **[!UICONTROL (login)]** 将替换为Adobe Campaign运营商的标识符。

   >[!CAUTION]
   >
   >设 **[!UICONTROL dc]** 置必须为小写。

* 选择此选 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 项可同步LDAP目录中的组和用户关联以及Adobe Campaign中的组和用户关联。

   选择此选项时，将启 **[!UICONTROL Application level DN used for the search]** 用 **[!UICONTROL Password of the application login]** 和。

   如果填充这两个字段，Adobe Campaign将使用自己的登录名和密码连接到LDAP服务器。 如果它们为空，Adobe Campaign将匿名连接到服务器。

## 搜索标识符 {#searching-for-identifiers}

如果选择搜索标识符，则部署向导允许您配置搜索。

* 在和字 **[!UICONTROL Application level DN used for the search]** 段中， **[!UICONTROL Password of the application login]** 提供Adobe Campaign用来搜索标识符的标识符和密码。 如果它们为空，Adobe Campaign将匿名连接到服务器。
* 指定 **[!UICONTROL Base identifier]** 和字 **[!UICONTROL Search scope]** 段，以确定要从中开始搜索的LDAP目录子集。

   在下拉列表中选择所需的模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      从给定级别开始，将完整搜索LDAP目录。

   1. **[!UICONTROL Limited to the base]**.

      搜索中包含所有属性。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      该搜索从该属性的第一级开始，对该目录的所有属性执行。

* 该字 **[!UICONTROL Filter]** 段允许您指定元素以细化搜索范围。

## 配置LDAP授权 {#configuring-ldap-authorizations}

当您选择选项时，将显示此 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 窗口。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必须指定多个参数才能查找用户所属的一个或多个组及其相应权限，即：

* 场 **[!UICONTROL Database identifier]** 地，
* 场 **[!UICONTROL Search scope]** 地，

   >[!NOTE]
   >
   >如果选择搜索DN，则可以选择以 **[!UICONTROL Reuse the DN search parameters]** 便继承上一屏幕中DN的选定值和搜索范围。

* 根据 **[!UICONTROL Rights search filter]** 登录名和用户的辨别名，
* 关于 **[!UICONTROL Attribute containing the group or authorization name]** 用户的字段，
* 该字 **[!UICONTROL Association mask]** 段允许在Adobe Campaign中提取组名称及其关联权限。 可以使用正则表达式搜索名称。
* 选择 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 此选项，以便用户在连接时自动获得访问权限。

单击 **[!UICONTROL Save]** 以完成实例的配置。

## 管理运营商 {#managing-operators}

确认配置后，必须定义通过LDAP目录管理的Adobe Campaign操作符。

要使用LDAP目录验证操作符的身份，请编辑相应的配置文件，然后单击链 **[!UICONTROL Edit the access parameters]** 接。 选择选 **[!UICONTROL Use LDAP for authentication]** 项：此运 **[!UICONTROL Password]** 算符的字段将灰显。

![](assets/s_ncs_install_operator_in_ldap.png)

## 用例 {#use-cases}

本节提供几个简单的使用案例，帮助您根据需要实现最合适的配置。

1. 已在LDAP目录中创建用户，但未在Adobe Campaign中创建。

   可以配置Adobe Campaign，以便用户通过其LDAP身份验证访问平台。 Adobe Campaign需要能够控制LDAP目录中ID/密码组合的有效性，以便在Adobe Campaign中即时创建该运营商。 要执行此操作，请选中该 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 选项。 在这种情况下，还需要配置组同步：需 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 要选择此选项。

1. 该用户已在Adobe Campaign中创建，但未在LDAP目录中创建。

   他们将无法登录Adobe Campaign。

1. LDAP目录中有一个组，Adobe Campaign中不存在该组。

   此组不会在Adobe Campaign中创建。 您需要创建组并同步这些组，以通过选项启用匹 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 配。

1. Adobe Campaign中存在用户组，活动结束后将激活LDAP目录：Adobe Campaign中的用户组不会自动替换为LDAP组的内容。 同样，如果组仅存在于Adobe Campaign中，则在LDAP中创建并同步组之前，不能将LDAP用户添加到该组。

   不管是通过Adobe Campaign还是LDAP，用户组始终不会动态创建。 它们需要在Adobe Campaign和LDAP目录中单独创建。

   LDAP目录中的用户组名称需要与Adobe Campaign用户组的名称一致。 其关联掩码是在部署向导的最后一个配置阶段定义的：Adobe Campaign_(.*)。

