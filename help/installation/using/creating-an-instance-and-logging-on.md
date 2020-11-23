---
solution: Campaign Classic
product: campaign
title: 创建实例并登陆
description: 创建实例并登陆
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 3%

---


# 创建实例并登陆{#creating-an-instance-and-logging-on}

要创建新实例和Adobe Campaign库，请应用以下过程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库。

>[!NOTE]
>
>只有内部 **标识符** 才能执行这些操作。 For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

启动Adobe Campaign控制台后，您将访问登录页面。

要创建新实例，请按照以下步骤操作：

1. 单击凭据字段右上角的链接以访问连接配置窗口。 此链接可以是或 **[!UICONTROL New...]** 现有实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单 **[!UICONTROL Add > Connection]** 击并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名，或您的IP地址。

   例如，您可以使用类 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 型URL。

   >[!CAUTION]
   >
   >对于连接URL，只使用以下字符： `[a-z]`、 `[A-Z]`、 `[0-9]` 和虚线(-)或完全停止。

1. 单击 **[!UICONTROL Ok]** 以确认设置：您现在可以从实例创建过程开始。
1. 在窗 **[!UICONTROL Connection settings]** 口中，输入 **内部登录** 及其口令以连接到Adobe Campaign应用程序服务器。 连接后，您可以访问实例创建向导以声明新实例
1. 在字 **[!UICONTROL Name]** 段中，输入实 **例名称**。 由于此名称用于生成配置文 **件config-`<instance>`.xml** ，并用在命令行参数中以标识实例，请确保选择一个不带特殊字符的短名称。 例如： **电子营销**。

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的实例的名称不得超过40个字符。 这样，您就可以限制“Message-ID”头的大小，并防止邮件被视为垃圾邮件，尤其是通过SpamAssassin等工具。

1. 在字 **[!UICONTROL DNS masks]** 段中，输 **入实例应附加到的** DNS掩码的列表。 Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串 **https://** 和服务器地址的第 **一个斜** 杠字符／之间。

   您可以定义一列表以逗号分隔的值。

   ? 和*字符可用作通配符以替换一个或多个字符（DNS、端口等）。 例如，demo* **值将像** “https://demo:8080”甚至“https://demo2”一样与“https://demo”一起使用。

   使用的名称必须在DNS中定义。 您还可以在Windows中的 **c:/windows/system32/drivers/etc/hosts** 文件和Linux中的 **** /etc/hosts文件中通知DNS名称与IP地址之间的对应。 因此，必须修改连接设置才能使用此DNS名称，才能连接到所选实例。

   服务器必须用此名称进行标识，尤其是用于在电子邮件中上传图像。

   此外，服务器必须能够通过此名称和环回地址(127.0.0.1)连接到自身，尤其是允许以PDF格式导出报告。

1. 在下 **[!UICONTROL Language]** 拉列表中，选择实 **例语言**:英语（美国）、英语（英国）、法语或日语。

   本节介绍了美国英语和英国英语之 [间的差异](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

   >[!CAUTION]
   >
   >此步骤后无法修改实例语言。 Adobe Campaign实例不是多语言：不能将界面从语言切换到其他语言。

1. 单击 **[!UICONTROL Ok]** 以确认实例声明。 注销然后重新登录以声明数据库。

   >[!NOTE]
   >
   >可以通过命令行创建实例。 For more on this, refer to [Command lines](../../installation/using/command-lines.md).

