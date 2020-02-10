---
title: 在使用Adobe Campaign Classic时提高声誉
description: 了解有关在使用Adobe Campaign Classic时提高声誉的更多信息。
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 提高您的声誉{#improve-reputation}

为避免让收件人精疲力尽，请从目标中删除重复的电子邮件地址。 此步骤可保护您的发送信誉，并确保良好的隔离管理。 Adobe Campaign提供了实施这些建议的必要工具，并避免了被ISP列入黑名单的风险。

要尽可能避免重复，必须执行以下操作：

* 必须仔细配置导入
* 修改电子邮件地址时请注意
* 在自动导入过程中要注意
* 应将配置文件分类到不同的文件夹

隔离管理显示在本 [节中](../../delivery/using/understanding-quarantine-management.md)。

您将在下面找到有关复制和隔离管理的详细信息。

您可以按IP地址监视已发送的电子邮件量。 需要此架构扩展。 您需要扩展广播表以添加“公共标识符”，并创建一个工作流以提取和显示数据。 如果需要，请与Adobe联系。

## 重复项 {#duplicates}

拥有重复的电子邮件地址可能会产生多种后果：

* 同一消息已多次发送。 即使Campaign在发送之前默认执行重复数据消除过程，在拆分目标时，也无法阻止具有相同内容的不同操作发送相同的消息。
* 未接受取消订阅请求。 如果收件人在收到消息后取消订阅，则其重复的配置文件仍有资格获取将来的消息。

除了选择加入程序的这一侧，这种情况还可能导致用户将消息视为垃圾信息，并在ISP触发黑名单过程。

对数据库执行操作时必须特别谨慎：

* 必须仔细配置导入，特别是在选择协调密钥时。
* 更改后的电子邮件地址也可以是重复的源。 特别地，具有不同域的两个地址可以被路由到同一邮箱，例如，在某个公司已经更改名称并且已维护前一个域一段时间的情况下：joe.doe@amce-co.com和joe.doe@acme-rebranded.com。
* 自动导入是管理配置文件时要考虑的元素，无论是列表导入还是其他数据库导入。 当您删除或移动另一个分区中的配置文件时会发生什么情况？ 它可能通过自动导入在初始分区中重新创建，例如，下订单时。
* 可以使用视图而不是分区来实现将配置文件存储在不同文件夹中。 这样，您就可以确保配置文件位于同一物理分区中，同时仍然能够显示和管理足够的权限。

同样，在不同分区之间重复的情况也是正常的。 例如，当为第三方或不同的公司实体发送时，出于不同的原因，同一人成为收件人是合乎逻辑的。 但是，在同一分区内查找副本很少是正常的。

## 检疫 {#quarantines}

Adobe Campaign 管理了一个隔离地址列表。在传送分析过程中，默认情况下将排除其地址被隔离的收件人：他们没有目标。 例如，当收件箱已满或地址不存在时，可以隔离电子邮件地址。 在所有情况下，隔离均符合下面详述的特定规则。

隔离管理显示在本 [节中](../../delivery/using/understanding-quarantine-management.md)。