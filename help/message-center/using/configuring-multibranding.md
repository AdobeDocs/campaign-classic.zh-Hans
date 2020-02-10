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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5eac80743d4cc82cdf55aa9287e8bb4fcc84356

---


# 配置多品牌{#configuring-multibranding}

本节介绍一个解决方案，用于为Adobe Campaign中的交易消息根据品牌配置跟踪和镜像页面URL。

## 先决条件 {#prerequisites}

* 必须将所有主机添加到实例(`config-<instance>.xml`)的配置文件。
* 必须为每个品牌分配一个子域。
* 如果对HTTPS页面进行Web跟踪，则必须拥有所有品牌的HTTPS证书。

## 典型过程 {#typical-process}

要配置多品牌，您需要配置执行实例和控制实例。 在执行实例中，请执行以下步骤：

1. 为每个品牌创建一个外部帐户。

   >[!NOTE]
   >
   >创建执行实例类型外部帐户显示在“控制实例 [”部分](../../message-center/using/creating-a-shared-connection.md#control-instance) 。

1. 扩展nms:extAccount架构以添加跟踪URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >扩展现有架构在扩展架构部 [分中介绍](../../configuration/using/extending-a-schema.md) 。

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

   with:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!CAUTION]
   >
   >这些更改在升级时可能会导致冲突。 您可能需要手动将这些公式与其新版本合并。

在控件实例上，您需要链接交付模板和外部帐户。 为此，您需要：

1. 使用与步骤1中定义的相同内部名称为每个品牌创建一个外部帐户。
1. 为每个品牌创建一个默认的交付模板。
1. 在交付模板的 **[!UICONTROL Properties]** 中，将路由设置为品牌的外部帐户。

