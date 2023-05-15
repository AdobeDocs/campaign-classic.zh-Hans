---
product: campaign
title: 配置实例
description: 了解如何在Adobe Campaign Classic中配置事务型消息传递控制和执行实例
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---


# 配置实例 {#creating-a-shared-connection}



要使用事务型消息传递功能，您需要配置控制和执行实例。 您可以使用以下任一方法：
* [一个控制实例](#control-instance) 与一个或多个执行实例关联
* [多个控制实例](#using-several-control-instances) 与多个执行实例关联

>[!IMPORTANT]
>
>架构扩展会影响 [消息中心技术工作流](../../message-center/using/additional-configurations.md#technical-workflows) 控件或执行实例需要复制到事务型消息传递模块使用的其他实例上。

您还需要指定执行实例并将其连接到控制实例。

此部分介绍了配置和连接控制实例和执行实例所需的所有步骤。

>[!IMPORTANT]
>
>控制实例和执行实例必须安装在不同的计算机上。 他们无法共享同一Campaign实例。

## 配置控制实例 {#control-instance}

要连接控制实例和执行实例，您首先需要创建并配置 **[!UICONTROL Execution instance]** 类型外部帐户 **在控制实例上**. 因此， [发布](../../message-center/using/publishing-message-templates.md#template-publication)，事务型消息模板可部署到执行实例。

如果您使用多个执行实例，则必须创建与存在执行实例相同数量的外部帐户。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符进行划分。 有关此内容的更多信息，请参阅 [使用多个控制实例](#using-several-control-instances).

### 创建外部帐户

>[!NOTE]
>
>必须执行以下步骤 **在控制实例上**.

创建 **[!UICONTROL Execution instance]** 键入外部帐户，应用以下内容：

1. 转到 **[!UICONTROL Administration > Platform > External accounts]** 文件夹。
1. 选择一个执行实例类型，其中一个是随Adobe Campaign提供的现成外部帐户，右键单击并选择 **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根据需要更改标签。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 选择 **[!UICONTROL Enabled]** 选项，以使外部帐户可正常运行。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安装执行实例的服务器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帐户必须与操作员文件夹中定义的消息中心代理相匹配。 默认情况下，Adobe Campaign提供的现成帐户为 **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. 输入在操作员文件夹中定义的帐户密码。

   >[!NOTE]
   >
   >为避免在每次登录到实例时输入密码，您可以在执行实例中指定控制实例的IP地址。 有关此内容的更多信息，请参阅 [配置执行实例](#execution-instance).

1. 指定要由执行实例使用的恢复方法。 要恢复的数据由执行实例转发到控制实例，以添加到事务型消息和事件存档。

   ![](assets/messagecenter_create_extaccount_007.png)

   数据收集是通过使用HTTP/HTTPS访问的Web服务进行，或通过联合数据访问(FDA)模块进行。

   >[!NOTE]
   >
   >请注意，在通过HTTP使用FDA时，仅支持使用PostgreSQL数据库的执行实例。 不支持MSSQL或Oracle数据库。

   如果控制实例可以直接访问执行实例的数据库，则建议使用第二种方法(FDA)。 如果没有，请选择Web服务访问。 要指定的FDA帐户与与在控制实例上创建的各种执行实例的数据库的连接一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有关联合数据访问(FDA)的更多信息，请参阅 [此部分](../../installation/using/about-fda.md).

1. 单击 **[!UICONTROL Test the connection]** 以确保控制实例和执行实例已关联。

   ![](assets/messagecenter_create_extaccount_006.png)

使用多个执行实例时，请重复这些步骤以创建与存在执行实例相同数量的外部帐户。

### 确定执行实例 {#identifying-execution-instances}

每个执行实例必须与唯一标识符关联，以便在控制实例上查看每个执行实例的历史记录时区分这些实例的历史记录。

此标识符可归因于每个执行实例 **手动**. 在这种情况下，必须执行此步骤 **在每个执行实例上**. 要实现此目的，请使用部署向导，如下所述：

1. 在执行实例上打开部署向导。
1. 转到 **[!UICONTROL Message Center]** 窗口。
1. 将您选择的标识符分配给实例。

   ![](assets/messagecenter_id_execinstance_001.png)

1. 对每个执行实例重复上述步骤。

标识符也可以是 **自动** 属性。 要执行此操作，请转到 **控制实例**，然后单击 **[!UICONTROL Initialize connection]** 按钮。

![](assets/messagecenter_create_extaccount_006bis.png)

## 配置执行实例 {#execution-instance}

>[!NOTE]
>
>必须执行以下步骤 **执行实例上**.

要将执行实例连接到控制实例，请执行以下步骤。

为了使控制实例能够连接到执行实例而不必给出口令，只需在 **消息中心** 访问权限部分。 但是，默认情况下禁止使用空密码。

要使用空密码，请转到执行实例，并定义一个限制为用于传送事件的信息系统IP地址的安全区域。 此安全区域必须允许空密码并接受 `<identifier> / <password>` 类型连接。 如需详细信息，请参阅[此部分](../../installation/using/security-zones.md)。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符进行划分。 有关此内容的更多信息，请参阅 [使用多个控制实例](#using-several-control-instances).

1. 在执行实例中，转到运算符文件夹( **[!UICONTROL Administration > Access management > Operators]** )。
1. 选择 **消息中心** 代理。

   ![](assets/messagecenter_operator_001.png)

1. 选择 **[!UICONTROL Edit]** ，单击 **[!UICONTROL Access rights]** ，然后单击 **[!UICONTROL Edit the access parameters...]** 链接。

   ![](assets/messagecenter_operator_002.png)

1. 在 **[!UICONTROL Access settings]** 窗口，单击 **[!UICONTROL Add a trusted IP mask]** 链接并添加控制实例的IP地址。

   ![](assets/messagecenter_operator_003.png)

使用多个执行实例时，对每个执行实例重复这些步骤。

## 使用多个控制实例 {#using-several-control-instances}

您可以与各种控制实例共享执行群集。 此类架构需要以下配置。

例如，假设您的公司管理两个品牌，每个品牌都有其自己的控制实例： **控制1** 和 **控制2**. 还使用两个执行实例。 您需要为每个控制实例输入不同的消息中心运算符：an **mc1** 运算符 **控制1** 实例和 **mc2** 运算符 **控制2** 实例。

在所有执行实例的树中，为每个运算符创建一个文件夹(**文件夹1** 和 **文件夹2**)，并限制每个运算符对其文件夹的数据访问。

### 配置控制实例 {#configuring-control-instances}

>[!NOTE]
>
>必须执行以下步骤 **在控制实例上**.

1. 在 **控制1** 控制实例，为每个执行实例创建一个外部帐户，然后输入 **mc1** 运算符。 的 **mc1** 之后，将在所有执行实例上创建运算符(请参阅 [配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_1.png)

1. 在 **控制2** 控制实例，为每个执行实例创建一个外部帐户，然后输入 **mc2** 运算符。 的 **mc2** 之后，将在所有执行实例上创建运算符(请参阅 [配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有关配置控制实例的更多信息，请参阅 [此部分](#control-instance).

### 配置执行实例 {#configuring-execution-instances}

>[!NOTE]
>
>必须执行以下步骤 **执行实例**.

要使用多个控制实例，必须对所有执行实例执行此配置。

1. 在 **[!UICONTROL Administration > Production > Message Center]** 节点： **文件夹1** 和 **文件夹2**. 有关创建文件夹和视图的更多信息，请参阅 [本页](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. 创建 **mc1** 和 **mc2** 运算符（复制默认提供的消息中心运算符）**mc**)。 有关创建运算符的更多信息，请参阅 [此部分](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 和 **mc2** 运算符必须 **[!UICONTROL Message Center execution]** 权限，且他们无权访问Adobe Campaign客户端控制台。 运算符必须始终与安全区域链接。 如需详细信息，请参阅[此部分](../../installation/using/security-zones.md)。

1. 对于每个运算符，请检查 **[!UICONTROL Restrict to information found in sub-folders of]** ，然后选择相关文件夹(**文件夹1** 对于 **mc1** 运算符和 **文件夹2** 对于 **mc2** 运算符)。

   ![](assets/messagecenter_multi_control_5.png)

1. 为每个操作员授予其文件夹的读写权限。 要执行此操作，请右键单击文件夹并选择 **[!UICONTROL Properties]** . 然后，选择 **[!UICONTROL Security]** 选项卡，并添加相关运算符(**mc1** 表示 **文件夹1** 和 **mc2** 表示 **文件夹2**)。 确保 **[!UICONTROL Read/Write data]** 复选框。

   ![](assets/messagecenter_multi_control_6.png)
