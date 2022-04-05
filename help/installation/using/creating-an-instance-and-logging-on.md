---
product: campaign
title: 创建实例并登陆
description: 创建实例并登陆
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 5%

---

# 创建实例并登陆{#creating-an-instance-and-logging-on}

![](../../assets/v7-only.svg)

要创建新实例和Adobe Campaign数据库，请应用以下过程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库.

>[!NOTE]
>
>仅 **内部** 标识符可以执行这些操作。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

启动Adobe Campaign控制台后，您将访问登录页面。

要创建新实例，请执行以下步骤：

1. 单击凭据字段右上角的链接以访问连接配置窗口。 此链接可以是 **[!UICONTROL New...]** 或现有实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击 **[!UICONTROL Add > Connection]** 并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用DNS或计算机的别名，或您的IP地址。

   例如，您可以使用 `https://<machine>.<domain>.com` 键入URL。

   >[!CAUTION]
   >
   >对于连接URL，仅使用以下字符： `[a-z]`, `[A-Z]`, `[0-9]` 和破折号(-)或全停。

1. 单击 **[!UICONTROL Ok]** 要确认设置，请执行以下操作：您现在可以从实例创建过程开始。
1. 在 **[!UICONTROL Connection settings]** 窗口，输入 **内部** 用于连接到Adobe Campaign应用程序服务器的登录及其密码。 连接后，您将访问实例创建向导以声明新实例
1. 在 **[!UICONTROL Name]** 字段，输入 **实例名称**. 由于此名称用于生成配置文件 **配置 — `<instance>`.xml** 和用在命令行参数中以标识实例，请确保选择不带特殊字符的短名称。 例如： **电子营销**.

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的实例名称不得超过40个字符。 这样，您就可以限制“消息ID”标头的大小，并防止消息被视为垃圾信息，尤其是SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** 字段，输入 **DNS掩码列表** 实例附加到的ID。 Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串之间 **https://** 和第一个斜线字符 **/** 服务器地址的。

   您可以定义一个值列表，其中各个值之间用逗号分隔。

   此 ? 和 &#42; 字符可用作通配符来替换一个或多个字符（DNS、端口等）。 例如， **演示&#42;** 值将与“https://demo”一起使用，因为它与“https://demo:8080”甚至“https://demo2”一起使用。

   使用的名称必须在DNS中定义。 您还可以通知DNS名称与 **c:/windows/system32/drivers/etc/hosts** 文件 **/etc/hosts** 文件。 因此，您必须修改连接设置以使用此DNS名称，才能连接到您选择的实例。

   服务器必须使用此名称进行标识，尤其是用于在电子邮件中上传图像。

   此外，服务器必须能够通过此名称连接自身，如果可能，还可以通过环回地址(127.0.0.1)连接自身，尤其是允许以PDF格式导出报表。

1. 在 **[!UICONTROL Language]** 下拉列表中，选择 **实例语言**:英语（美国）、英语（英国）、法语或日语。

   美式英语与英式英语之差异在 [此部分](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >此步骤后无法修改实例语言。 Adobe Campaign实例不是多语言：无法将界面从一种语言切换到另一种语言。

1. 单击 **[!UICONTROL Ok]** 确认实例声明。 注销然后重新启动以声明数据库。

   >[!NOTE]
   >
   >可以从命令行创建实例。 有关更多信息，请参阅 [命令行](../../installation/using/command-lines.md).
