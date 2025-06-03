---
product: campaign
title: Campaign操作员入门
description: 了解如何创建和管理活动用户
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 2%

---

# 创建和管理操作员 {#operators}

>[!CAUTION]
>
>* 从Campaign Classic v7.3.1开始，所有操作员都应使用[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}连接到Campaign。
>  &#x200B;>作为加强安全和身份验证过程的一部分，Adobe Campaign强烈建议将所有现有的操作员身份验证模式从登录/密码本机身份验证迁移到Adobe Identity Management System (IMS)。 在[此页面](../../technotes/using/migrate-users-to-ims.md)中了解如何迁移操作员。
> 
>* 进行此迁移后，请注意，以下部分不再适用。  请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hans){target="_blank"}以了解如何使用Adobe IMS设置权限。


## Campaign操作员入门 {#about-operators}

>[!NOTE]
>
>这些步骤仅适用于使用本机身份验证连接到Campaign的操作员。 有关Adobe IMS身份验证，请参阅[此文档](https://helpx.adobe.com/cn/enterprise/using/manage-users-individually.html#_blank)。

操作员是具有登录和执行操作权限的Adobe Campaign用户。

默认情况下，运算符存储在&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中。

![](assets/s_ncs_user_list_operators.png)

操作符可以手动创建，也可以在现有LDAP目录上映射。

[此页面](#creating-an-operator)中介绍了创建运算符的完整过程。

有关Adobe Campaign与LDAP集成的详细信息，请参阅[此页面](../../installation/using/connecting-through-ldap.md)。

>[!IMPORTANT]
>
>操作员需要链接到安全区域才能登录到实例。 有关Adobe Campaign中安全区域的详细信息，请参阅[此页面](../../installation/using/security-zones.md)。

用户还可以使用其Adobe ID直接连接到Adobe Campaign。 有关详细信息，请参见此 [ 页面](../../integrations/using/about-adobe-id.md)。

## 创建运算符 {#creating-an-operator}

要创建新操作员并授予权限，请执行以下步骤：

1. 单击运算符列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后输入新运算符的详细信息。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定用户的&#x200B;**[!UICONTROL Identification parameters]**：其登录名、密码和名称。 操作员将使用登录名和密码登录到Adobe Campaign。 用户登录后，可通过&#x200B;**[!UICONTROL Tools > Change password]**&#x200B;菜单更改密码。 操作员的电子邮件至关重要，因为它使操作员能够接收通知，例如，在处理审批时。

   利用此部分，还可以将操作员链接到组织实体。 有关详细信息，请参阅[此页面](../../distributed/using/about-distributed-marketing.md)。

1. 在&#x200B;**[!UICONTROL Operator access rights]**&#x200B;部分中选择授予操作员的权限。

   要向操作员分配权限，请单击权限列表上方的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后从可用组列表中选择一组操作员：

   ![](assets/s_ncs_user_permissions_operators.png)

   您还可以选择一个或多个命名权限（请参阅[命名权限](#named-rights)）。 为此，请单击&#x200B;**[!UICONTROL Folder]**&#x200B;字段右侧的箭头，然后选择&#x200B;**[!UICONTROL Named rights]**：

   ![](assets/s_ncs_user_rights_operators.png)

   选择要分配的组和/或命名权限，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;进行验证。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;以创建运算符：配置文件已添加到现有运算符的列表。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以通过创建新的运算符文件夹，根据自己的要求组织运算符。 为此，请右键单击操作员文件夹并选择&#x200B;**[!UICONTROL Add an 'Operators' folder]**。

创建操作员的配置文件后，您可以添加或更新其信息。 为此，请单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>**[!UICONTROL Session timeout]**&#x200B;字段允许您在FDA会话超时之前调整延迟。 有关详细信息，请参阅[关于联合数据访问](../../installation/using/about-fda.md)。

## 定义运算符的时区 {#time-zone-of-the-operator}

在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，您可以选择运算符的时区。 默认情况下，运算符在服务器时区工作。 但是，可以使用下拉列表选择其他时区。

[此页面](../../installation/using/time-zone-management.md)中介绍了时区的配置。

>[!NOTE]
>
>不同时区内的协作需要以UTC格式存储日期。 在以下上下文中，日期将以适当的时区进行转换：日期以用户时区显示时、导入和导出文件时、计划电子邮件投放时、在工作流中计划活动时（计划程序、等待、时间约束等）
>
>与这些上下文关联的限制和建议在Adobe Campaign文档的相关部分中介绍。

此外，**[!UICONTROL Regional settings]**&#x200B;下拉列表允许您选择显示日期和数字的格式。

## 添加权限 {#access-rights-options}

使用&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡更新链接到运算符的组和已命名权限。

![](assets/operator_profile_security_options.png)

**[!UICONTROL Edit the access parameters...]**&#x200B;链接允许您访问以下选项：

* 通过&#x200B;**[!UICONTROL Disable account]**&#x200B;选项，您可以禁用操作员的帐户：此用户将不再访问Adobe Campaign。

  >[!NOTE]
  >
  >即使其帐户被禁用，操作员仍可以从Campaign接收警报或通知。 要停止向此运营商发送Campaign通知，Adobe建议您从其用户档案中删除电子邮件地址。

* 通过&#x200B;**[!UICONTROL Forbid access from the rich client]**&#x200B;选项，您可以将Adobe Campaign的使用限制为[Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)，或者通过API使用：无法再访问Adobe Campaign客户端控制台。
* 可以将安全区链接到操作员。 有关详细信息，请参见[此页面](../../installation/using/security-zones.md)。
* 您还可以使用相应的链接定义受信任的IP掩码。

  如果操作员的IP地址在此列表中，则操作员无需输入密码即可连接到Adobe Campaign。

  您还可以指定一组IP地址，这些地址将被授权无需密码即可连接，如以下示例所示：

  ![](assets/operator_trustip.png)

  >[!NOTE]
  >
  >要安全地访问您的平台，必须谨慎使用此选项。

* 通过&#x200B;**[!UICONTROL Restrict to information found in sub-folders of:]**&#x200B;选项，您可以限制归属于文件夹运算符的权限。 只有在该选项中指定的节点的子文件夹对用户可见：

  ![](assets/s_ncs_user_restrictions_operators.png)

  >[!IMPORTANT]
  >
  >这是一个非常严格的限制，必须谨慎使用。 使用此类型权限登录的操作员只能查看指定文件夹的内容，而不能通过资源管理器访问树的任何其他节点。 但是，根据此操作员有权访问的功能（例如：工作流），用户可以显示通常存储在无法访问中的节点中的数据。

### 检查设置 {#check-settings}

**[!UICONTROL Audit]**&#x200B;选项卡允许您查看与运算符相关的信息。 各种选项卡会根据操作员的干预区域中定义的设置自动添加到。

您可以访问：

* 链接到运算符的文件夹的权限列表。

  ![](assets/operator_folder_permissions.png)

  >[!NOTE]
  >
  >有关详细信息，请参阅[文件夹访问管理](#folder-access-management)。

* 操作员审批日志。

  ![](assets/operator_profile_validations.png)

* 他们订阅的讨论区列表。
* 日历中的活动。
* 分配给它们的任务列表。

## 默认运算符 {#default-operators}

Adobe Campaign使用具有默认配置的用户档案的技术操作员：管理员（“管理员”）、计费（“计费”）、监控、Web应用程序代理(“webapp”)等。 其中一些取决于平台上安装的应用程序和选项：例如，“central”和“local”运算符仅在安装了“Distributed Marketing”（分布式营销）选项时才可见。

>[!IMPORTANT]
>
>默认情况下，当平台返回信息消息时，会通知这些技术操作员。 我们强烈建议向他们提供联系电子邮件。
>
>为确保Web应用程序正常运行，我们还建议不要为“webapp”运算符定义特定的区域设置。

默认情况下，“webapp”技术操作员具有指定的“管理”权限，这可能会导致安全风险。 要解决此问题，我们建议删除此权限。 操作步骤：

1. 从&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;以创建权限并将其命名为WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   [已命名权限](#named-rights)部分中详细介绍了已命名权限。

1. 从&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中，选择Web应用程序代理运算符(“webapp”)。

   选择&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡，并从列表中删除名为的ADMINISTRATION权限。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择您刚刚创建的WEBAPP，然后保存更改。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 分配“webapp”操作员对与该操作员相关的文件夹（主要是“收件人”文件夹）的读写数据访问权限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   有关修改树文件夹的权限的详情，请参见[文件夹访问管理](#folder-access-management)部分。

>[!NOTE]
>
>有关安全准则的更多信息，请参阅[Adobe Campaign安全配置核对清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。