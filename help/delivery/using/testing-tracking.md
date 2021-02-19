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
1. 指定将接收电子邮件的用户。 由于此用户必须打开电子邮件并单击其包含的链接，请确保您选择了您控制的测试收件人地址。
1. 在电子邮件内容中添加镜像页面(MirrorPage)个性化块。
1. 发送包含指向投放的链接的镜像页面。
1. 收到电子邮件后，请打开它并单击镜像页面链接。
1. 将您正确重定向到镜像页面后，访问&#x200B;**管理>技术工作流**&#x200B;文件夹并打开&#x200B;**跟踪**&#x200B;工作流。
1. 开始工作流，右键单击&#x200B;**调度程序**&#x200B;活动，然后选择&#x200B;**立即执行挂起任务**。
1. 等待约30秒，然后选择&#x200B;**审核**&#x200B;选项卡。 确保至少找到一个跟踪日志记录。

   如果未看到任何新日志，请单击&#x200B;**刷新**。

1. 转至用于测试的收件人的用户档案页，然后选择&#x200B;**跟踪**&#x200B;选项卡。 某些记录应当在&#x200B;**Type**&#x200B;列中以&#x200B;**镜像页面**&#x200B;值显示。

   >[!NOTE]
   >
   >默认情况下，收件人的用户档案页位于&#x200B;**用户档案和目标>收件人**&#x200B;文件夹中。

   要检查电子邮件日志跟踪，请在&#x200B;**Type**&#x200B;列中查找&#x200B;**Open**&#x200B;和&#x200B;**[!UICONTROL Email click]**&#x200B;值。

   如果未显示打开的日志，请转到投放并访问其&#x200B;**属性**，以确保选中&#x200B;**激活跟踪**&#x200B;和&#x200B;**[!UICONTROL Opens tracking]**&#x200B;选项。

