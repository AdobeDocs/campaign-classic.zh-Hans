---
product: campaign
title: 面向业务的 API
description: 面向业务的 API
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: API
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---

# 面向业务的 API{#business-oriented-apis}

业务API特定于每种类型的对象。 它们会对以下内容产生影响：

* 投放:

   * 创建投放操作，请参阅 [SubmitDelivery (nms：delivery)](#submitdelivery--nms-delivery-)，
   * 发送营销活动（开始、暂停、停止、发送校样），
   * 恢复投放日志。

* 工作流:

   * 启动工作流，
   * 验证进程等。

      请参阅 [javascript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md).

* 内容管理
* 订阅管理，请参阅 [订阅(nms：subscription)](#subscribe--nms-subscription-) 和 [取消订阅(nms：subscription)](#unsubscribe--nms-subscription-).
* 数据过程：导入、导出。

本节详细说明了“Subscribe”、“Unsubscribe”和“SubmitDelivery”服务的使用。

>[!IMPORTANT]
>
>[Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans) 包含有关在Adobe Campaign中SOAP调用和使用Javascript的其他信息，以及对应用程序中使用的所有方法和函数的完整引用。

## 订阅(nms：subscription) {#subscribe--nms-subscription-}

此服务允许您为收件人订阅信息服务并更新收件人配置文件。

调用服务需要以下参数：

* 验证，
* 订阅服务的内部名称，
* 包含收件人信息的XML文档（来自“nms：recipient”模式），
* 用于收件人创建的布尔值（如果尚不存在）。

“nms：subscription”模式中“subscription”方法的描述：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

必须通过_输入协调键值的定义&#x200B;**键** 上的属性 `<recipient>` XML文档的元素。 此属性的内容是以逗号分隔的XPath列表。

此调用不会返回任何数据，错误除外。

### 示例 {#examples}

电子邮件地址上具有收件人协调密钥的订阅：输入XML文档必须引用此字段上的电子邮件地址和密钥定义。

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

* 响应:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## 取消订阅(nms：subscription) {#unsubscribe--nms-subscription-}

此服务允许您从信息服务中取消订阅收件人并更新收件人用户档案。

调用服务需要以下参数：

* 验证，
* 要取消订阅的服务的内部名称，
* 包含收件人信息的XML文档（来自“nms：recipient”模式），

“nms：subscription”模式中“Unsubscribe”方法的描述：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

必须通过_key属性(位于 `<recipient>` XML文档的元素。 此属性的内容是以逗号分隔的XPath列表。

如果收件人不在数据库中或未订阅有关的信息服务，该服务将不执行任何操作并且不生成错误。

>[!NOTE]
>
>阻止列表如果未将服务名称指定为参数，则收件人将在(@blackList=&quot;1&quot;)时自动收到。

此调用不会返回任何数据，错误除外。

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

响应:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms：delivery) {#submitdelivery--nms-delivery-}

此服务允许您创建和提交投放操作。

调用服务需要以下参数：

* 验证，
* 投放模板的内部名称，
* 包含其他投放数据的可选XML文档。

不应在卷中调用此API，因为您可能会遇到性能问题。

方法在其模式中的描述：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

必须从Adobe Campaign客户端控制台创建投放模板。 它包含所有投放的通用参数（发件人地址或消息的有效期）。

输入XML文档是符合“nms：delivery”模式结构的投放模板片段。 它将包含无法在投放模板中静态定义的所有附加数据（例如，要定位的收件人列表）。

此调用不会返回任何数据，错误除外。

### XML文档示例 {#xml-document-example}

此示例基于来自外部数据源的自定义投放模板（此示例中是一个文件）。 投放模板中完整描述了配置，因此当调用发生时，仅需发送以下文件中的内容： `<externalsource>` 元素。

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
