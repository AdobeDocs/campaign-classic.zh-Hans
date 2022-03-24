---
product: campaign
title: Chrome和Firefox浏览器中的Campaign Web组件和版本100
description: Chrome和Firefox浏览器中的Campaign Web组件和版本100
hide: true
hidefromtoc: true
source-git-commit: d238f0aa28289c69c91dc6a028792260708ed9f3
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# Chrome和Firefox v100对Campaign Web组件的影响 {#version-100}

Google和Mozilla警告，Chrome和Firefox由于即将推出3位版本，可能会损坏某些网站。

版本号从2位更改为3位，在访问未准备好进行此更改的网站时，可能会导致一些问题。 某些网页可能会在这些新浏览器版本中停止正确显示。

Chrome v100已设置为在 **2022年3月29日**，和Firefox v100 on **2022年5月3日**.

Mozilla和Google正在提前测试主要网站的兼容性。 如果站点在发布这些版本之前无法修复的问题，则两个站点都准备好备份计划，以确保站点不受影响。

网站上的潜在问题或功能丢失源于浏览器发送到您正在访问的网站的用户代理字符串：用户代理是由浏览器发送到网站的字符串，用于告知网站您使用的浏览器和版本以及相关技术。 当您的浏览器向网站发送请求时，它会使用用户代理字符串标识自己，然后再检索您请求的内容。 用户代理字符串中的数据可帮助网站以适合您的浏览器的格式交付内容。 用户代理的版本会递增以匹配浏览器版本号。 从2位移到3位可能会导致问题。

## 您是否受影响？{#version-100-impact}

Adobe建议您测试Campaign Web应用程序（包括Web窗体和调查），以确保它们仍然可以使用这些新浏览器版本正常工作。

此建议适用于所有Web应用程序，特别是当您已包含JavaScript代码时。

您必须同时使用Firefox和Chrome、移动和桌面进行检查。

## 如何测试？{#version-100-test}

在Chrome和Firefox中，您可以将浏览器配置为立即报告版本100，然后报告并更正您遇到的任何问题。

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

通过这些设置，浏览器会将新用户代理字符串发送到网站，这表示浏览器为Firefox 100。 如果您的Web表单存在任何问题，则应该为Mozilla创建新的错误报告。 请考虑在此更改广泛可用之前重新构建这些Web窗体。

要将用户代理更改回默认值，只需返回 `about:config` 和搜索 `general.useragent.override` 设置。  出现后，单击垃圾桶图标以删除设置，然后重新启动浏览器。

### 使用Chrome 100进行测试{#test-chrome-100}

要在您自己的Web应用程序上测试Google Chrome 100用户代理，可以通过以下步骤启用此测试：

1. 打开Chrome，输入 `chrome://flags` 在地址栏中，然后按enter。
1. 搜索 `Force major version to 100 in User-Agent` ，并将其启用，如下所示。

   ![](assets/force-user-agent-chrome.png)

1. 关闭并重新启动浏览器。
1. 关闭 `chrome://flags` 屏幕。

通过这些设置，浏览器会将新用户代理字符串发送到网站，这表示浏览器是Chrome 100。 如果您访问的网站存在任何问题，则应该为Google创建新的错误报告。 请考虑在此更改广泛可用之前重新构建这些Web窗体。

要将用户代理更改为默认代理，只需按照此过程将标志的设置更改为 `Default` 然后重新启动浏览器。
