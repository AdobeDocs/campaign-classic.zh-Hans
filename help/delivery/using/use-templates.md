---
solution: Campaign Classic
product: campaign
title: 使用投放模板
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---


# 使用模板 {#use-templates}

投放模板为大多数常见类型的活动提供现成方案，从而提高效率。 借助模板，营销人员可以在更短的时间内以最少的自定义次数部署新活动。

了解有关[本节](../../delivery/using/creating-a-delivery-template.md)中投放模板的更多信息。

## 开始使用投放模板{#gs-templates}

[投放模板](../../delivery/using/creating-a-delivery-template.md)允许您定义一组技术和功能属性，这些属性符合您的需求，并且可以重用于将来的投放。 然后，您可以节省时间并在需要时标准化投放。

在Adobe Campaign中管理多个品牌时，Adobe建议每个品牌有一个子域。 例如，银行可以具有与其每个区域机构对应的多个子域。 如果银行拥有bluebank.com域，其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每个子域有一个投放模板使您始终可以为每个品牌使用正确的预配置参数，从而避免错误并节省您的时间。

**提示**:为避免在Campaign Standard中出现配置错误，建议您重复本机模板并更改其属性，而不要创建新模板。

## 配置地址

* 发送者的地址是允许发送电子邮件的必填地址。

* 某些ISP(Internet服务提供商)在接受消息前检查发送者地址的有效性。

* 格式不良的地址可能导致接收服务器拒绝它。 您必须确保提供了正确的地址。

* 地址必须明确标识发件人。 域必须由发送方拥有并注册。

* Adobe建议创建与为投放和回复指定的地址对应的电子邮件帐户。 请咨询消息系统管理员。

要在活动接口中配置地址，请执行以下步骤：

1. 在[投放模板](../../delivery/using/creating-a-delivery-template.md)中，单击&#x200B;**[!UICONTROL From]**&#x200B;链接。 在&#x200B;**[!UICONTROL Email header parameters]**&#x200B;窗口中，填写以下字段：

   ![](assets/d_best_practices_email_header.png)

1. 在&#x200B;**[!UICONTROL Sender address]**&#x200B;字段中，确保地址域与您委托给Adobe的子域相同。 可以更改“@”之前的部分，但不能更改域地址。

1. 在&#x200B;**[!UICONTROL From]**&#x200B;字段中，使用收件人可轻松识别的名称（如您的品牌名称）来提高投放的开业率。 要进一步改善收件人的体验，您可以添加人名，例如“Emma from Megastore”。

1. 在&#x200B;**[!UICONTROL Reply address text]**&#x200B;字段中，默认情况下，发件人地址用于回复。 但是，Adobe建议使用现有的真实地址，如您品牌的客户关怀。 在这种情况下，如果收件人发送回复，客户关怀团队将能够处理。

### 设置对照组

发送投放后，您可以将被排除收件人的行为与收到投放的收件人进行比较。 然后，您可以衡量活动的效率。 了解有关对照组[本节](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)的更多信息。

要设置对照组，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接。 在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Control group]**&#x200B;选项卡。 您可以提取目标的一部分，例如5%随机样本。

![](assets/d_best_practices_control_group.png)

## 使用类型应用过滤器或控制规则

排版包含在发送任何消息之前在分析阶段应用的检查规则。

在模板属性的&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡中，根据需要更改默认类型。

例如，为了更好地控制出站流量，您可以通过为每个子域定义一个关联，为每个关联创建一个类型来定义可以使用的IP地址。 关联在实例的配置文件中定义。 与您的Adobe Campaign管理员联系。

有关类型的详细信息，请参阅[本节](../../campaign/using/about-campaign-typologies.md)。
