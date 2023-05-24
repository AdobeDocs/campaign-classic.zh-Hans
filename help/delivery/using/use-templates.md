---
product: campaign
title: 使用投放模板
description: 使用投放模板
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 使用模板 {#use-templates}



通过为最常见类型的活动提供现成的方案，交付模板可以提高效率。 借助模板，营销人员可以在更短的时间内部署具有最小自定义的新营销活动。

要了解有关投放模板的更多信息，请参阅 [本节](creating-a-delivery-template.md).

## 投放模板入门 {#gs-templates}

A [投放模板](creating-a-delivery-template.md) 允许您定义一次可满足您需求且可重复用于未来投放的一组技术和功能属性。 然后，您可以节省时间并在需要时实现交付的标准化。

在Adobe Campaign中管理多个品牌时，Adobe建议每个品牌拥有一个子域。 例如，银行可以具有与其每个地区机构对应的多个子域。 如果银行拥有bluebank.com域，则其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每个子域拥有一个投放模板使您能够为每个品牌始终使用正确的预配置参数，从而避免错误并节省您的时间。

**笔尖**：为了避免配置错误，我们建议您复制本机模板并更改其属性，而不是创建新模板。

## 配置地址

* 发件人的地址是允许发送电子邮件的必填项。

* 有些ISP（Internet服务提供商）在接受消息之前会检查发件人地址的有效性。

* 格式错误的地址可能导致接收服务器拒绝该地址。 您必须确保提供正确的地址。

* 地址必须明确标识发件人。 域必须由发件人拥有并向其注册。

* Adobe建议创建对应于为投放和回复指定的地址的电子邮件帐户。 请与您的消息传递系统管理员联系。

要在Campaign界面中配置地址，请执行以下步骤：

1. 在 [投放模板](creating-a-delivery-template.md)，单击 **[!UICONTROL From]** 链接。 在 **[!UICONTROL Email header parameters]** 窗口中，填写以下字段：

   ![](assets/d_best_practices_email_header.png)

1. 在 **[!UICONTROL Sender address]** 字段中，确保地址域与您委派给Adobe的子域相同。 您可以更改“@”之前的部分，但不能更改域地址。

1. 在 **[!UICONTROL From]** 字段中，使用易于收件人识别的名称（如您的品牌名称）来提高投放的打开率。 为进一步改善收件人的体验，您可以添加一个人的姓名，例如“Emma from Megastore”。

1. 在 **[!UICONTROL Reply address text]** 字段中，默认情况下使用发件人地址进行回复。 但是，Adobe建议使用现有的真实地址，例如您品牌的客户关怀团队。 在这种情况下，如果收件人发送回复，客户关怀部门将能够处理。

### 设置控制组

发送投放后，您可以将排除的收件人的行为与接收投放的收件人的行为进行比较。 然后，您可以衡量营销活动的效率。 了解有关控制组的更多信息 [本节](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

要设置控制组，请单击 **[!UICONTROL To]** 链接。 在 **[!UICONTROL Select target]** 窗口中，选择 **[!UICONTROL Control group]** 选项卡。 您可以提取目标的一部分，例如5%的随机样本。

![](assets/d_best_practices_control_group.png)

## 使用类型应用过滤器或控制规则

分类包含在发送任何消息之前在分析阶段应用的检查规则。

在 **[!UICONTROL Typology]** 选项卡中，根据需要更改默认的分类。

例如，为了更好地控制出站流量，您可以通过定义每个子域一个关联并为每个关联创建一个类型来定义可以使用的IP地址。 相关性在实例的配置文件中定义。 联系Adobe Campaign管理员。

有关分类的详细信息，请参阅 [本节](../../campaign-opt/using/about-campaign-typologies.md).
