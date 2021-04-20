---
solution: Campaign Classic
product: campaign
title: 开始使用活动运算符
description: 了解如何创建和管理活动用户
feature: Access Management
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---


# 创建和管理运算符{#operators}

## 开始使用活动运算符{#about-operators}

操作员是具有登录和执行操作权限的Adobe Campaign用户。

默认情况下，运算符存储在&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中。

![](assets/s_ncs_user_list_operators.png)

可以手动创建运算符，也可以在现有LDAP目录上映射运算符。

有关创建运算符的完整过程，请参阅[此页](#creating-an-operator)。

有关Adobe Campaign和LDAP集成的详细信息，请参阅[此页](../../installation/using/connecting-through-ldap.md)。

>[!IMPORTANT]
>
>要登录到实例，操作符需要链接到安全区域。 有关Adobe Campaign中安全区域的详细信息，请参阅[此页](../../installation/using/security-zones.md)。

用户还可以使用其Adobe ID直接连接到Adobe Campaign。 有关详细信息，请参见此 [ 页面](../../integrations/using/about-adobe-id.md)。

## 创建运算符{#creating-an-operator}

要创建新操作员并授予权限，请执行以下步骤：

1. 单击位于运算符列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后输入新运算符的详细信息。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定用户的&#x200B;**[!UICONTROL Identification parameters]**:其登录名、密码和名称。 操作员将使用登录名和密码登录Adobe Campaign。 用户登录后，可以通过&#x200B;**[!UICONTROL Tools > Change password]**&#x200B;菜单更改其口令。 运营商的电子邮件至关重要，因为它使运营商能够接收通知，例如在处理批准时。

   此部分还允许您将运算符链接到组织实体。 有关详细信息，请参阅[此页](../../campaign/using/about-distributed-marketing.md)。

1. 在&#x200B;**[!UICONTROL Operator access rights]**&#x200B;部分中选择授予操作员的权限。

   要将权限分配给操作员，请单击位于权限列表上方的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后从可用组列表中选择一个操作员组:

   ![](assets/s_ncs_user_permissions_operators.png)

   您还可以选择一个或多个已命名权限(请参阅[已命名权限](#named-rights))。 要执行此操作，请单击&#x200B;**[!UICONTROL Folder]**&#x200B;字段右侧的箭头，然后选择&#x200B;**[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   选择要分配的组和/或已命名权限，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以验证。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;以创建运算符：用户档案将添加到现有运算符的列表中。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以根据您的要求，通过创建新的操作员文件夹来组织操作员。 要执行此操作，请右键单击操作符文件夹，然后选择&#x200B;**[!UICONTROL Add an 'Operators' folder]**。

创建操作员的用户档案后，您可以添加或更新其信息。 要执行此操作，请单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>通过&#x200B;**[!UICONTROL Session timeout]**&#x200B;字段，可以调整联合数据访问会话超时之前的延迟。 有关详细信息，请参阅[关于联合数据访问](../../installation/using/about-fda.md)。

## 定义运算符的时区{#time-zone-of-the-operator}

在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，可以选择运算符的时区。 默认情况下，运算符在服务器时区中工作。 但是，可以使用下拉列表选择其他时区。

有关时区的配置，请参见[此页](../../installation/using/time-zone-management.md)。

>[!NOTE]
>
>不同时区内的协作需要存储UTC中的日期。 日期将在以下上下文的适当时区转换：在用户时区中显示日期时，在导入和导出文件时，在计划电子邮件投放时，在工作流中计划活动时(调度程序、等待、时间约束等)
>
>与这些上下文相关的限制和建议见Adobe Campaign文件的相关章节。

此外，**[!UICONTROL Regional settings]**&#x200B;下拉列表允许您选择显示日期和数字的格式。

## 添加权限{#access-rights-options}

使用&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡可更新链接到运算符的组和已命名权限。

![](assets/operator_profile_security_options.png)

**[!UICONTROL Edit the access parameters...]**&#x200B;链接允许您访问以下选项：

* 使用&#x200B;**[!UICONTROL Disable account]**&#x200B;选项可以禁用运算符的帐户：他不再能接触Adobe Campaign。

   >[!NOTE]
   >
   >即使禁用了该帐户，操作员仍可以接收来自活动的警报或通知。 要停止向此操作员发送活动通知，Adobe建议您从其用户档案中删除电子邮件地址。

* 通过&#x200B;**[!UICONTROL Forbid access from the rich client]**&#x200B;选项，可将Adobe Campaign的使用限制为[Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)或通过API:访问Adobe Campaign客户端控制台不再可用。
* 可以将安全区与操作员链接。 有关详细信息，请参见[此页面](../../installation/using/security-zones.md)。
* 您还可以使用相应的链接定义可信IP掩码。

   如果Adobe Campaign的IP地址在此列表中，则操作员将能够连接到，而无需输入密码。

   您还可以指定一组IP地址，这些地址将授权在不使用口令的情况下进行连接，如以下示例中所示：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >要保证对平台的安全访问，必须谨慎使用此选项。

* 通过&#x200B;**[!UICONTROL Restrict to information found in sub-folders of:]**&#x200B;选项，可限制属于文件夹运算符的权限。 用户只能看到此选项中指定的节点的子文件夹：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >这是非常严格的限制，必须谨慎使用。 使用此类权限登录的运算符只能查看指定文件夹的内容，并且无法通过资源管理器访问树的任何其他节点。 但是，具体取决于他可以访问的功能(例如：工作流)，他可以显示通常存储在他看不到的节点中的数据。

### 检查设置{#check-settings}

使用&#x200B;**[!UICONTROL Audit]**&#x200B;选项卡可以视图与操作符相关的信息。 根据操作员干预区域中定义的设置自动添加各种选项卡。

您可以访问：

* 列表与操作员链接的文件夹的权限。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有关详细信息，请参阅[文件夹访问管理](#folder-access-management)。

* 操作员批准日志。

   ![](assets/operator_profile_validations.png)

* 他们订阅的论坛的列表。
* 事件。
* 分配给他们的任务的列表。

## 默认运算符{#default-operators}

Adobe Campaign使用技术操作符并配置默认用户档案:管理员（“管理员”）、帐单（“帐单”）、监控、Web 应用程序代理(“webapp”)等 其中一些取决于平台上安装的应用程序和选项：例如，“central”和“local”运算符仅在安装了“分布式营销”选项时才可见。

>[!IMPORTANT]
>
>默认情况下，当平台返回信息消息时，会通知这些技术运营商。 我们强烈建议为他们提供联系电子邮件。
>
>为确保Web 应用程序正确运行，我们还建议不为“webapp”运算符定义特定区域设置。

默认情况下，“webapp”技术运营商具有命名的ADMINISTRATION权限，这会导致安全风险。 要解决此问题，建议删除此权限。 操作步骤：

1. 在&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;创建一个右侧，并将其命名为WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   已命名权限详见[已命名权限](#named-rights)部分。

1. 从&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中，选择Web 应用程序代理运算符(“webapp”)。

   选择&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡，并从列表中删除名为right的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   单击&#x200B;**[!UICONTROL Add]**，选择刚刚创建的WEBAPP，然后保存更改。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 为与此操作符(主要是“收件人”文件夹)相关的文件夹分配“webapp”操作符读取和写入数据访问权限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   [文件夹访问管理](#folder-access-management)部分详细介绍了修改树状文件夹的权限。

>[!NOTE]
>
>有关安全指南的详细信息，请参阅[Adobe Campaign安全配置清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。
