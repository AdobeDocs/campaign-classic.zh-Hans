---
product: campaign
title: 监视作业执行
description: 了解如何监视导入和导出作业的执行。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 55%

---

# 监测作业执行 {#monitoring-job-execution}

![](../../assets/common.svg)

您可以直接从导入/导出作业列表跟踪导入和导出作业的执行情况。

![](assets/s_ncs_user_export_list_and_details.png)

* 的 **[!UICONTROL Journal]** 选项卡，用于查看有关执行的日志消息。
* 的 **[!UICONTROL Rejects]** 选项卡包含被拒绝的记录。 请参阅[此小节](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error)。

在 **[!UICONTROL General]** 选项卡 **[!UICONTROL Status]** 字段指示作业的当前状态。

每个状态都由一个特殊的图标和标签表示。状态及其图标如下：

![](assets/s_ncs_user_export_status.png)

* **正在编辑**

   正在创建作业。

* **正在执行**

   此作业正在执行。

* **取消**

   单击 **[!UICONTROL Cancel]** 按钮：正在进行的作业被取消。

* **正在取消**

   取消命令已接收并且正在取消作业。

* **正在暂停**

   单击 **[!UICONTROL Pause]**:工作正在暂停。

* **已暂停**

   单击 **[!UICONTROL Pause]**:作业已挂起。 可以通过单击 **[!UICONTROL Start]**.

* **已完成**

   作业的执行已完成。

* **已完成且存在错误**

   由于技术错误，该作业未执行。

* **正在关闭服务器**

   正在进行的作业因 Adobe Campaign 服务器已关闭而中断。
