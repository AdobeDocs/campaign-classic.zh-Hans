---
product: campaign
title: 跟踪入门
description: 进一步了解有关在Adobe Campaign Classic中跟踪的一般准则
feature: Monitoring, Email
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 9%

---

# 消息跟踪入门 {#get-started-tracking}

![](../../assets/common.svg)

凭借其跟踪功能，Adobe Campaign使您能够跟踪发送的消息并检查收件人的行为：打开、点击链接、退订等。

此信息可在 **[!UICONTROL Tracking]** 选项卡。 此选项卡显示从列表中选择的收件人所跟踪和点击的所有URL链接。 这是投放屏幕中仍存在的投放中跟踪的所有URL的累积。 该列表可进行配置，通常包含：点击的URL、点击的日期和时间以及找到URL的文档。 如需详细信息，请参阅[此部分](../../platform/using/editing-a-profile.md#tracking-tab)。

的 **投放仪表板** 也是监控投放情况以及在发送消息过程中遇到的最终问题的关键。 有关更多信息，请参阅 [此部分](delivery-dashboard.md).

下图显示了用户与各种服务器之间对话的各个阶段。

![](assets/tracking-diagram.png)

## 配置跟踪 {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**工作原理**

在使用跟踪之前，您需要先为实例配置它。 [了解详情](../../installation/using/deploying-an-instance.md#operating-principle)

**跟踪服务器**

要配置跟踪，必须向跟踪服务器声明并注册您的实例。 [了解详情](../../installation/using/deploying-an-instance.md#tracking-server)

**保存跟踪**

配置跟踪并填充URL后，必须注册跟踪服务器。 [了解详情](../../installation/using/deploying-an-instance.md#saving-tracking)

## 消息跟踪 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**跟踪的链接**

您可以跟踪消息的接收情况以及消息内容中插入的链接的激活情况，以便更好地了解收件人的行为。 [了解详情](how-to-configure-tracked-links.md)

**URL跟踪**

可以通过激活或取消激活跟踪的URL来配置跟踪选项。 [了解详情](personalizing-url-tracking.md)

**跟踪的链接个性化**

Campaign Classic跟踪功能允许您在电子邮件中添加可进行个性化且支持跟踪的链接。 [了解详情](tracking-personalized-links.md)

**跟踪日志**

发送投放并激活跟踪后，跟踪技术工作流会检索跟踪数据。 此数据可在投放的跟踪选项卡中找到。 [了解详情](accessing-the-tracking-logs.md)

**测试跟踪**

在发送包含跟踪的消息之前，您可以在镜像页面、电子邮件日志和链接上测试跟踪。 [了解详情](testing-tracking.md)

## Web应用程序跟踪 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**跟踪 Web 应用程序**

您还可以使用跟踪标记来跟踪和测量Web应用程序页面上的访问量。 此功能可用于所有Web应用程序类型，如表单和登陆页面。 [了解详情](../../web/using/tracking-a-web-application.md)

**选择退出 Web 应用程序跟踪**

Web应用程序跟踪选择退出功能允许您停止跟踪选择退出行为跟踪的最终用户的Web行为。 您可以包括在Web应用程序或登陆页中显示横幅的功能，以允许用户选择退出。 [了解详情](../../web/using/web-application-tracking-opt-out.md)

## 跟踪报表 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**跟踪统计信息**

此报表提供打开数、点击数和交易统计信息，并允许您跟踪投放的营销影响。 [了解详情](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 和点击流**

此报表显示投放后访问的页面列表。 [了解详情](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**人员和收件人**

通过此示例，更好地了解Adobe Campaign中的人员和收件人之间的跟踪差异。 [了解详情](../../reporting/using/person-people-recipients.md)

**跟踪指标**

此报表整合了用于在收到投放时跟踪收件人行为的关键指标，如打开率、点进率和点击流。 [了解详情](../../reporting/using/delivery-reports.md#tracking-indicators)

**指标计算**

不同的表格提供了不同报表中使用的指标列表及其计算公式，具体取决于投放类型。 [了解详情](../../reporting/using/indicator-calculation.md)

## 跟踪故障排除 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

以下故障诊断提示将帮助您解决在Adobe Campaign Classic中使用跟踪时出现的最常见问题。 如需更高级的故障诊断，请参阅 [此部分](tracking-troubleshooting.md).

* 检查trackinglogd进程是否正在运行

   此过程从IIS/Web服务器共享内存中读取并写入重定向日志。

   您可以通过选择实例中的监视选项卡，从主页访问该页面。 您还可以对实例执行以下命令： `<user>@<instance>:~$ nlserver pdump`

   如果trackinglogd进程未显示在列表中，请在实例中使用以下命令启动该进程： `<user>@<instance>:~$ nlserver start trackinglogd`

* 检查跟踪技术工作流是否最近运行。

   您可以在文件夹管理>生产>技术工作流中找到跟踪技术工作流。
