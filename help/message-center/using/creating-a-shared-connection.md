---
title: 创建共享连接
seo-title: 创建共享连接
description: 创建共享连接
seo-description: null
page-status-flag: never-activated
uuid: 30d6d23b-72c6-4454-8d6b-a10102f89262
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 7f471ac1-cd6a-4371-977e-52d60ce8d968
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65043155ab6ff1fe556283991777964bb43c57ce

---


# 创建共享连接{#creating-a-shared-connection}

>[!CAUTION]
>
>* 对消息中心在控制或执行实例上使用的架构进行的架构扩展 [](../../message-center/using/technical-workflows.md) ，需要在Adobe Campaign事务消息传递模块使用的其他实例上重复执行。
>* 控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一营销活动实例。
>



## 控制实例 {#control-instance}

如果您有分解架构，则需要指定与控件实例链接的执行实例并连接它们。 事务消息模板被部署到执行实例。 通过配置外部帐户类型，可以创建控件实例与执行实例之 **[!UICONTROL Execution instance]** 间的连接。 您需要创建与执行实例相同数量的外部帐户。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符进行划分。 有关详细信息，请参阅使 [用多个控件实例](#using-several-control-instances)。

要创建执行实例类型外部帐户，请应用以下步骤：

1. 转到文件 **[!UICONTROL Administration > Platform > External accounts]** 夹。
1. 选择随Adobe Campaign提供的现成执行实例类型之一，右键单击并选择 **[!UICONTROL Duplicate]** 。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根据您的需求更改标签。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 选择选 **[!UICONTROL Enabled]** 项以使外部帐户可运行。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安装执行实例的服务器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帐户必须与操作符文件夹中定义的消息中心代理匹配。 默认情况下，Adobe Campaign提供的现成帐户为 **[!UICONTROL mc]** 。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 输入操作符文件夹中定义的帐户密码。

   >[!NOTE]
   >
   >为避免每次登录实例时输入口令，可在执行实例中指定控件实例的IP地址。 For more on this, refer to [Execution instance](#execution-instance).

1. 指定要由执行实例使用的恢复方法。

   执行实例将要恢复的数据转发到控制实例，以添加到事务消息和事件存档。

   ![](assets/messagecenter_create_extaccount_007.png)

   通过使用HTTP/HTTPS访问的Web服务或通过Federated Data Access(FDA)模块进行数据收集。

   >[!NOTE]
   >
   >请注意，在HTTP上使用FDA时，仅支持使用Postgres数据库的执行实例。 不支持MSSQL或Oracle数据库。

   如果控制实例可以直接访问执行实例的数据库，则建议使用第二种方法。 否则，选择Web服务访问。 要指定的FDA帐户与在控制实例上创建的各种执行实例的数据库的连接一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有关Federated Data Access(FDA)的详细信息，请参阅 [访问外部数据库](../../platform/using/about-fda.md)。

1. 单 **[!UICONTROL Test the connection]** 击以确保控件实例和执行实例已关联。

   ![](assets/messagecenter_create_extaccount_006.png)

1. 每个执行实例都必须与标识符相关联。 此标识符可以通过使用部署向导(请参阅标识执行实例 [)手动分配给每个执行实例，也可以通过单击控制实例的](../../message-center/using/identifying-execution-instances.md)**** Initialize连接按钮自动分配给每个执行实例。

   ![](assets/messagecenter_create_extaccount_006bis.png)

## 执行实例 {#execution-instance}

为了使控制实例能够连接到执行实例而无需提供口令，只需在消息中心访问权限部分中输入控制实例的 **IP地址** 。 但是，默认情况下禁止使用空密码。

要使用空密码，请转到执行实例，并定义一个限制于传送事件的信息系统IP地址的安全区。 此安全区域必须允许空密码并接受类 `<identifier> / <password>` 型连接。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符进行划分。 有关详细信息，请参阅使 [用多个控件实例](#using-several-control-instances)。

1. 转到执行实例( **[!UICONTROL Administration > Access management > Operators]** )中的运算符文件夹。
1. 选择“消 **息中心** ”代理。

   ![](assets/messagecenter_operator_001.png)

1. 选择选 **[!UICONTROL Edit]** 项卡，单 **[!UICONTROL Access rights]** 击，然后单击链 **[!UICONTROL Edit the access parameters...]** 接。

   ![](assets/messagecenter_operator_002.png)

1. 在窗 **[!UICONTROL Access settings]** 口中，单击链 **[!UICONTROL Add a trusted IP mask]** 接并添加控件实例的IP地址。

   ![](assets/messagecenter_operator_003.png)

## 使用多个控件实例 {#using-several-control-instances}

您可以与各种控制实例共享执行群集。 此类架构需要以下配置。

例如，如果您的公司管理两个品牌，每个品牌都有其自己的控制实例：控 **制1** 和 **控制2**。 还使用两个执行实例。 您需要为每个控件实例输入不同的消息中心运算符： **Control** 1实例的mc运算符和 **Control 2实例的** mc2 **运****** 算符。

在所有执行实例的树中，为每个操作符创建一个文件夹(**Folder 1** and **Folder 2**)，并限制每个操作符对其文件夹的数据访问。

### 配置控件实例 {#configuring-control-instances}

1. 在 **Control 1** 控制实例中，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入 **mc1** 运算符。 之后 **将在所有执行实例上创建** mc1运算符(请参阅配置 [执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_1.png)

1. 在 **Control 2控制实例中** ，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入 **mc2** 运算符。 之后 **将在所有执行实例上创建** mc2运算符(请参阅配置 [执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有关配置控件实例的详细信息，请参阅 [Control实例](#control-instance)。

### 配置执行实例 {#configuring-execution-instances}

要使用多个控件实例，必须对所有执行实例执行此配置。

1. 在节点中，为每个操作员创建一个文 **[!UICONTROL Administration > Production > Message Center]** 件夹：文 **件夹1** 和 **文件夹2**。 有关创建文件夹和视图的详细信息，请参阅 [平台](../../platform/using/access-management.md#folders-and-views)。

   ![](assets/messagecenter_multi_control_3.png)

1. 复制默 **认提供的** Message center运算符( **mc******)，创建mc1和mc2运算符。 For more on creating operators, refer to [this section](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 和 **mc2** 运营商必须具有权 **[!UICONTROL Message Center execution]** 限，并且无法访问Adobe Campaign客户端控制台。 操作员必须始终与安全区关联。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

1. 对于每个运算符，选中 **[!UICONTROL Restrict to information found in sub-folders of]** 该框，然后选择相关的文件夹(**Folder 1** for the **mc1** operator and **Folder 2****** for the mc2 operator)。

   ![](assets/messagecenter_multi_control_5.png)

1. 为每个操作员授予其文件夹的读写权限。 为此，请右键单击文件夹并选择 **[!UICONTROL Properties]** 。 然后，选择选 **[!UICONTROL Security]** 项卡并添加相关的运算符(**mc1** for **Folder 1** , **mc2****** for Leader 2)。 确保选中 **[!UICONTROL Read/Write data]** 了这些框。

   ![](assets/messagecenter_multi_control_6.png)

