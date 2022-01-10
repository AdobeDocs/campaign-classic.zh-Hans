---
product: campaign
title: Campaign操作员入门
description: 了解如何创建和管理Campaign用户
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# 创建和管理操作员 {#operators}

![](../../assets/common.svg)

## Campaign操作员入门  {#about-operators}

操作员是具有登录和执行操作权限的Adobe Campaign用户。

默认情况下，运算符存储在 **[!UICONTROL Administration > Access management > Operators]** 节点。

![](assets/s_ncs_user_list_operators.png)

可以手动创建或映射现有LDAP目录上的运算符。

有关创建运算符的完整过程，请参见 [本页](#creating-an-operator).

有关Adobe Campaign与LDAP集成的更多信息，请参阅 [本页](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>操作员需要链接到安全区域才能登录到实例。 有关Adobe Campaign安全区的更多信息，请参阅 [本页](../../installation/using/security-zones.md).

用户还可以使用其Adobe ID直接连接到Adobe Campaign。 有关详细信息，请参见此 [ 页面](../../integrations/using/about-adobe-id.md)。

## 创建运算符 {#creating-an-operator}

要创建新运算符并授予权限，请执行以下步骤：

1. 单击 **[!UICONTROL New]** 按钮，并输入新运算符的详细信息。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定 **[!UICONTROL Identification parameters]** 用户：其登录名、密码和名称。 操作员将使用登录名和密码登录到Adobe Campaign。 用户登录后，即可通过 **[!UICONTROL Tools > Change password]** 菜单。 操作员的电子邮件至关重要，因为它使操作员能够接收通知，例如在处理批准时。

   此部分还允许您将运算符链接到组织实体。 有关更多信息，请参阅 [本页](../../distributed/using/about-distributed-marketing.md).

1. 在 **[!UICONTROL Operator access rights]** 中。

   要为运算符分配权限，请单击 **[!UICONTROL Add]** 按钮，然后从可用组列表中选择一组运算符：

   ![](assets/s_ncs_user_permissions_operators.png)

   您还可以选择一个或多个命名权限(请参阅 [已命名权限](#named-rights))。 为此，请单击 **[!UICONTROL Folder]** 字段，然后选择 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   选择要分配的组和/或命名权限并单击 **[!UICONTROL OK]** 验证。

1. 单击 **[!UICONTROL Ok]** 要创建运算符，请执行以下操作：该用户档案将添加到现有运算符的列表。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以通过创建新的操作员文件夹，根据您的要求组织操作员。 要执行此操作，请右键单击运算符文件夹，然后选择 **[!UICONTROL Add an 'Operators' folder]**.

创建操作员的用户档案后，即可添加或更新其信息。 为此，请单击 **[!UICONTROL Edit]** 选项卡。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>的 **[!UICONTROL Session timeout]** 字段可让您调整FDA会话超时前的延迟。 有关更多信息，请参阅 [关于联合数据访问](../../installation/using/about-fda.md).

## 定义运算符的时区 {#time-zone-of-the-operator}

在 **[!UICONTROL General]** 选项卡，则可以选择运算符的时区。 默认情况下，运算符在服务器时区中工作。 但是，可以使用下拉列表选择其他时区。

时区的配置在 [本页](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>不同时区内的协作需要按UTC存储日期。 在以下上下文中，日期将以相应的时区进行转换：在用户时区中显示日期时，导入和导出文件时，计划电子邮件投放时，在工作流中计划活动时（调度程序、等待、时间约束等）
>
>与这些情况相关的限制因素和建议见Adobe Campaign文档的相关章节。

此外， **[!UICONTROL Regional settings]** 下拉列表允许您选择显示日期和数字的格式。

## 添加权限 {#access-rights-options}

使用 **[!UICONTROL Access rights]** 选项卡，以更新链接到运算符的组和命名权限。

![](assets/operator_profile_security_options.png)

的 **[!UICONTROL Edit the access parameters...]** 链接允许您访问以下选项：

* 的 **[!UICONTROL Disable account]** 选项允许您禁用操作员的帐户：此用户将不再访问Adobe Campaign。

   >[!NOTE]
   >
   >即使其帐户被禁用，操作员仍可以从Campaign接收警报或通知。 要停止向此运算符发送Campaign通知，Adobe建议您从其用户档案中删除电子邮件地址。

* 的 **[!UICONTROL Forbid access from the rich client]** 选项，您可以将Adobe Campaign的使用限制为 [Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 或通过API:对Adobe Campaign客户端控制台的访问权限不再可用。
* 可以将安全区与操作员链接。 有关详细信息，请参见[此页面](../../installation/using/security-zones.md)。
* 您还可以使用相应的链接定义可信IP掩码。

   如果操作员的IP地址在此列表中，则他们将能够连接到Adobe Campaign，而无需输入其密码。

   您还可以指定一组IP地址，这些地址将在无密码的情况下被授权连接，例如以下示例中的：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >要保护对平台的访问安全，必须谨慎使用此选项。

* 的 **[!UICONTROL Restrict to information found in sub-folders of:]** 选项可限制分配给文件夹运算符的权限。 只有此选项中指定的节点的子文件夹才对用户可见：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >这是非常严格的限制，必须谨慎使用。 使用此类权限登录的操作员只能查看指定文件夹的内容，并且无法通过资源管理器访问树的任何其他节点。 但是，根据此操作员有权访问的功能(例如：工作流)，则用户可以显示通常存储在无法访问的节点中的数据。

### 检查设置 {#check-settings}

的 **[!UICONTROL Audit]** 选项卡，可查看与运算符相关的信息。 根据操作员干预区域中定义的设置，将各种选项卡自动添加到中。

您可以访问：

* 链接到运算符的文件夹的权限列表。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有关更多信息，请参阅 [文件夹访问管理](#folder-access-management).

* 操作员批准日志。

   ![](assets/operator_profile_validations.png)

* 他们订阅的论坛列表。
* 活动。
* 分配给它们的任务列表。

## 默认运算符 {#default-operators}

Adobe Campaign使用默认配置了用户档案的技术运算符：管理员（“管理员”）、账单（“账单”）、监控、Web应用程序代理(“webapp”)等。 其中某些选项取决于平台上安装的应用程序和选项：例如，“中心”和“本地”运算符仅在安装“分布式营销”选项时才可见。

>[!IMPORTANT]
>
>当平台返回信息消息时，默认情况下会通知这些技术操作员。 我们强烈建议向他们提供联系电子邮件。
>
>为确保Web应用程序正常运行，我们还建议不要为“webapp”运算符定义特定的区域设置。

默认情况下，“webapp”技术操作员具有命名的“管理”权限，这可能会导致安全风险。 要解决此问题，我们建议删除此权限。 操作步骤：

1. 从 **[!UICONTROL Administration > Access management > Named rights]** 节点，单击 **[!UICONTROL New]** 创建权限并将其命名为WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   有关命名权限的详细信息，请参阅 [已命名权限](#named-rights) 中。

1. 从 **[!UICONTROL Administration > Access management > Operators]** 节点，选择Web应用程序代理运算符(“webapp”)。

   选择 **[!UICONTROL Edit]** 选项卡，然后 **[!UICONTROL Access rights]** 选项卡，并从列表中删除名为的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   单击 **[!UICONTROL Add]** 并选择之前创建的WEB应用程序权限，然后保存更改。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 为与此运算符相关的文件夹（主要是“收件人”文件夹）分配“webapp”运算符的读取和写入数据访问权限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   有关修改树文件夹权限的详情，请参阅 [文件夹访问管理](#folder-access-management) 中。

>[!NOTE]
>
>有关安全准则的更多信息，请参阅 [Adobe Campaign安全配置检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html).
