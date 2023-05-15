---
product: campaign
title: TLS 1.0 和 1.1 支持生命周期终止
description: TLS 1.0 和 1.1 支持生命周期终止
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# TLS 1.0 和 1.1 支持生命周期终止{#eol-tls-support}



Adobe不再支持与传输层安全(TLS)1.2协议不兼容的用户系统和客户端系统。 如果您继续使用旧版TLS，则可能会失去对所有Adobe产品和服务的访问权限。

## 为什么我要看到此页面？

如果您看到以下消息： **无法显示此页**，这表示您尝试访问的Adobe应用程序、网页或服务需要与web浏览器、操作系统或应用程序建立更安全的网络连接。 必须使用 **TLS 1.2** 用户系统与Adobe应用程序和web服务之间的安全网络通信和数据交换。

Adobe已弃用对较低版本的TLS（包括TLS 1.0和1.1）的支持。 有关TLS 1.2协议的技术详细信息，请参阅 [常见问题解答](#faq).

## 恢复服务可以执行哪些操作？

新式Web浏览器支持TLS 1.2。升级您的浏览器可以访问这些应用程序和服务。

您可以下载并安装以下一种常用浏览器：

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

如果您使用的是其他浏览器，请确保它支持TLS 1.2。

您的操作系统和应用程序框架还必须支持TLS 1.2。如果升级您的浏览器无法解决您的问题，请确保您的计算机符合 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md).

## 常见问题{#faq}

* **什么是传输层安全性(TLS)?**

   [传输层安全性](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS)是一种安全协议，可在两个通信应用程序之间提供隐私和数据完整性。 它广泛用于Web浏览器和其他需要通过网络安全交换数据的应用程序。

   根据协议规范，TLS包括两层，即TLS记录协议和TLS握手协议。 记录协议提供连接安全性。 握手协议使服务器和客户端能够相互验证，并在数据交换之前协商加密算法和加密密钥。

* **会有什么影响？**

   Adobe的安全合规标准要求从2018年5月起弃用旧协议，并规定使用TLS 1.2作为最新版本。 如果您的系统不符合TLS 1.2，则对某些Adobe应用程序和服务的访问将会受到限制。

* **TLS对您有何影响？**

   您只能通过安全的网络连接来使用某些Adobe应用程序和服务。 TLS有助于确保浏览器与这些应用程序和Web服务之间的连接安全可靠。

   随着新浏览器和操作系统的发布，安全标准将得到升级，以确保更高级别的隐私和数据完整性。 但是，这些浏览器或操作系统的早期版本不会更新为包含最新标准。

   随着可接受的安全级别的提高，这些较旧、较不安全的浏览器版本和应用程序将被遗弃。

   要能够与安全站点连接，请更新您的操作系统和浏览器版本。

* **TLS是否容易受到黑客的攻击？**

   已记录到使用旧加密方法对TLS 1.0发起的攻击，且较旧版本比TLS 1.2更易受攻击。有关更多信息，请参阅对TLS/SSL发起的攻击。

* **为什么Adobe会禁用对TLS 1.0和1.1的支持？**

   Adobe有安全合规标准，要求对旧协议禁用支持。 其中一个标准可确保符合支付卡行业(PCI)。 PCI适配服务器是一组安全标准，要求组织接受、处理、存储或传输信用卡信息以维护安全环境。

   自2018年5月起，PCI合规性要求使用TLS 1.1或更高版本。

* **为什么Adobe强制使用TLS 1.2，而不是允许TLS 1.1或TLS 1.0?**

   对Adobe应用程序和Web服务的大多数请求源自符合TLS 1.2规范的用户系统，而来自TLS 1.1系统的流量较低。

   Adobe已迁移到TLS 1.2，因此可以更安全地访问其应用程序和Web服务。

* **我可以使用旧版TLS的最后一个日期是什么时间？**

   Adobe鼓励用户快速放弃旧版本，以避免暴露安全漏洞。 有关更多信息，请联系Adobe客户关怀团队或您的客户成功经理。

* **如果我使用的浏览器未配置TLS 1.2，会显示什么错误消息？**

   这取决于您所使用的浏览器。 中提及的所有浏览器 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md) 配置为使用TLS 1.2。如果您使用的浏览器或版本在列表中未显示，请更新您的浏览器。

   Adobe不控制由SSL通信层生成的错误消息。 浏览器在连接到Adobe应用程序和服务之前会生成这些消息。 以下是Windows 7上的Internet Explorer 11可能发生的错误示例：

   ![](assets/do-not-translate/page-not-displayed.png)

   默认情况下，TLS 1.2在Internet Explorer 11中处于启用状态，但如果将其关闭，则可以将其打开。 在这种情况下，请从“高级设置”对话框中打开TLS 1.2，而不是使用其他选项。 其他错误，例如：

   * 无法连接到服务
   * 服务不可用
   * 连接错误
