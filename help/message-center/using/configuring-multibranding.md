---
title: 配置多品牌
seo-title: 配置多品牌
description: 配置多品牌
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---


# 配置多品牌{#configuring-multibranding}

本节介绍一个解决方案，用于为Adobe Campaign中的事务性消息根据品牌配置跟踪和镜像页面URL。

## 先决条件{#prerequisites}

* 必须将所有主机添加到实例()的配置文`config-<instance>.xml`件中。
* 必须为每个品牌分配一个子域。
* 如果在HTTPS页面上进行Web跟踪，则必须为所有品牌提供HTTPS证书。

## 典型过程 {#typical-process}

要配置多品牌，您需要同时配置执行实例和控制实例。 在执行实例中，请按照以下步骤操作：

1. 为每个品牌创建一个外部帐户。

   >[!NOTE]
   >
   >创建执行实例类型外部帐户显示在 [控制实例](../../message-center/using/creating-a-shared-connection.md#control-instance) 部分。

1. 扩展nms:extAccount模式以添加跟踪URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >扩展现有模式在扩展 [模式部分中](../../configuration/using/extending-a-schema.md) 。

1. 修改nms:extAccount表单：

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 修改NmsTracking_OpenFormula和NmsTracking_ClickFormula选项以使用外部帐户而不是全局选项。

   为此，请替换：

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   与：

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >升级时，这些更改可能会导致冲突。 您可能需要手动将这些公式与其新版本合并。

在控制实例上，您需要链接投放模板和外部帐户。 为此，您需要：

1. 使用与步骤1中定义的相同内部名称，为每个品牌创建一个外部帐户。
1. 为每个品牌创建一个默认投放模板。
1. 在投放模板 **[!UICONTROL Properties]** 中，将路由设置为品牌的外部帐户。

