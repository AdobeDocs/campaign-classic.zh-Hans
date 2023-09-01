---
product: campaign
title: 跟踪入门
description: 了解更多Adobe Campaign中跟踪的一般准则
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 10%

---

# 消息跟踪入门 {#get-started-tracking}



借助其跟踪功能，Adobe Campaign使您能够跟踪发送的消息并检查收件人的行为：打开、单击链接、退订等。

此信息可在 **[!UICONTROL Tracking]** 每个投放收件人用户档案的选项卡。 此选项卡显示从列表中选择的收件人跟踪和点击的所有URL链接。 这是投放中跟踪的仍存在于投放屏幕中的所有URL的累积。 该列表可以配置，通常包含：点击的URL、点击的日期和时间以及在其中找到URL的文档。 如需详细信息，请参阅[此部分](../../platform/using/editing-a-profile.md#tracking-tab)。

此 **投放仪表板** 对于监控投放以及在发送消息期间遇到的最终问题也很关键。 有关详细信息，请参阅 [本节](delivery-dashboard.md).

下图显示了用户与各种服务器之间的对话阶段。

![](assets/tracking-diagram.png)

## 配置跟踪 {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**工作原理**

在使用跟踪之前，您需要先为实例配置它。 [了解详情](../../installation/using/deploying-an-instance.md#operating-principle)

**跟踪服务器**

要配置跟踪，必须声明您的实例并在跟踪服务器中注册。 [了解详情](../../installation/using/deploying-an-instance.md#tracking-server)

**正在保存跟踪**

配置跟踪并填充URL后，必须注册跟踪服务器。 [了解详情](../../installation/using/deploying-an-instance.md#saving-tracking)

## 消息跟踪 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**跟踪的链接**

您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击，以便更好地了解收件人的行为。 [了解详情](how-to-configure-tracked-links.md)

**URL跟踪**

可通过激活或停用跟踪的URL来配置跟踪选项。 [了解详情](personalizing-url-tracking.md)

**跟踪的链接个性化**

Campaign Classic跟踪功能允许您在电子邮件中添加可个性化并支持跟踪的链接。 [了解详情](tracking-personalized-links.md)

**跟踪日志**

在发送投放并激活跟踪后，跟踪技术工作流会检索跟踪数据。 此数据可在投放的“跟踪”选项卡中找到。 [了解详情](accessing-the-tracking-logs.md)

**测试跟踪**

在将消息与跟踪一起发送之前，您可以在镜像页面、电子邮件日志和链接上测试跟踪。 [了解详情](testing-tracking.md)

## Web应用程序跟踪 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**跟踪 Web 应用程序**

您还可以跟踪和测量带有跟踪标记的Web应用程序页面上的访问次数。 此功能可用于所有Web应用程序类型，例如表单和登陆页面。 [了解详情](../../web/using/tracking-a-web-application.md)

**选择退出 Web 应用程序跟踪**

通过选择退出Web应用程序跟踪，您可以停止跟踪选择退出行为跟踪的最终用户的Web行为。 您可以包括在Web应用程序或登陆页中显示横幅的功能，以允许用户选择退出。 [了解详情](../../web/using/web-application-tracking-opt-out.md)

## 跟踪报表 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**跟踪统计信息**

此报表提供了有关打开、点击和交易的统计数据，并允许您跟踪投放对营销的影响。 [了解详情](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 和点击流**

此报表显示投放后访问的页面列表。 [了解详情](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**人员和收件人**

通过此示例，更好地了解Adobe Campaign中个人/人员与收件人之间的跟踪差异。 [了解详情](../../reporting/using/person-people-recipients.md)

**跟踪指标**

此报表将组合关键指标，用于跟踪接收投放时的收件人行为，例如打开次数、点进率和点击流。 [了解详情](../../reporting/using/delivery-reports.md#tracking-indicators)

**指标计算**

不同的表格会根据投放类型为您提供不同报告中使用的指标列表及其计算公式。 [了解详情](../../reporting/using/indicator-calculation.md)

## 跟踪故障排除 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

以下故障排除提示将帮助您解决在Adobe Campaign Classic中使用跟踪时最常见的问题。 有关更高级的疑难解答，请参阅 [本节](tracking-troubleshooting.md).

* 检查trackinglogd进程是否正在运行

  此进程从IIS/Web服务器共享内存中读取并写入重定向日志。

  您可以通过选择实例中的监视选项卡，从主页访问它。 您还可以在实例上执行以下命令： `<user>@<instance>:~$ nlserver pdump`

  如果trackinglogd进程未出现在列表中，请在实例上使用以下命令启动它： `<user>@<instance>:~$ nlserver start trackinglogd`

* 检查跟踪技术工作流最近是否正在运行。

  您可以在文件夹“管理” > “生产” > “技术工作流”中找到“跟踪”技术工作流。
