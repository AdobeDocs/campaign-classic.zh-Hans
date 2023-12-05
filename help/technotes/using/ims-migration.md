---
title: 将技术用户迁移到Adobe Developer控制台
description: 了解如何将Campaign技术操作员迁移到Adobe Developer控制台上的技术帐户
feature: Technote
role: Admin
source-git-commit: 68d1f5ae0089a0c447acf67c28c27f4e1069a218
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 0%

---

# 将Campaign技术操作员迁移到Adobe Developer控制台 {#migrate-tech-users-to-ims}

作为加强安全和身份验证流程工作的一部分，从Campaign Classicv7.3.5开始，对Campaign Classic的身份验证流程正在得到改进。 技术操作员现在应使用 [AdobeIdentity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe建议在Campaign v7.3.5中执行此迁移，以便能够顺利迁移到Campaign v8。**

技术操作员是为API集成明确创建的Campaign用户配置文件。 本文详细介绍了通过Adobe Developer控制台将技术操作员迁移到技术帐户所需的步骤。


## 您是否受影响？{#ims-impacts}

如果您从Campaign外部的系统向Campaign营销实例或实时消息中心实例进行API调用，Adobe强烈建议您通过Adobe Developer控制台将技术操作员迁移到技术帐户，如下所述。

此更改适用于Campaign Classicv7.3.5，并且 **必需** 以迁移到Adobe Campaign v8。

## 迁移过程 {#ims-migration-procedure}

按照以下步骤在Adobe Developer控制台中创建技术帐户，然后使用这些新创建的帐户能够更改在Adobe Campaign中进行API调用的所有外部系统的身份验证方法。

这些步骤概述如下：

* 在Adobe Developer控制台中创建项目
* 为新创建的项目分配相应的API
* 将所需的Campaign产品配置文件授予项目
* 更新API以使用新创建的技术帐户凭据
* 从Campaign实例中删除旧版技术运算符

### 迁移的先决条件{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Campaign托管客户和Managed Services客户

  对于进入消息中心实例的API调用，在升级到Campaign v7.3.5期间或配置实例期间应已创建产品配置文件。 此产品配置文件的名称为：

  `campaign - <your campaign instance> - messagecenter`

  如果您已使用基于IMS的身份验证来使用户访问Campaign，则Admin Console中应已存在API调用所需的产品配置文件。 如果您在Campaign中使用自定义运算符组来调用营销实例的API，则必须在Admin Console中创建该产品配置文件。

  对于其他情况，您必须联系Adobe过渡经理(适用于Managed Services用户)或Adobe客户关怀（适用于其他托管用户），以便Adobe技术团队能够将您现有的操作员组和已命名权限迁移到Admin Console中的产品配置文件。

* Campaign内部部署和混合型客户

  对于进入消息中心实例的API调用，您必须创建一个名为的产品配置文件：

  `campaign - <your campaign instance> - messagecenter`

  如果您已使用基于IMS的身份验证来使用户访问Campaign，则Admin Console中应已存在API调用所需的产品配置文件。 如果您在Campaign中使用自定义运算符组来调用营销实例的API，则必须在Admin Console中创建该产品配置文件。

  您可以在的Adobe控制台中了解有关产品配置文件的更多信息 [Adobe Developer控制台文档](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### 步骤1 — 在Adobe Developer控制台中创建Campaign项目 {#ims-migration-step-1}

集成是作为的一部分创建的 **项目** 在Adobe Developer控制台中。 了解有关中项目的更多信息 [Adobe Developer控制台文档](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

您可以使用之前创建的任何项目，也可以创建新项目。 有关创建项目的详细步骤，请参见 [Adobe Developer控制台文档](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. 您可以找到以下关键步骤

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

要创建新项目，请单击 **创建新项目** 从Adobe Developer Console的主屏幕。

![](assets/New-Project.png)

您可以使用 **编辑项目** 按钮以重命名此项目。


### 步骤2 — 将API添加到您的项目中 {#ims-migration-step-2}

从新创建的项目屏幕中，根据需要添加API，以便能够将此项目用作您对Adobe Campaign的API调用的技术帐户。

要将API添加到项目中，请执行以下步骤：

1. 单击 **添加API** 以选择要添加到项目中的API。
   ![](assets/do-not-translate/ims-updates-01.png)
1. 通过勾选Adobe Campaign卡片右上角的框，选择并将Adobe Campaign API添加到您的项目中，在将鼠标悬停在该卡片上时会显示该框
   ![](assets/do-not-translate/ims-updates-02.png)
1. 单击 **下一个** 在屏幕底部。

### 步骤3 — 选择身份验证类型  {#ims-migration-step-3}

在 **配置API** 屏幕中，选择所需的身份验证类型。 **OAuth服务器到服务器** 此项目需要身份验证。 确保选中并单击 **下一个** 在屏幕底部。

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### 第4步 — 选择产品配置文件 {#ims-migration-step-4}

如先决条件部分中所述，您必须分配项目使用的相应产品配置文件。 在此步骤中，您必须选择要由正在创建的技术帐户使用的产品配置文件。

如果此技术帐户用于对Message Center实例进行API调用，请确保选择以结尾的Adobe创建产品配置文件 `messagecenter`.

对于营销实例的API调用，请选择与实例和操作员组对应的产品配置文件。

选择所需的产品配置文件后，单击 **保存配置的API** 在屏幕底部。

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### 步骤5 — 将I/O管理API添加到您的项目中 {#ims-migration-step-5}


在项目屏幕中，单击 **[!UICONTROL + Add to Project]** 并选择 **[!UICONTROL API]** ，以便能够将I/O管理API添加到此项目中。

![](assets/do-not-translate/ims-updates-04.png)

在 **添加API** 屏幕，向下滚动以查找 **I/O管理API** 卡片。 单击将鼠标悬停在信息卡上时显示的复选框以将其选中。 然后单击 **下一个** 在屏幕底部。

![](assets/do-not-translate/ims-updates-05.png)


在 **配置API** 屏幕时，OAuth服务器到服务器身份验证已存在。 单击 **保存配置的API** 在屏幕底部。


![](assets/do-not-translate/ims-updates-06.png)

这会将您带回新创建项目的I/O管理API中的项目屏幕。 单击屏幕顶部的痕迹导航中的项目名称，可返回到项目详细信息主页。


### 步骤6 — 验证项目设置 {#ims-migration-step-6}

请查看您的项目，确保它类似于以下内容，带有 **I/O管理API** 和 **ADOBE CAMPAIGN API** 在“产品和服务”部分中显示并 **OAuth服务器到服务器** 在“凭据”部分中。

![](assets/do-not-translate/ims-updates-07.png)


### 步骤7 — 验证配置 {#ims-migration-step-7}

要尝试连接，请按照 [Adobe Developer Console凭据指南](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} ，用于生成访问令牌并复制提供的示例cURL命令。 您可以使用这些凭据创建soap调用，以测试您是否可以正确进行身份验证并连接到Adobe Campaign实例。 我们建议在对第三方API集成进行所有更改之前执行此验证。

### 步骤8 — 更新第三方API集成 {#ims-migration-step-8}

您现在必须更新对Adobe Campaign进行调用的API集成，才能使用新创建的技术帐户。

有关API集成步骤的更多详细信息（包括顺利集成的示例代码），请参阅 [Adobe Developer Console身份验证文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

以下是示例SOAP调用，其中显示第三方系统的迁移前调用和迁移后调用。

完成并验证迁移过程后，Soap调用将更新如下：



* 迁移前：不支持技术帐户访问令牌。

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* 迁移后：支持技术帐户访问令牌。 访问令牌应在中提供 `Authorization` 标头作为持有者令牌。 应在此处忽略会话令牌的使用，如以下soap调用示例中所示。

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### 步骤9 — （可选）在Campaign客户端控制台中更新技术帐户操作员 {#ims-migration-step-9}

此步骤是可选的，并且仅在营销实例中可用，不能在任何消息中心实例中使用。 如果已经为技术操作员定义了特定文件夹权限或已命名权限，但未通过分配的操作员组。 现在，您需要更新Admin Console中新创建的技术帐户用户，以授予所需的文件夹权限或命名权限。

请注意，在对Campaign实例至少进行API调用后（IMS届时将在Campaign中创建用户），技术帐户用户才会存在于Adobe Campaign中。 如果您在Campaign中找不到技术用户，请确保您能够按概述成功发送API调用 [步骤7](#ims-migration-step-7).

1. 要应用新的技术帐户用户所需的更改，请按照电子邮件地址在Campaign客户端控制台中找到它们。 此电子邮件地址是在上述项目创建和身份验证步骤中创建的。

   您可以通过单击 **OAuth服务器到服务器** 标题位于 **凭据** 部分。

   ![](assets/do-not-translate/ims-updates-07.png)

   在“凭据”屏幕中，向下滚动以找到**技术帐户电子邮件**，然后单击 **复制** 按钮。

   ![](assets/do-not-translate/ims-updates-08.png)

1. 现在，您需要在Adobe Campaign客户端控制台中更新新创建的技术运算符。 您必须将现有的技术操作员文件夹权限应用到新的技术操作员。

   要更新此运算符，请执行以下步骤：

   1. 在Campaign Client Console资源管理器中，浏览到 **管理>访问管理>运算符**.
   1. 访问用于API的现有技术操作员。
   1. 浏览到文件夹权限并检查权限。
   1. 将相同的权限应用到新创建的技术操作员。 该操作员的电子邮件是 **技术帐户电子邮件** 值之前已复制。
   1. 保存您的更改。


>[!CAUTION]
>
>新的技术操作员必须至少进行了一次要添加到Campaign客户端控制台的API调用。
>

### 步骤10 — 从Adobe Campaign中删除旧的技术运算符 {#ims-migration-step-10}

在迁移所有第三方系统以将新的技术帐户用于IMS身份验证后，您可以从Campaign客户端控制台中删除旧的技术操作员。

为此，请登录Campaign客户端控制台，导航至 **管理>访问管理>运算符** 并查找并删除旧的技术用户。
