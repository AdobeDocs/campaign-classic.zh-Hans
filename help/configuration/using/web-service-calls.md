---
solution: Campaign Classic
product: campaign
title: Web 服务调用
description: Web 服务调用
audience: configuration
content-type: reference
topic-tags: api
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Web 服务调用{#web-service-calls}

## 一般信息{#general-information}

所有API方法都以Web服务的形式呈现。 这使您能够通过SOAP调用管理所有Adobe Campaign函数，SOAP调用是Adobe Campaign应用程序服务器的本机入口点。 Adobe Campaign控制台本身仅使用SOAP调用。

Web服务允许您从第三方系统创建许多应用程序：

* 从后台或交易系统同步警报、通知和实时投放模板执行，
* 开发具有简化功能（Web界面等）的特殊界面，
* 在遵守贸易规则和与基础物理模型保持隔离的同时，提供和查找数据库中的数据。

## Web服务的定义{#definition-of-web-services}

在Adobe Campaign应用程序服务器上实现的Web服务的定义可从数据模式获得。

Web服务在数据模式的语法中描述，可从&#x200B;**`<methods>`**&#x200B;元素中使用。

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

这里我们有一个名为&#x200B;**GenerateForm**&#x200B;的方法定义示例。

`<method>`元素对服务开始的描述。 从`<parameters>`元素完成方法参数的列表。 每个参数都由名称、类型（Boolean、string、DOMElement等）指定 和描述。 带有“out”值的“inout”属性允许您指定“result”参数在SOAP调用输出处。

存在“static”属性（带有值“true”）将此方法描述为静态，这意味着必须声明方法的所有参数。

“const”方法隐式地具有XML文档，其格式为其关联模式作为输入。

[Method](../../configuration/using/schema/method.md)下的“Adobe Campaign引用”一章中提供了有关模式模式的`<method>`元素的完整说明

来自“xtk:queryDef”模式的“const”类型“ExecuteQuery”方法的示例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的输入参数是格式为&quot;xtk:queryDef&quot;文档的XML模式。

## Web服务描述：WSDL {#web-service-description--wsdl}

每个服务都有一个WSDL（Web服务描述库）文件。 此XML文件使用元语言描述服务并指定可用的方法、参数和要与服务器联系以执行服务。

### 生成{#wsdl-file-generation}的WSDL文件

要生成WSDL文件，必须从Web浏览器输入以下URL:

https://`<server>`/nl/jsp/schemawsdl.jsp?模式=`<schema>`

通过：

* **`<server>`**:Adobe Campaign应用程序服务器(nlserver web)
* **`<schema>`**:模式标识键(命名空间:模式_name)

### 关于模式“xtk:queryDef”{#example-on-the--executequery--method-of-schema--xtk-querydef-}的“ExecuteQuery”方法的示例

WSDL文件是从URL生成的：

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

WSDL描述开始，通过定义用于形成消息的类型（与“端口”关联），通过“绑定”与协议连接，从而形成Web服务。

#### 类型{#types}

类型定义基于XML模式。 在我们的示例中，&quot;ExecuteQuery&quot;方法采用&quot;s:string&quot;字符串和XML文档(`<s:complextype>`)作为参数。 方法的返回值(&quot;ExecuteQueryResponse&quot;)是XML文档(`<s:complextype>`)。

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### 消息{#messages}

`<message>`描述一组要发送的字段的名称和类型。 该方法使用两条消息作为参数(“ExecuteQueryIn”)和返回值(“ExecuteQueryOut”)传递。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

`<porttype>`将由生成响应(&quot;output&quot;)的查询(&quot;input&quot;)触发的“ExecuteQuery”操作的消息关联起来。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 绑定{#binding}

`<binding>`部分指定SOAP通信协议(`<soap:binding>`)、HTTP中的数据传输（“transport”属性的值）和“ExecuteQuery”操作的数据格式。 SOAP封套的正文直接包含消息段，无需转换。

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### 服务 {#service}

`<service>`部分描述“XtkQueryDef”服务，其URI位于Adobe Campaign应用程序服务器的URL上。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 连接{#connectivity}

Adobe Campaign通过引入[安全区域](../../installation/using/security-zones.md)和会话管理设置提高了身份验证机制的安全性。

有两种可用的身份验证模式：

* **通过调用logon方法()**。此模式生成会话令牌和安全令牌。 它是最安全的模式，因此是最推荐的模式。

或者

* **通过Adobe Campaign登录+** 口令创建会话令牌。会话令牌会在设置的时间段后自动过期。 不建议使用此模式，并要求降低某些区域设置（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）的应用程序安全性设置。

### 会话令牌特性{#session-token-characteristics}

会话令牌具有以下特征：

* a X小时生命周期（生命周期可在“serverConf.xml”文件中配置，默认时间为24小时）
* 随机构造（不再包含用户登录名和口令）
* 当通过Web访问时：

   * 会话令牌将成为永久令牌，一旦浏览器关闭，它不会被销毁
   * 它位于仅HTTP Cookie中（必须为运算符激活Cookie）

### 安全令牌特性{#security-token-characteristics}

安全令牌具有以下特征：

* 它是从会话令牌生成的
* 它有一个24小时的生命周期（可在“serverConf.xml”文件中配置，默认时间为24小时）
* 它存储在Adobe Campaign控制台中
* 当通过Web访问时：

   * 它存储在文档中。__securityToken属性
   * 页面URL将更新以更新安全令牌
   * 表单还通过包含令牌的隐藏字段进行更新

#### 安全令牌移动{#security-token-movement}

通过控制台访问时，它为：

* 在登录响应中传输（在HTTP头中）
* 在每个查询中使用（在HTTP头中）

来自POST和GETHTTP:

* 服务器用令牌完成链接
* 服务器向表单中添加隐藏字段

通过SOAP调用：

* 添加到呼叫头

### 调用示例{#call-examples}

* 使用&#x200B;**HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* 使用&#x200B;**HttpServletRequest**:

>[!NOTE]
>
>以下&#x200B;**HttpServletRequest**&#x200B;调用中使用的URL必须位于&#x200B;**serverConf.xml**&#x200B;文件的url权限部分的允许列表。 服务器本身的URL也是如此。

登录执行():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

查询执行：

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
