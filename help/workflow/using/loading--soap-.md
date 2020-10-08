---
title: 加载 (SOAP)
seo-title: 加载 (SOAP)
description: 加载 (SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 5%

---


# 加载 (SOAP){#loading-soap}

>[!CAUTION]
>
>仅 **当您安装了活动** (联合数据访问)模块时， **加载(SOAP** )联合数据访问才可用。 请核实您的许可协议。

当无 **法通过外部数据** 库中的活动直接收集数据时，除了数据加载(RDBMS) **** 活动外，还使用加载(SOAP)联合数据访问。

操作如下：

1. 选择使用XML示例或WSDL。

   以下示例来自消息中心模块的技术工作流。

   ![](assets/load_soap_002.png)

1. 对于XML示例，请选择一个示例文件。 分析该文件以建立一个结果示例。

   对于WSDL，输入匹配的访问URL，然后生成骨骼代码。 所选的服务和呼叫将自动更新和显示。

   ![](assets/soap_load_003.png)

1. 选择 **[!UICONTROL Click here to view and edit analysis results]** 以指定每个标识的列。

   ![](assets/soap_load_001.png)

   如果要更新示例，请选择 **[!UICONTROL Re-analyze the example]**。

   您还可以通过链接个性化列数据 **[!UICONTROL Advanced parameters]** 格式。 有关格式化导入数据的详细信息，请参 [阅此部分](../../platform/using/importing-data.md#import-wizard)。

1. 您可以使用行号作为标识符和／或指定SOAP调用返回多个元素。
1. 根据选项卡脚本的函数输入以下选项卡脚本：

   * **[!UICONTROL Initialization]**:建立SOAP连接。
   * **[!UICONTROL Iteration]**:执行对SOAP服务的调用。 此函数的返回必须是与示例或WSDL的描述兼容的XML对象。

      Adobe Campaign将在循环中调用此选项卡的代码，直到返回空XML对象。

   * **[!UICONTROL Finalization]**:关闭连接和／或释放处理过程中创建的其他资源。

