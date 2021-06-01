---
product: campaign
title: 生成个性化内容
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 6%

---

# 生成个性化内容 {#build-personalized-content}

在设计消息内容时，请尽量避免可能阻止您执行投放的常见问题。 大多数情况下，可能的错误与[个性化](../../delivery/using/about-personalization.md)、[格式化](../../delivery/using/defining-the-email-content.md#message-content)和[图像](../../delivery/using/defining-the-email-content.md#adding-images)有关。

## 优化个性化{#optimize-personalization}

为避免可能阻止您执行投放并改善收件人体验的常见问题，Adobe Campaign允许您个性化邮件。

您可以使用存储在Adobe Campaign数据库中的收件人数据，或通过跟踪、登陆页、订阅等方式收集的数据。
[此部分](../../delivery/using/personalization-fields.md)中介绍了个性化基础知识。

确保您的消息内容设计正确，以避免任何与个性化通常相关的错误。

**提示**:在来自第三方供应商提供的外部文件的个性化字段中，外部HTML内容可能会出错。要避免出现这种情况，请检查语法、标记的使用、字符等。 例如，Adobe Campaign个性化标记始终具有以下表单：&lt;%=table.field%>。 有关更多信息，请参阅[此章节](../../delivery/using/about-personalization.md)。

个性化块中参数的使用不正确可能是一个问题。 例如，JavaScript中的变量应按如下方式使用：

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
有关个性化块的更多信息，请参阅[此部分](../../delivery/using/personalization-blocks.md)。

您可以在工作流中准备个性化数据，以改进投放准备分析。 如果个性化数据通过联合数据访问(FDA)从外部表中获取，则应特别使用此功能。 此[此部分](../../delivery/using/personalization-fields.md#optimizing-personalization)中介绍了此选项

## 构建优化内容{#optimize-content}

在构建电子邮件时，请牢记以下一般最佳实践。

* 保持设计简单

* 请记住移动设备用户

* 避免完全基于图像的电子邮件

* 使用电子邮件安全字体

* 编码特殊字符

### 主题行

使用[主题行](../../delivery/using/defining-the-email-content.md#message-content)提高打开率：

* 避免话题太长。 最多使用50个字符

* 避免重复使用诸如“free”或“offer”之类的词语，这些词语可能会被视为垃圾邮件

* 避免使用大写字母和特殊字符，如“！”、“£”、“€”、“$”

### 镜像页面

始终包含镜像页面链接。 首选位置是电子邮件的顶部。 [了解详情](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### 退订链接

退订链接至关重要。 它必须可见且有效，并且表单必须有效。 默认情况下，分析消息时， [分类规则](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)会检查是否包含选择退订链接，并在缺少该链接时生成警告。

**提示**:由于始终可能出现人为错误，因此请在每次发送之前检查选择退出链接是否正常工作。例如，在发送校样时，请确保链接有效、表单已联机且“No lent contact this recipient（不再与此收件人联系）”字段已更改为“Yes（是）”。

了解如何在此部分](../../delivery/using/personalization-blocks.md#personalization-blocks-example)中插入选择退出链接[。

### 电子邮件大小

为避免出现性能或投放能力问题，建议电子邮件的最大大小约为&#x200B;**35KB**。 要检查消息大小，请转到&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，然后选择测试用户档案。 生成后，消息大小将显示在右上角。

要限制您的电子邮件，请考虑以下事项：

* 删除冗余或未使用的样式

* 将一些电子邮件内容移到登陆页面

* 缩小代码

确保在最终发送之前测试任何更改

### 短信长度

默认情况下，短信的字符数应符合 GSM（全球移动通信系统）标准。使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

音译指的是，如果 GSM 标准无法识别某个短信字符，则会用另一个字符替换该字符。请注意，在短信消息内容中插入个性化字段可能会引入GSM编码无法识别的字符。 您可以通过选中相应&#x200B;**[!UICONTROL External account]**的SMPP渠道设置选项卡中的相应框来授权字符音译。
在此部分](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)中了解更多[信息。

**提示**:

* 若要将短信消息中的所有字符按原样保留，请不要更改正确的名称（例如），请勿启用音译。

* 但是，如果短信消息包含大量GSM标准未考虑的字符，则启用音译可限制发送消息的成本。

在此部分](../../delivery/using/sms-set-up.md#about-character-transliteration)中了解更多[信息。

## 处理格式 {#formatting}

要避免出现常见的格式错误，请检查以下元素：

* 更正&#x200B;**日期格式**:Adobe Campaign为JavaScript模板和XSL样式表提供日期格式设置函数。 [了解详情](../../delivery/using/formatting.md#date-display)

* 电子邮件中&#x200B;**授权字符**&#x200B;的用法：电子邮件地址的有效字符列表在“XtkEmail_Characters”选项中定义。 了解如何访问此部分](../../installation/using/configuring-campaign-options.md)中的Campaign选项[。 要正确处理特殊字符，需要以Unicode安装Adobe Campaign。

* **电子邮件身份验证**&#x200B;的配置：确保电子邮件标头包含DKIM签名。 通过DKIM（域名密钥识别邮件）身份验证，接收电子邮件服务器可以验证消息是否确实是由其声称由其发送的个人或实体发送的，以及消息内容是否在最初发送（和DKIM“签名”）与收到之间发生更改。 此标准通常使用“发件人”或“发件人”标题中的域。 有关更多信息，请参阅[Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 响应式电子邮件设计

响应式设计可确保电子邮件在打开时能够以最佳方式呈现。

* 使用响应式电子邮件HTML，而不是Web HTML

* 使用预览模式并发送校样，以尽可能多地在设备上测试渲染效果

* Adobe Campaign Classic数字内容编辑器(DCE)模块包含一些响应式设计格式化的模板，可用于通过&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**&#x200B;获取的移动设备。 在本文](https://theblog.adobe.com/responsive-email-design-101/)中了解更多[信息

## 管理映像{#manage-images}

在使用图像时，请遵循以下准则。

### 防止图像阻塞

默认情况下，某些电子邮件客户端会阻止图像，而某些用户会更改其设置以阻止图像，以便保存数据。 因此，如果不下载图像，则整个消息可能会丢失。 要避免出现这种情况，请执行以下操作：

* 在内容与图像和文本之间取得平衡。 避免完全基于图像的电子邮件。

* 如果图像中必须包含文本，请使用替换文本和标题文本，以确保消息能够被传递。 设置替换/标题文本的样式以改进其外观。

* 避免使用背景图像，因为某些电子邮件客户不支持这些图像。

### 使图像具有响应性

尝试使图像具有响应性和可调整大小。 请注意，这可能会对成本产生影响，因为构建过程需要较长时间。

### 使用绝对图像引用

要从外部访问，链接到营销活动的电子邮件和公共资源中使用的图像必须显示在可从外部访问的服务器上。

* 您可以检查实例配置是否启用公共资源管理。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 在投放向导中，您可以导入包含图像的HTML页面，或通过&#x200B;**[!UICONTROL Image]**&#x200B;图标使用HTML编辑器直接插入图像。 [了解详情](../../delivery/using/defining-the-email-content.md#adding-images)

* 如果未显示图像，请检查这些图像是否在服务器上可用。 要实现此目的，请单击投放中的源选项卡。 在Web浏览器中查找您的图像并复制粘贴每个图像的URL。 如果未显示图像，请与IT管理员或提供投放内容的第三方供应商联系。

## 预览消息{#preview-msg}

Adobe建议预览消息以检查其个性化以及收件人将如何看到您的投放。

* 在投放向导中，使用&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡可以查看收件人的每个内容的渲染。 个性化字段和内容的条件元素将替换为选定用户档案的相应信息。 [了解详情](../../delivery/using/defining-the-email-content.md#message-content)

* 在每次预览期间执行自动防垃圾邮件检查。 在&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡中，检查[SpamAssassin](../../delivery/using/spamassassin.md)垃圾信息评分。  单击&#x200B;**[!UICONTROL More...]**&#x200B;以详细了解警告。  在执行此操作之前，请确保在Adobe Campaign应用程序服务器上正确安装和配置了SpamAssassin。 [了解详情](../../installation/using/configuring-spamassassin.md)
