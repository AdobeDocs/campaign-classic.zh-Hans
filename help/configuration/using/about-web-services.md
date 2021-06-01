---
product: campaign
title: 关于 Web 服务
description: 关于 Web 服务
audience: configuration
content-type: reference
topic-tags: api
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 4%

---

# 关于 Web 服务{#about-web-services}

## Adobe Campaign API的定义{#definition-of-adobe-campaign-apis}

Adobe Campaign应用程序服务器旨在实现与日益多样化和复杂的公司信息系统的开放和轻松集成。

Adobe Campaign API用在应用程序内的JavaScript中以及该应用程序外的SOAP中。 它们构成了可扩充的通用函数库。 有关更多信息，请参见[Implementing SOAP methods](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>每天授权的引擎呼叫次数因您的许可协议而异。 有关详细信息，请参见[此页面](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>[本专用文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中提供了所有API（包括其完整说明）的列表。

## 先决条件 {#prerequisites}

在使用Adobe Campaign API之前，您需要熟悉以下主题：

* Javascript
* SOAP协议
* Adobe Campaign数据模型

## 使用Adobe Campaign API {#using-adobe-campaign-apis}

Adobe Campaign使用两种类型的API:

* 通用数据访问用于查询数据模型数据的API。 请参阅[面向数据的API](../../configuration/using/data-oriented-apis.md)。
* 允许您对每个对象执行操作的特定于业务的API:投放、工作流、订阅等。 请参阅[面向业务的API](../../configuration/using/business-oriented-apis.md)。

要开发API并与Adobe Campaign进行交互，您需要熟悉数据模型。 Adobe Campaign允许您生成基础的完整说明。 请参阅[模型的描述](../../configuration/using/data-oriented-apis.md#description-of-the-model)。

## SOAP调用{#soap-calls}

SOAP协议允许您通过富客户端、使用Web服务的第三方应用程序或本地使用这些方法的JSP来调用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP消息的结构如下：

* 一个信封，它定义了信息的结构，
* 可选标题，
* 包含呼叫和响应信息的主体，
* 定义错误条件的错误管理。

## 资源和交换{#resources-and-exchanges}

以下架构显示了使用Adobe Campaign API时涉及的各种资源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## “ExecuteQuery”方法{#example-of-a-soap-message-on-the--executequery--method--}上的SOAP消息示例

在此示例中，SOAP查询调用“ExecuteQuery”方法，该方法将字符串作为身份验证（会话令牌）的参数，以及要执行的查询描述的XML内容。

有关更多信息，请参阅[ExecuteQuery(xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-)。

>[!NOTE]
>
>此服务的WSDL描述已完成，如下所示：[Web服务描述：WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl)。

### SOAP查询{#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

`<soap-env:envelope>`元素是表示SOAP信封的消息的第一个元素。

`<soap-env:body>`元素是信封的第一个子元素。 它包含消息的描述，即查询或响应的内容。

将在SOAP消息正文的`<executequery>`元素中输入要调用的方法。

在SOAP中，参数是按外观顺序识别的。 第一个参数`<__sessiontoken>`采用身份验证链，第二个参数是`<querydef>`元素中查询的XML描述。

### SOAP响应{#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

查询结果从`<pdomoutput>`元素中输入。

## 错误管理{#error-management}

SOAP错误响应示例：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

SOAP消息正文中的`<soap-env:fault>`元素用于传送在Web服务处理期间产生的错误信号。 这由以下子元素组成：

* `<faultcode>` :指示错误类型。错误类型包括：

   * 如果与使用的SOAP版本不兼容，则为“版本不匹配”；
   * 如果消息标头中出现问题，则为“必须了解”，
   * 如果客户端缺少某些信息，则为“客户端”
   * 如果服务器在执行处理时遇到问题，则为“服务器”。

* `<faultstring>` :描述错误的消息
* `<detail>` :长错误消息

验证`<faultcode>`元素后，将确定服务调用的成功或失败。

>[!IMPORTANT]
>
>所有Adobe Campaign Web服务都处理错误。 因此，强烈建议对每个调用进行测试，以处理返回的错误。

C#中错误处理的示例：

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## Web服务服务器（或EndPoint）{#url-of-web-service-server--or-endpoint-}的URL

要提交Web服务，必须联系实现相应服务方法的Adobe Campaign服务器。

服务器URL如下所示：

https://serverName/nl/jsp/soaprouter.jsp

使用&#x200B;**`<server>`** Adobe Campaign应用程序服务器(**nlserver web**)。
