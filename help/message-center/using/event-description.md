---
title: 事件描述
seo-title: 事件描述
description: 事件描述
seo-description: null
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 1%

---


# 事件描述{#event-description}

## 关于事务消息传递数据模型 {#about-transactional-messaging-datamodel}

事务消息传递依赖于Adobe Campaign数据模型，并使用两个额外的单独表。 这 [些表](../../configuration/using/data-model-description.md#message-center-module)(NmsRtEvent **** 和NmsBatchEvent ****)包含相同的字段，并允许您管理实时事件和批次事件。

## SOAP方法 {#soap-methods}

本节详细介绍与事务性消息模块模式关联的SOAP方法。

两 **个PushEvent** 或 **PushEvents** SOAP方法链接到两 **个nms:rtEvent** 和 **** nms:EventDataschemas。 它是决定事件是“批”还是“实时”类型的信息系统。

* **PushEvent** 允许您在消息中插入单个事件,
* **PushEvents** 允许您在消息中插入一系列事件。

访问这两种方法的WSDL路径为：

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** 访问实时类型模式。
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** ，以访问批处理类型模式。

这两种方法都包 **`<urn:sessiontoken>`** 含用于登录到事务消息模块的元素。 我们建议通过可信IP地址使用标识方法。 要检索会话令牌，请执行登录SOAP调用，然后执行获取令牌和注销。 对多个RT调用使用相同的令牌。 本节中包括的示例使用的是建议的会话令牌方法。

如果您使用的是负载平衡服务器，则可以使用用户／密码身份验证（在RT消息级别）。 示例:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

PushEvent **方法** ，由包含该 **`<urn:domevent>`** 事件的参数组成。

PushEvents **方法** ，由包含事件 **`<urn:domeventcollection>`** 的参数组成。

使用PushEvent的示例：

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>如果调用PushEvents方 **法** ，我们需要添加一个父XML元素以符合标准XML。 此XML元素将框架事件中 **`<rtevent>`** 包含的各种元素。

使用PushEvents的示例：

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

和 **`<rtevent>`** 元 **`<batchevent>`** 素具有一组属性以及一个必需的子元素： **`<ctx>`** 用于集成消息数据。

>[!NOTE]
>
>元 **`<batchevent>`** 素允许您将事件添加到“批处理”队列。 将 **`<rtevent>`** 事件添加到“实时”队列。

这些和元素的必 **`<rtevent>`** 需 **`<batchevent>`** 属性是@type和@email。 @type的值必须与配置列表时定义的分项执行实例值相同。 此值允许您定义要在投放期间链接到事件内容的模板。

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

在此示例中，提供了两个渠道:电子邮件地址和手机号码。 The **** wishedChannel允许您选择将渠道转换为消息时要使用的事件。 “0”值对应于电子邮件渠道、“1”值对应于移动渠道等。

如果要推迟事件投放，请添加 **[!UICONTROL scheduled]** 字段，后跟首选日期。 事件将在此日期转换为消息。

我们建议用数字值填写@whishedChannel和@emailFormat属性。 链接数值和标签的函数表在数据模式说明中。

>[!NOTE]
>
>在nms:rtEvent和nms:BatchEvent数据架构的描述中，可以详细描述 **所有授权属性****及其值** 。

元素 **`<ctx>`** 包含消息数据。 其XML内容是打开的，这意味着可以根据要传送的内容对其进行配置。

>[!NOTE]
>
>优化消息中包含的XML节点数和大小，以避免在投放期间超载服务器。

数据示例：

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
   
```

## SOAP调用返回的信息 {#information-returned-by-the-soap-call}

当Adobe Campaign收到事件时，其生成唯一返回ID。 这是事件的存档版本的ID。

>[!IMPORTANT]
>
>在接收SOAP调用时，Adobe Campaign验证电子邮件地址格式。 如果电子邮件地址格式不正确，则返回错误。

* 事件处理成功时，方法返回的标识符示例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

如果返回标识符的值严格大于零，则表示事件已以Adobe Campaign成功存档。

但是，如果事件无法处理，该方法将返回错误消息或等于零的值。

* 处理事件示例，当查询不包含登录名或指定的运算符没有所需权限时失败：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 由于事件中的错误而失败的查询示例（XML分类未得到遵守）:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 失败并返回零标识符的事件示例（方法名称错误）:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

