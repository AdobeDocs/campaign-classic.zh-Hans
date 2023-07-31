---
product: campaign
title: 创建实例并登陆
description: 创建实例并登陆
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 5%

---

# 创建实例并登陆{#creating-an-instance-and-logging-on}



要创建新实例和Adobe Campaign数据库，请应用以下流程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库.

>[!NOTE]
>
>仅 **内部** 标识符可以执行这些操作。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

启动Adobe Campaign控制台后，您将访问登录页面。

要创建新实例，请执行以下步骤：

1. 单击凭据字段右上角的链接可访问连接配置窗口。 此链接可以是 **[!UICONTROL New...]** 或现有实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击 **[!UICONTROL Add > Connection]** 并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名或IP地址。

   例如，您可以使用 `https://<machine>.<domain>.com` 键入URL。

   >[!CAUTION]
   >
   >对于连接URL，仅使用以下字符： `[a-z]`， `[A-Z]`， `[0-9]` 和短划线(-)或句号。

1. 单击 **[!UICONTROL Ok]** 要确认设置，请执行以下操作：您现在可以从实例创建过程开始。
1. 在 **[!UICONTROL Connection settings]** 窗口，输入 **内部** 用于连接到Adobe Campaign应用程序服务器的登录名及其密码。 连接后，即可访问实例创建向导以声明新实例
1. 在 **[!UICONTROL Name]** 字段中，输入 **实例名称**. 由于此名称用于生成配置文件 **config-`<instance>`.xml** 和在命令行参数中使用来标识实例，请确保选择不带特殊字符的短名称。 例如： **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的实例名称不能超过40个字符。 这样，您就可以限制“Message-ID”标头的大小，并防止将邮件视为垃圾邮件，尤其是SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** 字段，输入 **DNS掩码列表** 实例应附加到的对象。 Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串之间 **https://** 和第一个斜杠字符 **/** 服务器地址的。

   您可以定义以逗号分隔的值列表。

   此 ? 和 &#42; 字符可用作通配符以替换一个或多个字符（DNS、端口等）。 例如， **演示&#42;** 值将与“https://demo”配合使用，就像与“https://demo:8080”甚至“https://demo2”配合使用一样。

   使用的名称必须在DNS中定义。 您还可以将DNS名称与IP地址之间的通信告知给 **c：/windows/system32/drivers/etc/hosts** 在Windows和 **/etc/hosts** 文件。 因此，您必须修改连接设置以使用此DNS名称，才能连接到您选择的实例。

   服务器必须由此名称标识，尤其是在电子邮件中上传图像时。

   此外，服务器必须能够使用此名称与自身连接，如果可能，还必须使用环回地址127.0.0.1，尤其是要允许以PDF格式导出报告。

1. 在 **[!UICONTROL Language]** 下拉列表，选择 **实例语言**：英语（美国）、英语（英国）、法语或日语。

   美式英语与英式英语的区别详见 [本节](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >在此步骤之后无法修改实例语言。 Adobe Campaign实例不是多语言的：您无法将界面从一种语言切换到另一种语言。

1. 单击 **[!UICONTROL Ok]** 确认实例声明。 注销并重新登录以声明数据库。

   >[!NOTE]
   >
   >可以从命令行创建实例。 有关详细信息，请参见 [命令行](../../installation/using/command-lines.md).
