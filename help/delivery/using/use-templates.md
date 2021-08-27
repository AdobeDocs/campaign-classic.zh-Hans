---
product: campaign
title: 使用投放模板
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# 使用模板 {#use-templates}

![](../../assets/common.svg)

交付模板为大多数常见类型的活动提供现成方案，从而提高效率。 借助模板，营销人员可以在较短的时间内以最少的自定义时间部署新营销活动。

在[此部分](creating-a-delivery-template.md)中了解有关投放模板的更多信息。

## 投放模板快速入门 {#gs-templates}

使用[投放模板](creating-a-delivery-template.md)，您只需定义一组符合您需求且可重复用于将来投放的技术和功能属性即可。 然后，您可以节省时间并在需要时标准化投放。

在Adobe Campaign中管理多个品牌时，Adobe建议每个品牌具有一个子域。 例如，银行可以具有与其每个区域机构对应的多个子域。 如果银行拥有bluebank.com域，则其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每个子域有一个投放模板可让您始终为每个品牌使用正确的预配置参数，从而避免出现错误并节省您的时间。

**提示**:为避免出现配置错误，我们建议您复制本机模板并更改其属性，而不是创建新模板。

## 配置地址

* 发件人的地址是允许发送电子邮件的必填地址。

* 某些ISP（互联网服务提供商）在接受邮件前检查发件人地址的有效性。

* 地址格式不正确可能导致接收服务器拒绝该地址。 您必须确保提供正确的地址。

* 地址必须明确标识发件人。 域必须由发件人拥有并注册。

* Adobe建议创建与为投放和回复指定的地址对应的电子邮件帐户。 请咨询消息系统管理员。

要在Campaign界面中配置地址，请执行以下步骤：

1. 在[投放模板](creating-a-delivery-template.md)中，单击&#x200B;**[!UICONTROL From]**&#x200B;链接。 在&#x200B;**[!UICONTROL Email header parameters]**&#x200B;窗口中，填写以下字段：

   ![](assets/d_best_practices_email_header.png)

1. 在&#x200B;**[!UICONTROL Sender address]**&#x200B;字段中，确保地址域与您委派给Adobe的子域相同。 可以更改“@”之前的部分，但不能更改域地址。

1. 在&#x200B;**[!UICONTROL From]**&#x200B;字段中，使用收件人可轻松识别的名称（如品牌名称）来提高投放的开场率。 要进一步改善收件人的体验，您可以添加人员姓名，例如“Emma from Megastore”。

1. 在&#x200B;**[!UICONTROL Reply address text]**&#x200B;字段中，默认使用发件人地址进行回复。 但是，Adobe建议使用现有的实际地址，如您品牌的客户关怀。 在这种情况下，如果收件人发送了回复，客户关怀团队将能够处理该回复。

### 设置控制组

发送投放后，您可以将被排除的收件人的行为与收到投放的收件人进行比较。 然后，您可以衡量营销活动的效率。 了解有关控制组[此部分](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)的更多信息。

要设置控制组，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接。 在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Control group]**&#x200B;选项卡。 您可以提取目标的一部分，例如5%的随机样本。

![](assets/d_best_practices_control_group.png)

## 使用分类来应用过滤器或控制规则

分类包含在发送任何消息之前在分析阶段应用的检查规则。

在模板属性的&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡中，根据需要更改默认分类。

例如，为了更好地控制出站流量，您可以通过定义每个子域的一个亲和度并为每个亲和度创建一个分类来定义可以使用的IP地址。 相关性在实例的配置文件中定义。 联系您的Adobe Campaign管理员。

有关分类的更多信息，请参阅[此部分](../../campaign-opt/using/about-campaign-typologies.md)。
