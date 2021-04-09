---
solution: Campaign Classic
product: campaign
title: 创建实例并登陆
description: 创建实例并登陆
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# 创建实例并登陆{#creating-an-instance-and-logging-on}

要创建新实例和Adobe Campaign数据库，请应用以下过程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库.

>[!NOTE]
>
>只有&#x200B;**internal**&#x200B;标识符可以执行这些操作。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

启动Adobe Campaign控制台后，您可以访问登录页面。

要创建新实例，请按照以下步骤操作：

1. 单击凭据字段右上角的链接以访问连接配置窗口。 此链接可以是&#x200B;**[!UICONTROL New...]**&#x200B;或现有实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击&#x200B;**[!UICONTROL Add > Connection]**&#x200B;并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定通过URL与Adobe Campaign应用程序服务器的连接。 使用DNS或计算机的别名，或您的IP地址。

   例如，可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)类型URL。

   >[!CAUTION]
   >
   >对于连接URL，仅使用以下字符：`[a-z]`、`[A-Z]`、`[0-9]`和短划线(-)或完全停止。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认设置：您现在可以从实例创建过程开始。
1. 在&#x200B;**[!UICONTROL Connection settings]**&#x200B;窗口中，输入&#x200B;**internal**&#x200B;登录名及其连接到Adobe Campaign应用程序服务器的口令。 连接后，您可以访问实例创建向导以声明新实例
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;字段中，输入&#x200B;**实例名**。 由于此名称用于生成配置文件&#x200B;**config-`<instance>`.xml**，并用在命令行参数中以标识实例，因此请确保您选择一个不带特殊字符的短名称。 例如：**eMarketing**。

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的实例的名称不得超过40个字符。 这样，您就可以限制“Message-ID”头的大小，并防止将邮件视为垃圾邮件，尤其是通过SpamAssassin等工具。

1. 在&#x200B;**[!UICONTROL DNS masks]**&#x200B;字段中，输入应将实例附加到的DNS掩码&#x200B;**列表。** Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串&#x200B;**https://**&#x200B;和服务器地址的第一个斜杠字符&#x200B;**/**&#x200B;之间。

   您可以定义用逗号分隔的值列表。

   ? 和*字符可用作通配符，以替换一个或多个字符（DNS、端口等）。 例如，**demo***&#x200B;值将像与“https://demo:8080”甚至“https://demo2”一样与“https://demo”一起使用。

   使用的名称必须在DNS中定义。 您还可以在Windows中的&#x200B;**c:/windows/system32/drivers/etc/hosts**&#x200B;文件和Linux中的&#x200B;**/etc/hosts**&#x200B;文件中通知DNS名称与IP地址之间的对应关系。 因此，您必须修改连接设置才能使用此DNS名称，才能连接到所选实例。

   服务器必须用此名称进行标识，尤其是用于在电子邮件中上传图像。

   此外，服务器必须能够通过此名称连接到自身，并且如果可能通过环回地址(127.0.0.1)连接到自己，尤其是允许以PDF格式导出报表。

1. 在&#x200B;**[!UICONTROL Language]**&#x200B;下拉列表中，选择&#x200B;**实例语言**:英语（美国）、英语（英国）、法语或日语。

   美国英语和英国英语之间的差异在[本节](../../platform/using/adobe-campaign-workspace.md#date-and-time)中进行了说明。

   >[!CAUTION]
   >
   >此步骤后无法修改实例语言。 Adobe Campaign实例不是多语言：无法将界面从一种语言切换到另一种语言。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认实例声明。 注销并重新登录以声明数据库。

   >[!NOTE]
   >
   >可以从命令行创建实例。 有关详细信息，请参阅[命令行](../../installation/using/command-lines.md)。
