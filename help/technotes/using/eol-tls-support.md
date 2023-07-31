---
product: campaign
title: TLS 1.0 和 1.1 支持生命周期终止
description: TLS 1.0 和 1.1 支持生命周期终止
feature: Technote
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 4%

---

# TLS 1.0 和 1.1 支持生命周期终止{#eol-tls-support}



Adobe不再支持不符合Transport Layer Security (TLS) 1.2协议的用户系统和客户端系统。 如果您继续使用旧版本的TLS，则可能会失去对所有Adobe产品和服务的访问权限。

## 为什么我会看到此页面？

如果您看到以下消息： **此页面无法显示**，这意味着您尝试访问的Adobe应用程序、网页或服务需要与Web浏览器、操作系统或应用程序建立更安全的网络连接。 必须使用 **TLS 1.2** 用于用户系统与Adobe应用程序和Web服务之间的安全网络通信和数据交换。

Adobe已弃用对较低版本的TLS（包括TLS 1.0和1.1）的支持。 有关TLS 1.2协议的技术详细信息，请参阅 [常见问题解答](#faq).

## 怎样才能恢复该服务？

现代Web浏览器支持TLS 1.2。升级浏览器可让您访问这些应用程序和服务。

您可以下载并安装以下常用浏览器之一：

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

如果您使用的是其他浏览器，请确保其支持TLS 1.2。

您的操作系统和应用程序框架还必须支持TLS 1.2。如果升级浏览器不能解决问题，请确保您的计算机满足中列出的系统要求 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md).

## 常见问题{#faq}

* **什么是传输层安全性(TLS)？**

  [传输层安全性](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS)是一种安全协议，在两个通信应用程序之间提供隐私和数据完整性。 它广泛部署于Web浏览器和其他需要通过网络安全交换数据的应用程序。

  根据协议规范，TLS分为两层，TLS记录协议和TLS握手协议。 记录协议提供连接安全性。 握手协议使服务器和客户端能够相互验证，并在数据交换之前协商加密算法和加密密钥。

* **会有什么影响？**

  Adobe的安全合规标准要求从2018年5月起弃用旧协议，并强制使用TLS 1.2作为最新版本。 如果您的系统不符合TLS 1.2，则访问某些Adobe应用程序和服务会被限制。

* **TLS如何影响您？**

  您只能通过安全网络连接与某些Adobe应用程序和服务进行交互。 TLS有助于确保浏览器与这些应用程序和Web服务之间的连接是安全可靠的。

  随着新浏览器和操作系统的发布，安全标准也将升级，以确保更高级别的隐私和数据完整性。 但是，这些浏览器或操作系统的旧版本不会更新以包含最新标准。

  随着可接受的安全级别提高，这些较旧、较不安全的浏览器版本和应用程序将被留下。

  要能够连接到安全站点，请更新您的操作系统和浏览器版本。

* **TLS是否易受黑客攻击？**

  已记录使用旧版加密方法对TLS 1.0的攻击，并且旧版比TLS 1.2更易受攻击。有关更多信息，请参阅针对TLS/SSL的攻击。

* **为什么Adobe禁用对TLS 1.0和1.1的支持？**

  Adobe具有安全合规标准，该标准要求禁用对旧协议的支持。 其中一项标准可确保支付卡行业(PCI)的合规性。 PCI适配服务器是一组安全标准，要求接受、处理、存储或传输信用卡信息的组织维护安全的环境。

  从2018年5月起，PCI合规性要求使用TLS 1.1或更高版本。

* **为什么Adobe强制使用TLS 1.2而不是允许TLS 1.1或TLS 1.0？**

  大多数对Adobe应用程序和Web服务的请求源自符合TLS 1.2的用户系统，而TLS 1.1系统的流量较低。

  Adobe已迁移到TLS 1.2，以便更安全地访问其应用程序和Web服务。

* **我可以使用旧版TLS的最后一个日期是什么？**

  Adobe鼓励用户快速放弃旧版本以避免暴露安全漏洞。 有关更多信息，请联系Adobe客户关怀部门或您的客户成功经理。

* **如果使用的浏览器未针对TLS 1.2进行配置，会出现什么错误消息？**

  这取决于您使用的浏览器。 中提到的所有浏览器 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md) 配置为使用TLS 1.2。如果您使用的浏览器或版本未出现在列表中，请更新浏览器。

  Adobe不控制SSL通信层生成的错误消息。 浏览器在连接到Adobe应用程序和服务之前生成这些消息。 以下是Windows 7上的Internet Explorer 11可能发生的错误示例：

  ![](assets/do-not-translate/page-not-displayed.png)

  默认情况下，TLS 1.2在Internet Explorer 11上处于启用状态，但如果关闭它，则可以将其打开。 在这种情况下，请从高级设置对话框中打开TLS 1.2，而不是使用其他选项。 也可能会出现其他错误，例如：

   * 无法连接到服务
   * 服务不可用
   * 连接错误
