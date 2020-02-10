---
title: 加载(SOAP)
seo-title: 加载(SOAP)
description: 加载(SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 加载(SOAP){#loading-soap}

>[!CAUTION]
>
>仅 **当您安装了FDA（联合数据访问）模块** ，才可以执行加载(SOAP) **活动** 。 请检查您的许可协议。

当无 **法通过外部数据库中的FDA直接收集数据时，除了数据加载(****** RDBMS)活动外，还使用加载(SOAP)活动。

操作如下：

1. 在使用XML示例或WSDL之间进行选择。

   以下示例来自“消息中心”模块的技术工作流。

   ![](assets/load_soap_002.png)

1. 对于XML示例，请选择示例文件。 分析该文件以建立一个结果示例。

   对于WSDL，输入匹配的访问URL，然后生成骨骼代码。 选定的服务和呼叫会自动更新并显示。

   ![](assets/soap_load_003.png)

1. 选择 **[!UICONTROL Click here to view and edit analysis results]** 以指定每个标识的列。

   ![](assets/soap_load_001.png)

   如果要更新示例，请选择 **[!UICONTROL Re-analyze the example]**。

   您还可以通过链接个性化列数据的 **[!UICONTROL Advanced parameters]** 格式。 有关格式化导入数据的详细信息，请参阅此 [部分](../../platform/using/importing-data.md#import-wizard)。

1. 您可以使用行号作为标识符和／或指定SOAP调用返回多个元素。
1. 根据选项卡脚本的函数输入以下选项卡脚本：

   * **[!UICONTROL Initialization]**:建立SOAP连接。
   * **[!UICONTROL Iteration]**:执行对SOAP服务的调用。 此函数的返回必须是与示例或WSDL的描述兼容的XML对象。

      Adobe Campaign将循环调用此选项卡的代码，直到返回空XML对象。

   * **[!UICONTROL Finalization]**:关闭连接和／或释放在处理过程中创建的其他资源。

