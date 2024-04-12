---
product: campaign
title: 关于 Web 服务
description: 关于 Web 服务
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 3%

---

# 关于 Web 服务{#about-web-services}

## Adobe Campaign API的定义 {#definition-of-adobe-campaign-apis}

Adobe Campaign应用程序服务器旨在实现开放性，便于与日益多样化和复杂的公司信息系统集成。

Adobe Campaign API在应用程序内的JavaScript中以及应用程序外的SOAP中使用。 它们构成了可以扩充的通用函数库。 欲知更多信息，请参见 [实现SOAP方法](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>每天授权引擎呼叫数因您的许可合同而异。 有关详细信息，请参见[此页面](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>所有API的列表，包括其完整说明，请参见 [此专用文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html.

## 先决条件 {#prerequisites}

在使用Adobe Campaign API之前，您需要熟悉以下主题：

* JavaScript
* SOAP协议
* Adobe Campaign数据模型

## 使用Adobe Campaign API {#using-adobe-campaign-apis}

Adobe Campaign使用两种类型的API：

* 用于查询数据模型数据的通用数据访问API。 请参阅 [面向数据的API](../../configuration/using/data-oriented-apis.md).
* 允许您对每个对象执行操作的特定于业务的API：投放、工作流、订阅等。 请参阅 [面向业务的API](../../configuration/using/business-oriented-apis.md).

为了开发API并与Adobe Campaign交互，您需要熟悉您的数据模型。 Adobe Campaign允许您生成对基础的完整描述。 请参阅 [模型的描述](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP 调用 {#soap-calls}

SOAP协议允许您通过富客户端、使用Web服务的第三方应用程序或本地使用这些方法的JSP来调用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP消息的结构如下所示：

* 定义消息结构的信封，
* 可选标题，
* 包含呼叫和响应信息的正文，
* 定义错误条件的错误管理。

## 资源和交流 {#resources-and-exchanges}

以下架构显示了与使用Adobe Campaign API有关的各种资源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## &#39;ExecuteQuery&#39;方法上的SOAP消息示例 {#example-of-a-soap-message-on-the--executequery--method--}

在此示例中，SOAP查询调用“ExecuteQuery”方法，该方法将字符串作为用于身份验证（会话令牌）的参数，并将XML内容作为要执行的查询的说明。

欲知更多信息，请参见 [ExecuteQuery (xtk：queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>此服务的WSDL描述在以下示例中完成： [Web服务描述：WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP查询 {#soap-query}

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

此 `<soap-env:envelope>` 元素是表示SOAP信封的消息中的第一个元素。

此 `<soap-env:body>` 元素是信封的第一个子元素。 它包含消息的描述，即查询或响应的内容。

要调用的方法在 `<executequery>` 元素。

在SOAP中，参数按外观顺序进行识别。 第一个参数， `<__sessiontoken>`，采用身份验证链，第二个参数是来自的XML查询描述 `<querydef>` 元素。

### SOAP响应 {#soap-response}

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

查询的结果输入自 `<pdomoutput>` 元素。

## 错误管理 {#error-management}

示例SOAP错误响应：

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

此 `<soap-env:fault>` SOAP消息正文中的元素用于传递在web服务处理期间产生的错误信号。 它由以下子元素组成：

* `<faultcode>` ：指示错误类型。 错误类型包括：

   * 如果与所使用的SOAP版本不兼容，
   * “MustUnderstand”表示如果邮件标头出现问题，
   * “客户端”在客户端丢失某些信息时，
   * “服务器”（如果服务器在执行处理时遇到问题）。

* `<faultstring>` ：描述错误的消息
* `<detail>` ：长错误消息

服务调用的成功或失败在 `<faultcode>` 元素已验证。

>[!IMPORTANT]
>
>所有Adobe Campaign Web服务都会处理错误。 因此，强烈建议测试每个调用以处理返回的错误。

C#中的错误处理示例：

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

## Web服务服务器（或端点）的URL {#url-of-web-service-server--or-endpoint-}

要提交Web服务，必须联系实施相应服务方法的Adobe Campaign服务器。

服务器URL如下所示：

https://serverName/nl/jsp/soaprouter.jsp

替换为 **`<server>`** Adobe Campaign应用程序服务器(**nlserver web**)。
