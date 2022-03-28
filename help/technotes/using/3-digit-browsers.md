---
product: campaign
title: Chrome Firefox和Edge浏览器中的Campaign Web组件和版本100
description: Chrome、Firefox和Edge浏览器中的Campaign Web组件和版本100
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: b8329e24f07ec8b3dd89f655b47699f130266008
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# 3位数的浏览器版本对Campaign Web组件的影响 {#version-100}

Google和Mozilla警告，Chrome和Firefox由于即将推出3位版本，可能会损坏某些网站。

Chrome v100已设置为在 **2022年3月29日**，和Firefox v100 on **2022年5月3日**.

Microsoft于2022年3月早些时候发布Edge v100。

版本号从2位更改为3位，在访问未准备好进行此更改的网站时，可能会导致一些问题。 某些网页可能会在这些新浏览器版本中停止正确显示。

主要网站的兼容性已提前进行测试。 如果在发布这些版本之前站点存在无法修复的问题，则公司将制定备份计划，以确保站点不受影响。

网站上的潜在问题或功能丢失源于浏览器发送到您正在访问的网站的用户代理字符串：用户代理是由浏览器发送到网站的字符串，用于告知网站您使用的浏览器和版本以及相关技术。 当您的浏览器向网站发送请求时，它会使用用户代理字符串标识自己，然后再检索您请求的内容。 用户代理字符串中的数据可帮助网站以适合您的浏览器的格式交付内容。 用户代理的版本会递增以匹配浏览器版本号。 从2位移到3位可能会导致问题。

## 您是否受影响？{#version-100-impact}

Adobe建议您测试Campaign Web应用程序（包括Web窗体和调查），以确保它们仍然可以使用这些新浏览器版本正常工作。

此建议适用于所有Web应用程序，特别是当您已包含JavaScript代码时。

您必须使用所有浏览器、移动设备和桌面进行检查。

## 如何测试？{#version-100-test}

您可以立即将浏览器配置为报告100版本，然后报告并更正您遇到的任何问题。

通过这些设置，浏览器会将新用户代理字符串发送到网站，这表示浏览器为v100。 如果您在Web窗体中遇到任何问题，则应该为浏览器编辑器创建错误。 请考虑在这些更新广泛可用之前重新构建这些Web窗体。

### 使用Firefox 100测试{#test-firefox-100}

要使用Mozilla Firefox 100测试网页，您可以通过手动更改用户代理字符串来模拟即将在您的Web应用程序上发生的用户代理更改。

1. 打开Firefox，输入 `about:config` 在地址栏中，然后按enter。
1. 搜索 `general.useragent.override`.
1. 选择“字符串”，然后单击加号(+)。

   ![](assets/force-user-agent-firefox.png)

1. 在字段中输入以下文本：

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. 单击蓝色复选标记按钮以保存设置。
1. 关闭并重新启动浏览器。

要将用户代理更改回默认值，只需返回 `about:config` 和搜索 `general.useragent.override` 设置。  出现后，单击垃圾桶图标以删除设置，然后重新启动浏览器。

### 使用Chrome 100进行测试{#test-chrome-100}

要在您自己的Web应用程序上测试Google Chrome 100用户代理，可以通过以下步骤启用此测试：

1. 打开Chrome，输入 `chrome://flags` 在地址栏中，然后按enter。
1. 搜索 `Force major version to 100 in User-Agent` ，并将其启用，如下所示。

   ![](assets/force-user-agent-chrome.png)

1. 重新启动浏览器。
1. 关闭 `chrome://flags` 选项卡。

要将用户代理更改为默认代理，只需按照此过程将标志的设置更改为 `Default` 然后重新启动浏览器。


### 使用Microsoft Edge 100进行测试{#test-ms-edge-100}

从v97开始，站点所有者可以通过启用实验标记来模拟此版本  `#force-major-version-to-100` in `edge://flags`.

1. 打开Microsoft Edge，输入 `edge://flags` 在地址栏中，然后按enter。
1. 搜索 `force-major-version-to-100` ，并将其启用，如下所示。

   ![](assets/force-user-agent-edge.png)

1. 重新启动浏览器。
1. 关闭 `edge://flags` 选项卡。

要将用户代理更改为默认代理，只需按照此过程将标志的设置更改为 `Default` 然后重新启动浏览器。
