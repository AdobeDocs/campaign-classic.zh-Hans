---
solution: Campaign Classic
product: campaign
title: 生成个性化内容
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 6%

---


# 生成个性化内容 {#build-personalized-content}

在设计消息内容时，请尝试避免可能妨碍您执行投放的常见问题。 大多数时间中，可能的错误与[个性化](../../delivery/using/about-personalization.md)、[格式化](../../delivery/using/defining-the-email-content.md#message-content)和[图像](../../delivery/using/defining-the-email-content.md#adding-images)有关。

## 优化个性化{#optimize-personalization}

为避免可能妨碍您执行投放并改善收件人体验的常见问题，Adobe Campaign使您能够个性化您的信息。

您可以使用存储在Adobe Campaign数据库中或通过跟踪、登陆页、订阅等收集的收件人数据。
在[本节](../../delivery/using/personalization-fields.md)中介绍了个性化基础知识。

确保您的消息内容设计得当，以避免任何与个性化通常相关的错误。

**提示**:在来自第三方供应商提供的外部文件的个性化字段中，外部HTML内容可能出错。要避免这种情况，请检查语法、使用标记、字符等。 例如，Adobe Campaign个性化标签始终具有以下表单：&lt;%=table.field%>。 有关更多信息，请参阅[此章节](../../delivery/using/about-personalization.md)。

在个性化块中使用参数不正确可能是个问题。 例如，JavaScript中的变量应使用如下：

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
有关个性化块的详细信息，请参阅[此部分](../../delivery/using/personalization-blocks.md)。

您可以在工作流中准备个性化数据，以改进投放准备分析。 如果个性化数据是通过联合数据访问(联合数据访问)从外部表格提供的，则应特别使用此选项。 此选项在此[中有说明](../../delivery/using/personalization-fields.md#optimizing-personalization)

## 构建优化内容{#optimize-content}

在构建电子邮件时，请牢记以下一般最佳实践。

* 使设计变得简单

* 让移动用户牢记

* 避免完全基于图像的电子邮件

* 使用电子邮件安全字体

* 对特殊字符进行编码

### 主题行

在[主题行](../../delivery/using/defining-the-email-content.md#message-content)上工作以提高开放率：

* 避开过长的对象。 最多使用50个字符

* 避免重复使用“free”或“优惠”等可能被视为垃圾邮件的词语

* 避免大写字母和特殊字符，如&quot;!&quot;、&quot;£&quot;、&quot;€&quot;、&quot;$&quot;

### 镜像页面

始终包含镜像页面链接。 首选职位是电子邮件的顶部。 [了解详情](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### 退订链接

退订链接至关重要。 它必须可见且有效，并且表单必须能够正常工作。 默认情况下，在分析消息时，[类型规则](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)会检查是否已包含退出链接，并在消息缺失时生成警告。

**提示**:由于人为错误总是可能发生，因此在每次发送之前，请检查退出链接是否工作正常。例如，在发送验证时，请确保链接有效、表单联机且“不再与此收件人联系”字段更改为“是”。

了解如何在本节](../../delivery/using/personalization-blocks.md#personalization-blocks-example)中插入退出链接[。

### 电子邮件大小

为避免性能或交付性问题，建议电子邮件的最大大小约为&#x200B;**35KB**。 要检查消息大小，请转到&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，然后选择测试用户档案。 生成后，消息大小将显示在右上角。

要限制您的电子邮件，请考虑以下事项：

* 删除冗余或未使用的样式

* 将部分电子邮件内容移动到登陆页

* 简化代码

确保在最终发送之前测试所有更改

### SMS长度

默认情况下，短信的字符数应符合 GSM（全球移动通信系统）标准。使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

音译指的是，如果 GSM 标准无法识别某个短信字符，则会用另一个字符替换该字符。请注意，在SMS消息的内容中插入个性化字段可能会引入GSM编码未考虑的字符。 您可以通过选中相应&#x200B;**[!UICONTROL External account]**的SMPP渠道设置选项卡中的相应框来授权字符音译。
请阅读本节](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)了解更多信息。[

**提示**:

* 要保留SMS消息中所有字符的原样，例如，不要更改正确的名称，请不要启用音译。

* 但是，如果您的SMS消息包含许多GSM标准未考虑的字符，则允许音译以限制发送消息的成本。

请阅读本节](../../delivery/using/sms-channel.md#about-character-transliteration)了解更多信息。[

## 处理格式设置{#formatting}

要避免常见格式错误，请检查以下元素：

* 更正&#x200B;**日期格式**:Adobe Campaign为JavaScript模板和XSL样式表提供日期格式化功能。 [了解详情](../../delivery/using/formatting.md#date-display)

* 在电子邮件中使用&#x200B;**授权字符**:电子邮件地址的有效字符列表在“XtkEmail_Characters”选项中定义。 了解如何访问本节](../../installation/using/configuring-campaign-options.md)中的活动选项[。 要正确处理特殊字符，需要在Unicode中安装Adobe Campaign。

* **电子邮件身份验证**&#x200B;的配置：确保电子邮件标头包含DKIM签名。 DKIM（域密钥标识邮件）身份验证允许接收电子邮件服务器验证消息确实是由其声称其发送消息的个人或实体发送的，以及消息内容在最初发送（和DKIM“签名”）和接收时间之间是否发生了更改。 此标准通常使用“发件人”或“发件人”标题中的域。 有关详细信息，请参阅[《Adobe交付能力最佳实践指南》](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 响应式电子邮件设计

响应式设计可确保电子邮件能够针对打开电子邮件的设备进行最佳呈现。

* 使用响应式电子邮件HTML而非Web HTML

* 使用预览模式并发送验证，以在尽可能多的设备上测试渲染

* Adobe Campaign Classic数字内容编辑器(数字内容编辑器)模块包括一些响应式设计格式模板，可通过&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**&#x200B;获得。 请阅读本文](https://theblog.adobe.com/responsive-email-design-101/)，了解更多[

## 管理映像{#manage-images}

在使用图像时，请遵循以下准则。

### 防止图像阻塞

默认情况下，某些电子邮件客户端会阻止图像，而一些用户会更改其设置以阻止图像以保存数据使用情况。 因此，如果不下载图像，则会丢失整个消息。 要避免这种情况：

* 在内容与图像和文本之间取得平衡。 避免完全基于图像的电子邮件。

* 如果图像中必须包含文本，请使用alt和title文本来确保消息传递过来。 设置替代/标题文本的样式以改进其外观。

* 避免使用背景图像，因为某些电子邮件客户不支持这些图像。

### 使图像具有响应性

尝试使图像具有响应性和可调整大小。 请注意，这可能会因构建时间过长而产生成本影响。

### 使用绝对图像引用

要从外部访问，链接到活动的电子邮件和公共资源中使用的图像必须存在于可从外部访问的服务器上。

* 您可以检查实例配置是否启用公共资源管理。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 在该投放向导中，可以通过&#x200B;**[!UICONTROL Image]**&#x200B;图标直接使用HTML编辑器导入包含图像的HTML页面或插入图像。 [了解详情](../../delivery/using/defining-the-email-content.md#adding-images)

* 如果未显示图像，请检查服务器上是否提供了这些图像。 要执行此操作，请单击投放中的“源”选项卡。 在Web浏览器中查找图像并复制粘贴每个图像的URL。 如果未显示图像，请与IT管理员或提供投放内容的第三方供应商联系。

## 预览消息{#preview-msg}

Adobe建议预览您的消息，以检查其个性化以及收件人如何看到您的投放。

* 在投放向导中，**[!UICONTROL Preview]**&#x200B;子选项卡允许您视图收件人中每个内容的呈现。 个性化字段和内容的条件元素被替换为所选用户档案的相应信息。 [了解详情](../../delivery/using/defining-the-email-content.md#message-content)

* 在每个预览期间执行自动防垃圾邮件检查。 在&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡中，检查[SpamAssassin](../../delivery/using/spamassassin.md)垃圾邮件评分。  单击&#x200B;**[!UICONTROL More...]**&#x200B;以进一步了解警告。  在执行此操作之前，请确保在Adobe Campaign应用程序服务器上正确安装和配置了SpamAssan。 [了解详情](../../installation/using/configuring-spamassassin.md)
