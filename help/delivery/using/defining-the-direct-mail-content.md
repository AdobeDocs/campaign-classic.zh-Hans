---
solution: Campaign Classic
product: campaign
title: 定义直邮内容
description: 定义直邮内容
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 9%

---


# 定义直邮内容{#defining-the-direct-mail-content}

## 提取文件 {#extraction-file}

包含提取数据的文件的名称在字段中定 **[!UICONTROL File]** 义。 通过字段右侧的按钮，您可以使用个性化字段创建文件名。

默认情况下，提取文件会创建并存储在服务器上。 可将其保存在计算机上。 为此，请检查 **[!UICONTROL Download the generated file after the analysis of the delivery]**。 在这种情况下，您需要指示本地存储目录的访问路径以及文件名。

![](assets/s_ncs_user_mail_delivery_local_file.png)

对于直邮投放,提取的内容在链接中定 **[!UICONTROL Edit the extraction file format...]** 义。

![](assets/s_ncs_user_mail_delivery_format_link.png)

此链接允许您访问提取向导并定义要导出到输出文件的信息（列）。

![](assets/s_ncs_user_mail_delivery_format_wz.png)

可以在提取文件中插入个性化URL。 For more on this, refer to [Web functionality](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>此向导包括导出向导的步骤，详见入 [门部分](../../platform/using/exporting-data.md#export-wizard) 。
