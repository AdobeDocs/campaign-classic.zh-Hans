---
product: campaign
title: Chrome Firefox和Edge浏览器中的Campaign Web组件和版本100
description: Chrome、Firefox和Edge浏览器中的Campaign Web组件和版本100
feature: Technote
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# 3位数浏览器版本对Campaign Web组件的影响 {#version-100}

Google和Mozilla警告称，Chrome和Firefox可能因其即将推出的3位数版本而破坏某些网站。

Chrome v100的发行日期为 **2022年3月29日**&#x200B;上的和Firefox v100 **2022年5月3日**.

Microsoft于2022年3月早些时候发布了Edge v100。

如果版本号从2位更改为3位，则在访问未针对此更改做好准备的网站时，可能会导致一些问题。 在这些新的浏览器版本中，某些网页可能会停止正确显示。

提前测试了一些主要网站的兼容性。 如果在发布这些版本之前无法修复的网站出现问题，则公司已准备好备份计划以确保网站不受影响。

网站上的潜在问题或功能缺失源于浏览器发送到您正在访问的网站的用户代理字符串：用户代理是浏览器发送到网站的字符串，旨在告知网站您使用的浏览器和版本以及相关技术。 当您的浏览器向网站发送请求时，会在检索您请求的内容之前使用用户代理字符串标识自身。 用户代理字符串中的数据可帮助网站以适合您的浏览器的格式交付内容。 用户代理的版本将递增，以匹配浏览器的版本号。 从2位数字移动到3位数字可能会导致问题。

## 您是否受影响？{#version-100-impact}

Adobe建议您测试Campaign Web应用程序（包括Web窗体及调查），以确保它们仍然可以很好地与这些新浏览器版本配合使用。

此建议适用于所有Web应用程序，尤其是当您已包含JavaScript代码时。

您必须检查所有浏览器，包括移动和桌面浏览器。

## 如何测试？{#version-100-test}

您可以将浏览器配置为立即将版本报告为100，然后报告和更正您遇到的任何问题。

使用这些设置，浏览器会将新的用户代理字符串发送到网站，这表示浏览器是v100。 如果您在Web窗体时遇到任何问题，则应为浏览器编辑器创建错误。 请考虑重新构建这些Web窗体，然后这些更新才可广泛获取。

### 使用Firefox 100进行测试{#test-firefox-100}

要使用Mozilla Firefox 100测试网页，您可以通过手动更改用户代理字符串来模拟即将对Web应用程序进行的用户代理更改。

1. 打开Firefox，输入 `about:config` ，然后按Enter。
1. 搜索 `general.useragent.override`.
1. 选择“字符串”，然后单击加号(+)。

   ![](assets/force-user-agent-firefox.png)

1. 在字段中输入以下文本：

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. 单击蓝色复选标记按钮以保存设置。
1. 关闭并重新启动浏览器。

要将用户代理更改回其默认值，只需返回到 `about:config` 和搜索 `general.useragent.override` 再次设置。  出现时，单击垃圾桶图标以删除设置，然后重新启动浏览器。

### 使用Chrome 100进行测试{#test-chrome-100}

要在您自己的Web应用程序上测试Google Chrome 100用户代理，可以使用以下步骤启用此测试：

1. 打开Chrome，输入 `chrome://flags` ，然后按Enter。
1. Search `Force major version to 100 in User-Agent` ，并启用该功能，如下所示。

   ![](assets/force-user-agent-chrome.png)

1. 重新启动浏览器。
1. 关闭 `chrome://flags` 选项卡。

要将用户代理更改回其默认值，只需按照此流程并将标记设置更改为 `Default` 然后重新启动浏览器。


### 使用Microsoft Edge 100进行测试{#test-ms-edge-100}

从v97开始，站点所有者可以通过启用试验标志来模拟此版本  `#force-major-version-to-100` 在 `edge://flags`.

1. 打开Microsoft Edge，输入 `edge://flags` ，然后按Enter。
1. 搜索 `force-major-version-to-100` 字段，并将其启用，如下所示。

   ![](assets/force-user-agent-edge.png)

1. 重新启动浏览器。
1. 关闭 `edge://flags` 选项卡。

要将用户代理更改回其默认值，只需按照此流程并将标记设置更改为 `Default` 然后重新启动浏览器。
