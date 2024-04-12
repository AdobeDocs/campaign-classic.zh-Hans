---
product: campaign
title: 生成个性化内容
description: 了解如何在Adobe Campaign投放中构建个性化内容
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 4%

---

# 生成个性化内容 {#build-personalized-content}

在设计消息内容时，请尽量避免可能会阻止您执行投放的常见问题。 大多数情况下，可能的错误与 [个性化](about-personalization.md)， [格式化](defining-the-email-content.md#message-content) 和 [图像](defining-the-email-content.md#adding-images).

## 优化个性化 {#optimize-personalization}

为避免可能阻止您执行投放的常见问题并改善收件人体验，Adobe Campaign允许您个性化消息。

您可以使用存储在Adobe Campaign数据库中的收件人数据，或通过跟踪、登陆页面、订阅等收集的数据。
中介绍了个性化基础知识 [本节](personalization-fields.md).

确保消息内容设计正确，以避免出现任何错误，这些错误通常与个性化相关。

**提示**：在来自第三方供应商提供的外部文件的个性化字段中，外部HTML内容可能有误。 要避免此问题，请检查语法、标记的使用和字符等。 例如，Adobe Campaign个性化标记始终具有以下形式： &lt;%=table.field%>。 有关更多信息，请参阅[此小节](about-personalization.md)。

在个性化块中错误使用参数可能是个问题。 例如，JavaScript中的变量应按以下方式使用：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

有关个性化块的更多信息，请参阅 [本节](personalization-blocks.md).

您可以在工作流中准备个性化数据，以改进投放准备分析。 如果个性化数据来自通过联合数据访问(FDA)的外部表，则应当特别使用此字段。 该选项在此进行说明 [本节](personalization-fields.md#optimizing-personalization)

## 构建优化内容 {#optimize-content}

在构建电子邮件时，请牢记以下一般最佳实践。

* 保持设计简单

* 请牢记移动用户

* 避免完全基于图像的电子邮件

* 使用电子邮件安全字体

* 编码特殊字符

### 主题行

处理 [主题行](defining-the-email-content.md#message-content) 要提高开放率，请执行以下操作：

* 避免使用过长的主题。 最多使用50个字符

* 避免使用可被视为垃圾邮件的重复单词，如“free”或“offer”

* 避免使用大写字母和特殊字符，如“！”、“£”、“€”、“$”

### 镜像页面

始终包含镜像页面链接。 首选位置是电子邮件的顶部。 [了解详情](sending-messages.md#generating-the-mirror-page)

### 退订链接

退订链接是必需的。 它必须可见且有效，并且表单必须有效。 默认情况下，分析消息时， [类型规则](steps-validating-the-delivery.md#validation-process-with-typologies) 检查是否包含选择退出链接，如果缺少该链接，则生成警告。

**提示**：由于始终可能存在人为错误，因此请在每次发送前检查选择退出链接是否正常工作。 例如，在发送校样时，确保链接有效，表单处于联机状态且“不再联系此收件人”字段已更改为“是”。

了解如何插入选择退出链接 [在此部分中](personalization-blocks.md#personalization-blocks-example).

### 电子邮件大小

为了避免出现性能或可投放性问题，建议的最大电子邮件大小约为 **35KB**. 要检查邮件大小，请转到 **[!UICONTROL Preview]** 选项卡并选择测试配置文件。 生成后，消息大小将显示在右上角。

要将电子邮件保持在限制以内，请考虑以下事项：

* 删除多余或未使用的样式

* 将部分电子邮件内容移至登陆页面

* 缩小代码

确保在最终发送之前测试任何更改

### 短信长度

默认情况下，短信的字符数应符合GSM（全球移动通信系统）标准。 使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

音译指的是，如果GSM标准无法识别某个短信字符，则会用另一个字符替换该字符。 请注意，将个性化字段插入短信消息内容，可能会引入GSM编码无法识别的字符。 您可以通过选中对应的 **[!UICONTROL External account]**.
了解详情 [在此部分中](sms-set-up.md#creating-an-smpp-external-account).

**提示**：

* 要将短信消息中的所有字符都保持不变，例如不要更改正确名称，请不要启用音译。

* 但是，如果短信消息包含许多GSM标准无法识别的字符，请启用音译以限制发送消息的成本。

了解详情 [在此部分中](sms-set-up.md#about-character-transliteration).

## 处理格式设置 {#formatting}

要避免常见的格式错误，请检查以下元素：

* 正确 **日期格式**：Adobe Campaign为JavaScript模板和XSL样式表提供日期格式功能。 [了解详情](formatting.md#date-display)

* 使用 **授权字符** 在电子邮件中：电子邮件地址的有效字符列表在“XtkEmail_Characters”选项中定义。 了解如何访问Campaign选项 [在此部分中](../../installation/using/configuring-campaign-options.md). 要正确处理特殊字符，需要使用Unicode安装Adobe Campaign。

* 配置 **电子邮件身份验证**：确保电子邮件标头包含DKIM签名。 通过DKIM（域密钥识别邮件）身份验证，接收电子邮件服务器可以验证邮件确实是由其声明发送该邮件的个人或实体发送的，以及邮件内容在最初发送（和DKIM“签名”）与接收之间是否发生了更改。 此标准通常使用发件人或发件人标头中的域。 有关详细信息，请参见 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 响应式电子邮件设计

响应式设计可确保电子邮件以最佳方式呈现给打开它的设备。

* 使用响应式电子邮件HTML而不是WebHTML

* 使用预览模式和发送校样以尽可能多的在设备上测试渲染

* Adobe Campaign Classic数字内容编辑器(DCE)模块包括一些用于移动设备的响应式设计格式化模板，可通过以下方式获取 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. 了解详情 [本文内容](https://theblog.adobe.com/responsive-email-design-101/)

## 管理图像 {#manage-images}

在使用图像时，请遵循以下准则。

### 防止图像阻塞

默认情况下，某些电子邮件客户端会阻止图像，而某些用户会更改其设置以阻止图像以供在数据使用时保存。 因此，如果不下载图像，则可能会丢失整个消息。 要避免这种情况：

* 使您的内容与图像和文本保持平衡。 避免完全基于图像的电子邮件。

* 如果文本必须包含在图像中，请使用替换文本和标题文本以确保消息正确传递。 设置替代/标题文本的样式以改进其外观。

* 避免使用背景图像，因为某些电子邮件客户端不支持这些图像。

### 使图像具有响应性

尝试使图像具有响应性且可调整大小。 请注意，这可能会产生成本影响，因为构建所需的时间较长。

### 使用绝对图像引用

要从外部访问，必须在外部可访问的服务器上存在电子邮件中使用的图像以及与营销活动关联的公共资源。

* 您可以检查实例配置是否启用公共资源管理。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 在投放向导中，您可以通过，导入包含图像的HTML页面或直接使用HTML编辑器插入图像 **[!UICONTROL Image]** 图标。 [了解详情](defining-the-email-content.md#adding-images)

* 如果未显示图像，请检查图像在服务器上是否可用。 要实现此目的，请单击投放中的“源”选项卡。 在Web浏览器中查找图像并复制粘贴每个图像的URL。 如果未显示图像，请联系您的IT管理员或提供投放内容的第三方供应商。

## 预览消息 {#preview-msg}

Adobe建议预览您的消息以检查其个性化设置以及收件人如何看到您的投放。

* 在投放向导中， **[!UICONTROL Preview]** 通过子选项卡，可以查看收件人的每个内容的呈现。 将内容的个性化字段和条件元素替换为所选用户档案的相应信息。 [了解详情](defining-the-email-content.md#message-content)

* 在每次预览期间执行自动反垃圾邮件检查。 在 **[!UICONTROL Preview]** 子选项卡，选中 [SpamAssassin](spamassassin.md) 垃圾邮件评分。  单击 **[!UICONTROL More...]** 了解关于警告的更多信息。  在执行此操作之前，请确保已在Adobe Campaign应用程序服务器上正确安装和配置SpamAssassin。 [了解详情](../../installation/using/configuring-spamassassin.md)
