---
product: campaign
title: 面向业务的 API
description: 面向业务的 API
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 3%

---

# 面向业务的 API{#business-oriented-apis}

![](../../assets/v7-only.svg)

业务API特定于每种类型的对象。 它们会对以下内容产生影响：

* 投放:

   * 创建投放操作，请参阅[SubmitDelivery(nms:delivery)](#submitdelivery--nms-delivery-),
   * 发送营销活动（开始、暂停、停止、发送校样），
   * 恢复投放日志。

* 工作流:

   * 启动工作流，
   * 验证流程等。

      请参阅JavaScript](../../configuration/using/soap-methods-in-javascript.md)中的[SOAP方法。

* 内容管理
* 订阅管理，请参阅[订阅(nms:subscription)](#subscribe--nms-subscription-)和[退订(nms:subscription)](#unsubscribe--nms-subscription-)。
* 数据流程：进口、出口。

本节详细介绍“订阅”、“取消订阅”和“提交交付”服务的使用。

>[!IMPORTANT]
>
>[Campaign JSAPI文](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) 档包含有关Adobe Campaign中SOAP调用和使用Javascript的其他信息，以及对应用程序中使用的所有方法和函数的完整引用。

## 订阅(nms:subscription) {#subscribe--nms-subscription-}

此服务允许您向收件人订阅信息服务并更新收件人用户档案。

要调用服务，需要以下参数：

* 验证，
* 订阅服务的内部名称，
* 包含收件人信息的XML文档（来自“nms:recipient”模式），
* 一个布尔值，用于创建收件人（如果还没有）。

“nms:subscription”模式中“subscribe”方法的描述：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

协调键值的定义必须通过XML文档`<recipient>`元素上的_**key**&#x200B;属性输入。 此属性的内容是以逗号分隔的XPath列表。

除错误外，此调用不返回任何数据。

### 示例 {#examples}

在电子邮件地址上订阅收件人协调密钥：输入XML文档必须引用此字段中的电子邮件地址和键的定义。

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

## 取消订阅(nms:subscription) {#unsubscribe--nms-subscription-}

此服务允许您使收件人从信息服务中取消订阅并更新收件人用户档案。

要调用服务，需要以下参数：

* 验证，
* 要取消订阅的服务的内部名称，
* 包含收件人信息的XML文档（来自“nms:recipient”模式），

“nms:subscription”模式中“取消订阅”方法的描述：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

协调键值的定义必须通过XML文档`<recipient>`元素上的_key属性输入。 此属性的内容是以逗号分隔的XPath列表。

如果收件人不在数据库中或者没有订阅相关信息服务，则该服务不执行任何操作并且不产生错误。

>[!NOTE]
>
>如果未将服务名称指定为参数，则收件人随后将在阻止列表时自动(@blackList=&quot;1&quot;)。

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

## SubmitDelivery(nms:delivery) {#submitdelivery--nms-delivery-}

此服务允许您创建和提交投放操作。

要调用服务，需要以下参数：

* 验证，
* 投放模板的内部名称，
* 可选的XML文档，其中包含其他提交数据。

您可能遇到性能问题，因此不应在卷中调用此API。

其模式中方法的描述：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

必须从Adobe Campaign客户端控制台创建投放模板。 它包含所有投放通用的参数（发件人地址或消息有效期）。

输入XML文档是遵循“nms:delivery”模式结构的投放模板片段。 它将包含无法在投放模板中静态定义的所有其他数据（例如，要定位的收件人列表）。

除错误外，此调用不返回任何数据。

### XML文档示例 {#xml-document-example}

此示例基于来自外部数据源（本例中为文件）的自定义投放模板。 投放模板中对配置进行了完整描述，因此在调用发生时，所有仍要发送的内容都是`<externalsource>`元素中的文件内容。

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

如果您没有投放模板，则可以使用以下示例：

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
