---
solution: Campaign Classic
product: campaign
title: 测试跟踪
description: 测试跟踪
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---


# 测试跟踪{#testing-tracking}

您可以测试镜像页面、电子邮件日志和链接的跟踪。 操作步骤：

1. 创建用于测试的新电子邮件投放。
1. 指定将接收电子邮件的用户。 由于此用户必须打开电子邮件并单击其包含的链接，请确保您选择您控制的测试收件人地址。
1. 在电子邮件内容中添加镜像页面(MirrorPage)个性化块。
1. 发送包含指向投放的链接的镜像页面。
1. 收到电子邮件后，请打开该电子邮件并单击镜像页面链接。
1. 将您正确重定向到镜像页面后，访问“管 **理”>“技术工作流** ”文件夹并打 **开“跟踪** ”工作流。
1. 开始工作流，右键单击 **调度程序** 活动，然 **后选择立即执行挂起任务**。
1. 等待约30秒，然后选择“审 **核** ”选项卡。 确保至少找到一个跟踪日志记录。

   如果 **未看到** 任何新日志，请单击“刷新”。

1. 转到用于测试的用户档案的收件人页，然后选择“跟踪 **”** 选项卡。 某些记录应当在“类 **型** ”列中 **显示** 镜像页面值。

   >[!NOTE]
   >
   >默认情况下，收件人的用户档案页 **位于用户档案和目标** >收件人文件夹中。

   要检查电子邮件日志跟踪，请在“类型 **”列中****[!UICONTROL Email click]** 查找“ **打开** ”值。

   如果未显示打开的日志，请转到投放并访问其 **属性** ，以确保同时选中 **激活跟踪** 和 **[!UICONTROL Opens tracking]** 选项。

