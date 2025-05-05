---
title: 将Campaign操作员迁移到AdobeIdentity Management System (IMS)
description: 了解如何将Campaign操作员迁移到AdobeIdentity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 2%

---

# 将Campaign操作员迁移到AdobeIdentity Management System (IMS) {#migrate-users-to-ims}

作为加强安全和身份验证过程的一部分，Adobe Campaign强烈建议将最终用户身份验证模式从登录/密码本机身份验证迁移到AdobeIdentity Management System (IMS)。 所有操作员都应实施[AdobeIdentity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}以连接到Campaign。

在[此页面](ac-ims.md)中了解有关此迁移的更多信息。

## 更改了哪些内容？ {#move-to-ims-changes}

借助Campaign Classic，所有常规用户均已通过AdobeAdobe Campaign System (IMS)，使用其Adobe ID连接到Identity Management客户端控制台。 但是，用户/密码连接仍然可用。 Campaign v8将不再允许这样做。

此外，作为加强安全和身份验证过程的一部分，Adobe Campaign客户端应用程序现在使用IMS技术帐户令牌直接调用Campaign API。 有关技术操作员的迁移详情，请参阅[此页面](ims-migration.md)中的专篇文章。

此更改已适用于Campaign Classicv7，如果要移动到Campaign v8，此更改将为&#x200B;**必需**。

Adobe在此迁移工作中支持您。 您可以在下面文章中找到详细的上下文和分步指南。

## 您是否受影响？{#migrate-ims-impacts}

此过程适用于所有尚未使用Adobe ID连接到Campaign的Campaign用户。

如果贵组织中的操作员正在使用其登录/密码（也称为）连接到Campaign客户端控制台。 会受到影响，您应该将这些运算符迁移到Adobe IMS，如下所述。

迁移到[AdobeIdentity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}是确保环境安全和标准化的安全要求，因为大多数其他Adobe Experience Cloud解决方案和应用程序已在IMS上。

此更改适用于从Campaign Classicv7.4.1（和最新的[IMS迁移兼容版本](ac-ims.md#ims-versions)）开始，并且是&#x200B;**强制性的**，必须将其移至Adobe Campaign v8。


## 如何迁移托管环境和Managed Services环境？ {#ims-migration-procedure}

### 先决条件 {#ims-migration-prerequisites}

在开始迁移过程之前，您必须联系Adobe过渡经理(适用于Managed Services客户)，或Adobe客户关怀（适用于其他托管客户），以便Adobe技术团队可以迁移现有操作员组和已命名权限，以AdobeIdentity Management System (IMS)。

### 关键步骤 {#ims-migration-steps}

下面列出了此迁移的关键步骤：

1. Adobe将您的环境升级到Campaign v7.4.1（或与[IMS迁移兼容的版本](ac-ims.md#ims-versions)）。
1. 升级后，您仍然可以使用这两种方法创建新用户，即作为本机用户或者使用IMS。
1. 您的内部Campaign管理员必须向Campaign客户端控制台上的所有本地用户添加唯一的电子邮件，并在完成后向您的Adobe代表/客户关怀部门确认。  此步骤在[此部分](#ims-migration-id)中有详细说明。
1. 与您的Adobe代表/客户关怀团队合作，确定Adobe运行非技术用户（操作员）和产品配置文件自动迁移的日期。 此步骤需要一个小时窗口，您的任何服务都不会出现停机。
1. 您的内部Campaign管理员会验证这些更改并提供注销。 进行此迁移后，不能再创建任何进一步的操作员使用其登录名和密码进行身份验证。

您还可以将技术操作员迁移到Adobe Developer Console，如[此技术说明](ims-migration.md)中所述。

完成此迁移后，请向您的Adobe过渡经理(适用于Managed Services用户)确认，或Adobe客户关怀（适用于托管客户）。 然后Adobe将迁移标记为完成。 然后，您的环境将得到保护和标准化。


## 如何迁移混合和内部部署环境？ {#ims-migration-procedure-on-prem}

下面列出了此迁移的关键步骤：

1. 将您的环境升级到Campaign v7.4.1（或与[IMS迁移兼容的版本](#ims-versions)）。
1. 升级后，您仍然可以使用这两种方法创建新用户，即作为本机用户或者使用IMS。
1. 您的内部Campaign管理员必须配置Adobe IMS，如[此部分](../../integrations/using/configuring-ims.md)中所述。
1. 然后，将唯一的电子邮件添加到Campaign客户端控制台上的所有本机用户。 此步骤在[此部分](#ims-migration-id)中有详细说明。
1. 在Adobe Admin Console中创建用户和产品配置文件，如[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=zh-Hans){target="_blank"}中所述。
1. 为所有操作员启用&#x200B;**与Adobe ID连接**&#x200B;选项。
1. 如[此页面](../../integrations/using/implementing-ims.md)中所述，为您的连接实施Adobe IMS。

您还可以将技术操作员迁移到Adobe Developer Console，如[此技术说明](ims-migration.md)中所述。


## 常见问题解答 {#ims-migration-faq}

### 如何在迁移后创建用户？ {#ims-migration-native}

Adobe建议在升级到Campaign Classic v7.4.1（或[IMS迁移兼容版本](#ims-versions)）后仅创建IMS用户。
从Campaign v7.4.1开始，您可以通过更新[此页面](impact-ims-migration.md)中详述的实例配置来阻止创建本机运算符。

作为Campaign管理员，您可以通过Adobe Admin Console和Campaign Client Console向组织用户授予权限。 用户使用其Adobe ID登录到Adobe Campaign。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hans){target="_blank"}以了解如何使用IMS设置权限。

### 如何为当前本机用户添加电子邮件？ {#ims-migration-id}

作为Campaign管理员，您必须从客户端控制台向所有本机用户添加电子邮件ID。 要执行此操作，请按照以下步骤进行：

1. 连接到客户端控制台并浏览到&#x200B;**管理>访问管理>运算符**。
1. 在运算符列表中选择要更新的运算符。
1. 在操作员表单的&#x200B;**联系方式**&#x200B;部分中输入操作员的电子邮件。
1. 保存您的更改。

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### 如何通过IMS登录Campaign？ {#ims-migration-log}

在[本节](../../integrations/using/implementing-ims.md)中了解如何使用您的Adobe ID连接到Campaign。

### 此迁移期间是否会发生停机？ {#ims-migration-downtime}

对于托管和Managed Services客户，要完成迁移（迁移用户和产品配置文件），Adobe需要一小时的时间，并且任何实例（工作流等）无需停机。

在此时间范围内，所有Campaign用户都需要注销，并在完成向IMS的迁移后使用其Adobe ID重新登录。

Adobe强烈建议在迁移时段注销所有用户。

### 我组织中的用户已在使用IMS，我仍然需要执行IMS迁移吗？{#ims-migration-needed}

此迁移包括两个方面：最终用户迁移（以及产品配置文件）和技术用户迁移（用于自定义代码中的API）。

如果所有用户（Campaign操作员）都在IMS上，则仍需要联系Adobe代表/客户支持以计划产品配置文件迁移。 您还需要迁移可能在自定义代码中使用的技术用户。 请参阅[此页面](ims-migration.md)以了解详情。

### 如何查看操作员的身份验证类型？

了解如何在Campaign中查看操作员的身份验证类型：

1. 从&#x200B;**资源管理器**，访问&#x200B;**管理** `>` **访问管理** `>` **运算符**。

1. 右键单击标题行并选择&#x200B;**配置列表**&#x200B;菜单。

   ![](assets/ims_2.png)

1. 将&#x200B;**禁用帐户**&#x200B;和&#x200B;**身份验证类型**&#x200B;添加为&#x200B;**输出列**。

   ![](assets/ims_1.png)

您现在可以看到您的&#x200B;**操作员**&#x200B;及其&#x200B;**身份验证类型**&#x200B;的列表。

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [将技术用户迁移到Adobe Developer控制台](ims-migration.md)
>* [Adobe Campaign Classic v7发行说明](../../rn/using/latest-release.md)
>* [什么是AdobeIdentity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}
