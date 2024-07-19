---
product: campaign
title: 创建实例并登录
description: 创建实例并登录
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# 创建实例并登录{#creating-an-instance-and-logging-on}



要创建新实例和Adobe Campaign数据库，请应用以下流程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库。

>[!NOTE]
>
>**只有内部**&#x200B;标识符才能执行这些操作。如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

启动Adobe Campaign控制台后，您可以访问登录页面。

要创建新实例，请按照以下步骤操作：

1. 单击凭据字段右上角的链接以访问连接配置窗口。 此链接可以是&#x200B;**[!UICONTROL New...]**&#x200B;或现有的实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击&#x200B;**[!UICONTROL Add > Connection]**&#x200B;并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名或IP地址。

   例如，您可以使用`https://<machine>.<domain>.com`类型URL。

   >[!CAUTION]
   >
   >对于连接 URL，仅使用以下字符： `[a-z]`、 `[A-Z]`、 `[0-9]` 短划线 （-） 或句号。

1. 单击以 **[!UICONTROL Ok]** 确认设置：您现在可以开始实例创建过程。
1. 在 **[!UICONTROL Connection settings]** 窗口中，输入 **内部** 登录名及其密码以连接到Adobe Campaign应用程序服务器。 连接后，您可以访问实例创建向导以声明新实例
1. 在字段中 **[!UICONTROL Name]** ，输入 **实例名称**。 由于此名称用于生成配置文件 **config-`<instance>`.xml** ，并在命令行参数中用于标识实例，因此请确保选择一个不带特殊字符的短名称。 例如： **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名中的实例名称不得超过 40 个字符。 这使您可以限制“Message-ID”标头的大小，并防止邮件被视为垃圾邮件，尤其是 SpamAssassin 等工具。

1. 在 **[!UICONTROL DNS masks]** 字段中，输入 **实例应附加到的 DNS 掩码** 列表。 Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串&#x200B;**https://**&#x200B;和服务器地址的第一个斜杠字符&#x200B;**/**&#x200B;之间。

   您可以定义以逗号分隔的值列表。

   是？ &#42;字符可以用作通配符来替换一个或多个字符（DNS、端口等）。例如， **demo&#42;** 值将与“https://demo”一起使用，就像它适用于“https://demo:8080”甚至“https://demo2”。

   使用的名称必须在 DNS 中定义。 您还可以在 **Windows 的 c：/windows/system32/drivers/etc/hosts** 文件和 **Linux 的 /etc/hosts** 文件中通知 DNS 名称和 IP 地址之间的对应关系。 因此，您必须修改连接设置以使用此 DNS 名称，才能连接到您选择的实例。

   服务器必须使用此名称进行标识，尤其是在电子邮件中上传图像时。

   此外，服务器必须能够通过此名称连接到自身，如果可能的话，还可以通过环回地址 - 127.0.0.1 - 连接到自身，特别是允许以 PDF 格式导出报告。

1. 在下拉列表中&#x200B;**[!UICONTROL Language]****，选择实例语言**：英语（美国）、英语（英国）、法语或日语。

   美式英语和英国英语之间的差异在[本节](../../platform/using/adobe-campaign-workspace.md#date-and-time)中进行了说明。

   >[!CAUTION]
   >
   >在此步骤之后无法修改实例语言。 Adobe Campaign实例不是多语言的：您无法将界面从一种语言切换到另一种语言。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认实例声明。 注销并重新登录以声明数据库。

   >[!NOTE]
   >
   >可以从命令行创建实例。 有关更多信息，请参阅 [命令行](../../installation/using/command-lines.md)。
