---
title: 面向业务的 API
seo-title: 面向业务的 API
description: 面向业务的 API
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 4%

---


# 面向业务的 API{#business-oriented-apis}

业务API特定于每种类型的对象。 它们对以下方面有影响：

* 投放:

   * 创建投放操作，请参 [阅SubmitDelivery(nms:投放](#submitdelivery--nms-delivery-))
   * 发送活动(开始、暂停、停止、发送验证),
   * 恢复投放日志。

* 工作流:

   * 启动工作流，
   * 验证进程等。

      请参阅 [JavaScript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md)。

* 内容管理
* 订阅管理，请 [参阅订阅(nms:订阅](#subscribe--nms-subscription-) ) [和取消订阅(nms:订阅)](#unsubscribe--nms-subscription-)。
* 数据流程：进口，出口。

本节详细介绍“订阅”、“取消订阅”和“SubmitDelivery”服务的使用。

>[!IMPORTANT]
>
>[活动JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) 包含有关SOAP调用和在Adobe Campaign中使用Javascript的其他信息，以及对应用程序中使用的所有方法和函数的完整引用。

## 订阅(nms:订阅) {#subscribe--nms-subscription-}

此服务允许您订阅收件人信息服务并更新收件人用户档案。

调用服务时需要以下参数：

* 身份验证，
* 订阅服务的内部名称，
* 包含收件人信息的XML文档(来自“nms:收件人”模式),
* 一个布尔值，用于收件人创建（如果还没有）。

“nms:订阅”模式中“subscribe”方法的描述：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

必须通过XML合并关键项元素上&#x200B;**的** _key属 `<recipient>` 性输入文档的定义。 此属性的内容是以逗号分隔的XPath列表。

除错误外，此调用不返回任何数据。

### 示例{#examples}

订阅电子邮件地址为收件人合并关键项:输入XML文档必须引用此字段中的电子邮件地址和键的定义。

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

更新收件人和订阅。

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### SOAP消息示例 {#example-of-soap-messages}

* 查询:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 响应：

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## 取消订阅(nms:订阅) {#unsubscribe--nms-subscription-}

此服务允许您取消收件人与信息服务的订阅并更新收件人用户档案。

调用服务时需要以下参数：

* 身份验证，
* 要取消订阅的服务的内部名称，
* 包含收件人信息的XML文档(来自“nms:收件人”模式),

“nms:订阅”模式中“取消订阅”方法的描述：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

必须通过XML合并关键项元素上的_key属性输 `<recipient>` 入文档的定义。 此属性的内容是以逗号分隔的XPath列表。

如果收件人不在信息服务库中，或者未订阅相关，则服务将不执行任何操作，并且不生成错误。

>[!NOTE]
>
>如果未将服务名称指定为参数，则收件人将自阻止列表动(@blackList=&quot;1&quot;)。

除错误外，此调用不返回任何数据。

### SOAP消息示例 {#example-of-soap-messages-1}

查询:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

响应：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery(nms:投放) {#submitdelivery--nms-delivery-}

此服务允许您创建和提交投放操作。

调用服务时需要以下参数：

* 身份验证，
* 投放模板的内部名称，
* 可选的XML文档，包含其他投放数据。

不应在卷中调用此API，因为您可能遇到性能问题。

方法在其模式中的描述：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

必须从投放模板客户端控制台创建Adobe Campaign。 它包含所有投放（发送者地址或消息有效期）通用的参数。

输入XML文档是符合“nms:投放”模式结构的投放模板片段。 它将包含所有无法在投放模板中静态定义的附加数据(例如，收件人到目标的列表)。

除错误外，此调用不返回任何数据。

### XML文档示例 {#xml-document-example}

此示例基于来自外部数据源（本例中为文件）的自定义投放模板。 该配置在投放模板中进行了完整的说明，因此在调用发生时仍要发送的所有内容都是元素中的文件 `<externalsource>` 内容。

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

如果您没有投放模板，可以使用以下示例：

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```

