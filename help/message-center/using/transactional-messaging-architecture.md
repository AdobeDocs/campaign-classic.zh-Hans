---
title: Adobe Campaign Classic交易消息架构
description: 本节介绍Adobe Campaign Classic事务消息传递架构。
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# 交易消息架构{#transactional-messaging-architecture}

## 关于执行和控制实例 {#about-execution-and-control-instances}

在Adobe Campaign中，交易消息传递功能（也称为消息中心）设计为支持可伸缩性并提供全天候服务。 它由几个实例组成：

* 一个控件实例，消息模板是在其中创建的，
* 接收事件和传送消息的一个或多个执行实例。

要使用这些功能，Adobe Campaign用户登录到控件实例以创建事务性消息模板，使用种子列表生成消息预览，显示报告并监视执行实例。

执行实例接收事件，将其链接到事务消息模板，并向每个收件人发送个性化消息。

![](assets/messagecenter_diagram.png)

## 支持多个控件实例 {#supporting-several-control-instances}

>[!CAUTION]
>
>仅内部部署环境支持与多个控制实例共享执行群集。

可以在多个控制实例之间共享执行群集。 例如，如果您管理多个专用商店，则可以为每个品牌配置一个控制实例并将它们全部链接到同一个执行群集。

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>有关必要配置的详细信息，请参阅 [使用多个控件实例](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances)。

## 安装实例 {#installing-instances}

安装Transactional消息包时需要采取几种预防措施。 Adobe建议您在投入生产之前在测试环境中工作。 您还需要拥有兼容的Adobe Campaign许可证。 有关详细信息，请与您的Adobe客户经理联系。

>[!CAUTION]
>
>控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一营销活动实例。

如果需要使用多个渠道，则必须在安装Transactional消息包之前安装和配置相关包。 请参阅 [添加交付渠道](#adding-a-delivery-channel)。

* 要在计算机上安装控件实例，请选择该 **[!UICONTROL Transactional message control]** 模块。

   ![](assets/messagecenter_install_controlinstance_001.png)

* 要在计算机上安装执行实例，请选择该 **[!UICONTROL Transactional message execution]** 模块。

   ![](assets/messagecenter_install_executioninstance_001.png)

## 添加交付渠道 {#adding-a-delivery-channel}

添加交付渠道（移动渠道、移动应用渠道等）必须在安装Transactional消息包之前执行。 如果您已在电子邮件渠道上启动了交易消息传递项目，然后在项目过程中决定添加新渠道，则必须执行以下步骤：

1. 使用包导入向导( ******[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** )安装所需的渠道，例如移动渠道。
1. 执行文件导入( **[!UICONTROL Tools > Advanced > Import package... > File]** )，然后选择 ****`[Your language]`**datakitnmspackagemessageCenter.xml文件** 。
1. 在中， **[!UICONTROL XML content of the data to import]** 仅保留与添加的渠道对应的分发模板。 例如，如果已添加 **Mobile Channel**，则只保留与(smsTriggerMessage)对应的 **entities****[!UICONTROL Mobile transactional message]** 元素。 如果已添加移动应 **用程序渠道**，则仅保留 **iOS事务消息** (iosTriggerMessage)和 **Android事务消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

## 交易消息和入站交互 {#transactional-messages-and-inbound-interaction}

与“入站交互”模块结合使用时，交易消息传递允许您将专用于收件人的营销优惠插入消息中。

>[!NOTE]
>
>“交互”模块在“交互”中有 [详细说明](../../interaction/using/interaction-and-offer-management.md)。

要将交易消息传递与交互结合使用，您需要应用以下配置：

* 将 **Interaction** 包安装到控件实例上并配置选件目录。

   >[!CAUTION]
   >
   >请勿将选件复制到执行实例中。

* 活动必须包含链接到收件人的标识符，才能个性化选件。 @externalId **** 属性必须包含此标识符的值。 **交互** ，默认情况下配置为标识主键的收件人：

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
   ```

   您可以配 **置Interaction** ，以便在您选择的字段中进行标识，例如在电子邮件地址上：

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
   ```

以电子邮件营销活动的方式创建交付模板：

* 将选件添加到您的交易消息模板。
* 检查预览，发送证明并发布模板。

您还必须在选件空间上启用酉模式。 如需详细信息，请参阅[此部分](../../interaction/using/creating-offer-spaces.md)。

## 交易消息和推送通知 {#transactional-messaging-and-push-notifications}

与移动App渠道模块结合使用时，交易消息传递使您能够通过移动设备上的通知推送交易消息。

>[!NOTE]
>
>此部分详细介绍了移动应用 [程序渠道](../../delivery/using/about-mobile-app-channel.md)。

要将事务消息模块与移动应用程序渠道结合使用，您需要应用以下配置：

1. 将Mobile App **** Channel包安装到控件和执行实例上。
1. 复制 **Mobile应用程序类型** Adobe Campaign服务以及它在执行实例中包含的移动应用程序。

该事件必须包含以下元素：

* 移动设备ID(Android的&#x200B;**registrationId** ,iOS的 **deviceToken** )。 此ID表示通知将发送到的“地址”。
* 指向移动应用程序或集成密钥(**uuid**)的链接，用于恢复特定于应用程序的连接信息。
* 将通知发送到的渠道(**whistedChannel**):41适用于iOS,42适用于Android
* 所有对个性化有用的数据

以下是包含此信息的事件的示例：

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>消息模板的创建将保持不变。

## 交易消息和LINE {#transactional-messaging-and-line}

与LINE Channel相结合，交易消息允许您在安装在消费性移动设备上的LINE应用程序上发送实时消息。 这用于在LINE用户添加品牌页面时发送欢迎消息。

要将交易消息模块与LINE一起使用，在您的营销实例和执行实例上进行配置时 **需要** 以下 **元素** :

* 在两个 **[!UICONTROL LINE Connect]** 实例上安装包。
* 在您的 **[!UICONTROL Transactional message control]** 营销实例上安装包，在执行 **[!UICONTROL Transactional message execution]** 实例上安装包。
* 在两个实 **例上创建LINE外部帐户****** 和服务，其命名与要同步的相同。 有关如何创建LINE外部帐户和服务的详细信息，请参阅本 [页](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-)。

然后，从 **[!UICONTROL Explorer]** 、中 **[!UICONTROL Platform]** > **[!UICONTROL External account]** ，您需要在两个实例上配置不同的外部帐户：

1. 使用以 **[!UICONTROL External database]** 下配置在执行 **实例中** ，创建外部帐户：

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根据需要命名外部帐户。
   * **[!UICONTROL Type]** :选择 **[!UICONTROL External database]** 。
   * **[!UICONTROL Enabled]** 框中。
   从类 **[!UICONTROL Connection]** 别：

   * **[!UICONTROL Type]** :选择数据库服务器，例如PostgresSQL。
   * **[!UICONTROL Server]** :输入数据库服务器URL。
   * **[!UICONTROL Account]** :输入您的数据库帐户。

      >[!NOTE]
      >
      >数据库用户需要对以下表具有读取权限才能进行FDA连接：XtkOption、NmsVisitor、NmsVisitorSub、NmsService、NmsBroadLogRtEvent、NmsBroadLogBatchEvent、NmsTrackingLogRtEvent、NmsTrackingLogBatchEvent、NmsRtEvent、NmsEntEventBatchEvent、NmsBroadLogMsg、NmsTrackingUrl、NmsDelivery、NmsWebTrackingLogXtkFolder。

   * **[!UICONTROL Password]** :输入数据库帐户的口令。
   * **[!UICONTROL Database]** :输入执行实例的数据库名称。
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** 框中。


1. 使用以下 **[!UICONTROL External Database]** 配置在您的 **营销实例** 中创建帐户。

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根据需要命名外部帐户。
   * **[!UICONTROL Type]** :选择 **[!UICONTROL External database]** 。
   * 必须选中“已启用”框。
   从类 **[!UICONTROL Connection]** 别：

   * **[!UICONTROL Type]** :选择 **[!UICONTROL HTTP relay to remote Database]** 。
   * **[!UICONTROL Server]** :输入执行实例的系列活动的服务器URL。
   * **[!UICONTROL Account]** :输入用于访问执行实例的帐户。
   * **[!UICONTROL Password]** :输入用于访问执行实例的帐户的口令。
   * **[!UICONTROL Data Source]** :输入以下语法 **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** 。


1. 使用以 **[!UICONTROL Execution instance]** 下配置在您的 **营销实例中创建外部帐户** ，以创建数据同步工作流：

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根据需要命名外部帐户。
   * **[!UICONTROL Type]** :选择 **[!UICONTROL Execution instance]** 。
   * 必须选中“已启用”框。
   从类 **[!UICONTROL Connection]** 别：

   * **[!UICONTROL URL]** :输入执行实例的URL。
   * **[!UICONTROL Account]** :输入用于访问执行实例的帐户。
   * **[!UICONTROL Password]** :输入用于访问执行实例的帐户的口令。
   从类 **[!UICONTROL Account connection method]** 别：

   * **[!UICONTROL Method]** :选择 **[!UICONTROL Federated Data Access (FDA)]** 。
   * **[!UICONTROL FDA account]** :从下拉菜单中选择您的FDA帐户。
   * Click the **[!UICONTROL Create the archiving workflow]** button.
   * 单击按 **[!UICONTROL Create data synchronization workflow]** 钮以创建LINE数据同步工作流。



1. 您现在可以开始创建交易消息。 For more on this, refer to this [page](../../message-center/using/introduction.md).
