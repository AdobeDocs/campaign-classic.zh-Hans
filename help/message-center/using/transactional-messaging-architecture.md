---
title: Adobe Campaign经典事务消息传递体系结构
description: 本节介绍Adobe Campaign经典事务消息传递体系结构。
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
source-git-commit: e6f8eb6f4ffc3ffe9dbc643cf0edeef439c0f969
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# 交易消息架构{#transactional-messaging-architecture}

## 关于执行和控制实例 {#about-execution-and-control-instances}

在Adobe Campaign中，交易消息功能（也称为消息中心）设计为支持可伸缩性并提供全天候服务。 它由几个实例组成：

* 控制实例，消息模板是在其中创建的，
* 一个或多个执行实例接收事件并传送消息。

要使用这些功能，Adobe Campaign用户登录到控制实例以创建事务性消息模板，使用种子列表生成消息预览，显示报告并监视执行实例。

执行实例接收事件，将其链接到事务性消息模板，并向每位收件人发送个性化信息。

![](assets/messagecenter_diagram.png)

## 支持多个控制实例 {#supporting-several-control-instances}

>[!IMPORTANT]
>
>仅内部部署控制实例支持与多个环境共享执行群集。

可以在多个控制实例之间共享执行群集。 例如，如果您管理多个专用商店，则可以为每个品牌配置一个控制实例并将它们全部链接到同一个执行群集。

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>有关必要配置的详细信息，请参 [阅使用多个控制实例](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances)。

## 安装实例 {#installing-instances}

安装事务性消息包时，需要采取多种预防措施。 Adobe建议您在投入生产之前先在测试环境中工作。 您还需要具有兼容的Adobe Campaign许可证。 有关详细信息，请与您的Adobe客户经理联系。

>[!IMPORTANT]
>
>控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一活动实例。

如果您需要使用多个渠道，则必须在安装事务性消息包之前安装和配置相关包。 请参阅 [添加投放渠道](#adding-a-delivery-channel)。

* 要在计算机上安装控制实例，请选择 **[!UICONTROL Transactional message control]** 模块。

   ![](assets/messagecenter_install_controlinstance_001.png)

* 要在计算机上安装执行实例，请选择 **[!UICONTROL Transactional message execution]** 模块。

   ![](assets/messagecenter_install_executioninstance_001.png)

## 添加投放渠道 {#adding-a-delivery-channel}

添加投放渠道(移动渠道、移动应用渠道等) 必须先执行事务性消息包。 如果您已在电子邮件渠道上启动交易消息传递项目，则在项目过程中决定添加新渠道，则必须执行以下步骤：

1. 使用包渠道() **安装所需渠道**，例如移动导入向导 **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** 。
1. 执行文件导入( **[!UICONTROL Tools > Advanced > Import package... > File]** )，然后选 ****`[Your language]`**择datakitnmspackemessageCenter.xml文件** 。
1. 在中 **[!UICONTROL XML content of the data to import]** ，仅保留与添加的投放模板对应的渠道。 例如，如果已添加移 **动渠道**，则只保留与 **(smsTriggerMessage** )对应的 **[!UICONTROL Mobile transactional message]** 实体元素。 如果已添加“移 **动应用程序渠道**”，则仅保留 **iOS事务性消息** (iosTriggerMessage)和 **Android事务性消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

## 交易消息和推送通知 {#transactional-messaging-and-push-notifications}

结合移动应用渠道模块后，事务消息传递使您能够在移动设备上通过通知推送事务性消息。

>[!NOTE]
>
>移动应用程序渠道详 [细介绍](../../delivery/using/about-mobile-app-channel.md)。

要将事务性消息模块与移动应用程序渠道结合使用，您需要应用以下配置：

1. 将移动 **应用程序渠道** 包安装到控件和执行实例上。
1. 复制 **Mobile应用程序** 类型Adobe Campaign服务以及它包含在执行实例上的移动应用程序。

事件必须包含以下元素：

* 移动设备ID(**Android的** registrationId,iOS **的** deviceToken)。 此ID表示通知将发送到的“地址”。
* 指向移动应用程序或集成密钥(**uuid**)的链接，用于恢复特定于应用程序的连接信息。
* 将通知发送到的渠道(**whistedChannel**): 41适用于iOS,42适用于Android
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
>消息模板的创建保持不变。

## 交易消息和LINE {#transactional-messaging-and-line}

结合LINE渠道,事务性消息允许您在消费性移动设备中安装的LINE应用程序上发送实时消息。 这用于在LINE用户添加品牌页面时发送欢迎消息。

要将事务性消息模块与LINE结合使用，在您的营销实例和执行实例上进行 **配置** ，需要以 **下元素** :

* 在两个 **[!UICONTROL LINE Connect]** 实例上安装包。
* 在您的 **[!UICONTROL Transactional message control]** 营销实例上安装包，在执行实例 **[!UICONTROL Transactional message execution]** 上安装包。
* 在两个实 **例上****创建LINE** 外部帐户和服务，使其命名相同，以便同步。 有关如何创建LINE外部帐户和服务的详细信息，请参阅本 [页](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-)。

然后，从 **[!UICONTROL Explorer]** ，在 **[!UICONTROL Platform]** > **[!UICONTROL External account]** 中，您需要在两个实例上配置不同的外部帐户:

1. 使用以 **[!UICONTROL External database]** 下配置 **在执行** 实例中创建外部帐户:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 根据需要为您的外部帐户命名。
   * **[!UICONTROL Type]** : 选择 **[!UICONTROL External database]** 。
   * **[!UICONTROL Enabled]** 框中，选择“ 0 ”。
   从 **[!UICONTROL Connection]** 类别:

   * **[!UICONTROL Type]** : 选择数据库服务器，例如PostgresSQL。
   * **[!UICONTROL Server]** : 输入数据库服务器URL。
   * **[!UICONTROL Account]** : 输入您的数据库帐户。

      >[!NOTE]
      >
      >联合数据访问库用户需要对以下表具有读取权限才能进行连接： XtkOption、NmsVisitor、NmsVisitorSub、NmsService、NmsBroadLogRtEvent、NmsBroadLogBatchEvent、NmsTrackingLogRtEvent、NmsTrackingLogBatchEvent、NmsRtEvent、NmsBatchEvent、NmsBroadLogMsg、NmsTrackingUrl、NmsDelivery、NmsWebTrackingLogXtkFolder。

   * **[!UICONTROL Password]** : 输入数据库帐户的口令。
   * **[!UICONTROL Database]** : 输入执行实例的数据库名称。
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** 框中，选择“ 0 ”。


1. 使用以下 **[!UICONTROL External Database]** 配置在您 **的营销** 实例中创建帐户。

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 根据需要为您的外部帐户命名。
   * **[!UICONTROL Type]** : 选择 **[!UICONTROL External database]** 。
   * 必须选中“已启用”框。
   从 **[!UICONTROL Connection]** 类别:

   * **[!UICONTROL Type]** : 选择 **[!UICONTROL HTTP relay to remote Database]** 。
   * **[!UICONTROL Server]** : 输入活动的服务器URL。
   * **[!UICONTROL Account]** : 输入用于访问执行实例的帐户。
   * **[!UICONTROL Password]** : 输入用于访问执行实例的帐户的口令。
   * **[!UICONTROL Data Source]** : 输入以下语法 **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** 。


1. 使用以 **[!UICONTROL Execution instance]** 下配置在 **您的营销实例** 中创建外部帐户，以创建数据同步工作流：

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 根据需要为您的外部帐户命名。
   * **[!UICONTROL Type]** : 选择 **[!UICONTROL Execution instance]** 。
   * 必须选中“已启用”框。
   从 **[!UICONTROL Connection]** 类别:

   * **[!UICONTROL URL]** : 输入执行实例的URL。
   * **[!UICONTROL Account]** : 输入用于访问执行实例的帐户。
   * **[!UICONTROL Password]** : 输入用于访问执行实例的帐户的口令。
   从 **[!UICONTROL Account connection method]** 类别:

   * **[!UICONTROL Method]** : 选择 **[!UICONTROL Federated Data Access (FDA)]** 。
   * **[!UICONTROL FDA account]** : 从下拉列表中选择您的联合数据访问帐户。
   * 单击&#x200B;**[!UICONTROL Create the archiving workflow]**&#x200B;按钮。
   * 单击按 **[!UICONTROL Create data synchronization workflow]** 钮以创建LINE数据同步工作流。



1. 您现在可以开始创建事务性消息。 For more on this, refer to this [page](../../message-center/using/introduction.md).
