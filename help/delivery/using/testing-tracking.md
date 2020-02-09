---
title: 测试跟踪
seo-title: 测试跟踪
description: 测试跟踪
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 测试跟踪{#testing-tracking}

您可以测试对镜像页面、电子邮件日志和链接的跟踪。 操作步骤：

1. 创建用于测试的新电子邮件分发。
1. 指定将接收电子邮件的用户。 由于此用户必须打开电子邮件并单击其包含的链接，请确保您选择您控制的测试收件人地址。
1. 在电子邮件内容中添加镜像页面(MirrorPage)个性化块。
1. 发送包含指向镜像页面的链接的分发。
1. 收到电子邮件后，请打开该电子邮件，然后单击镜像页面链接。
1. 将您正确重定向到镜像页面后，访问“管理” **>“技术工作流程** ”文件夹并打开“跟 **踪** ”工作流。
1. 启动工作流，右键单击“调度程序 **”活动** ，然后选择“ **立即执行暂挂任务”**。
1. 等待约30秒，然后选择“审 **核** ”选项卡。 确保至少找到一个跟踪日志记录。

   如果 **未看到任何新日志** ，请单击“刷新”。

1. 转到用于测试的收件人的配置文件页面，然后选择“跟 **踪** ”选项卡。 某些记录应当在“类 **型** ”列中显示 **“镜像页面”值** 。

   >[!NOTE]
   >
   >默认情况下，收件人的配置文件页面位于“配置文件 **和目标”>“收件人** ”文件夹中。

   要检查电子邮件日志跟踪，请在“类型”列中 **查找****[!UICONTROL Email click]** “打 **开”值** 。

   如果未显示打开的日志，请转到交付并访问其 **属性** ，以确保同时选中 **激活跟踪****[!UICONTROL Opens tracking]** 和选项。

