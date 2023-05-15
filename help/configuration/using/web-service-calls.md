---
product: campaign
title: Web 服务调用
description: Web 服务调用
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: API
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 1%

---

# Web 服务调用{#web-service-calls}

## 一般信息 {#general-information}

所有API方法都以Web服务的形式呈现。 这样，您就可以通过SOAP调用(即Adobe Campaign应用程序服务器的本机入口点)管理所有Adobe Campaign函数。 Adobe Campaign控制台本身仅使用SOAP调用。

Web服务允许您从第三方系统创建许多应用程序：

* 从后台或交易系统执行同步警报、通知和实时投放模板，
* 开发具有简化功能（Web界面等）的特殊界面，
* 在遵守贸易规则并与基础物理模型保持隔离的同时，在数据库中提供和查找数据。

## Web服务的定义 {#definition-of-web-services}

在Adobe Campaign应用程序服务器上实施的Web服务的定义可从数据模式中获取。

Web服务在数据模式的语法中进行描述，可从 **`<methods>`** 元素。

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

下面我们有一个名为的方法定义示例 **GenerateForm**.

服务的描述以 `<method>` 元素。 方法的参数列表可从  `<parameters>` 元素。 每个参数都由名称、类型（布尔、字符串、DOMElement等）指定 和描述。 具有“out”值的“inout”属性允许您指定“result”参数位于SOAP调用输出中。

存在“static”属性（具有值“true”）会将此方法描述为静态，这意味着必须声明方法的所有参数。

“const”方法隐式地将XML文档作为其输入，其格式为其关联的模式。

对 `<method>` Adobe Campaign架构的元素可在 [方法](../../configuration/using/schema/method.md)

“xtk:queryDef”架构中的“const”类型“ExecuteQuery”方法示例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的输入参数是格式为“xtk:queryDef”架构的XML文档。

## Web服务描述：WSDL {#web-service-description--wsdl}

每个服务都有一个WSDL（Web服务描述库）文件。 此XML文件使用元语言来描述服务，并指定可用的方法、参数和与执行服务的服务器联系。

### WSDL文件生成 {#wsdl-file-generation}

要生成WSDL文件，必须从Web浏览器中输入以下URL:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

具有：

* **`<server>`**:Adobe Campaign应用程序服务器(nlserver web)
* **`<schema>`**:架构标识键(namespace:schema_name)

### 模式“xtk:queryDef”的“ExecuteQuery”方法示例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL文件是从URL生成的：

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

WSDL描述首先定义用于形成消息的类型，这些类型在“端口”中关联，通过“绑定”与协议连接，从而形成Web服务。

#### 类型 {#types}

类型定义基于XML架构。 在我们的示例中，“ExecuteQuery”方法采用“s:string”字符串和XML文档(`<s:complextype>`)作为参数。 方法的返回值(&quot;ExecuteQueryResponse&quot;)是XML文档(  `<s:complextype>`)。

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

#### 消息 {#messages}

的 `<message>` 描述要发送的一组字段的名称和类型。 方法使用两条消息作为参数(“ExecuteQueryIn”)和返回值(“ExecuteQueryOut”)传递。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 端口类型 {#porttype}

的 `<porttype>` 将消息与由生成响应（“输出”）的查询（“输入”）触发的“ExecuteQuery”操作关联。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 绑定 {#binding}

的 `<binding>` part指定SOAP通信协议( `<soap:binding>` )、HTTP中的数据传输（“传输”属性的值）以及“ExecuteQuery”操作的数据格式。 SOAP信封的正文直接包含消息段，而不进行转换。

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

的 `<service>` 部分介绍了“XtkQueryDef”服务及其URI在Adobe Campaign应用程序服务器URL上的情况。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 连接 {#connectivity}

Adobe Campaign通过引入 [安全区](../../installation/using/security-zones.md) 和会话管理设置。

有两种身份验证模式可用：

* **通过对logon方法()的调用**. 此模式会生成会话令牌和安全令牌。 它是最安全的模式，因此也是最推荐的模式。

或者

* **通过Adobe Campaign登录+密码** 会话令牌。 会话令牌在设置的时间段后自动过期。 不建议使用此模式，因此需要减少某些区域设置的应用程序安全设置（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）。

### 会话令牌特性 {#session-token-characteristics}

会话令牌具有以下特征：

* a X小时生命周期（生命周期可在“serverConf.xml”文件中配置，默认时间段为24小时）
* 随机结构（不再包含用户登录名和密码）
* 通过Web访问时：

   * 会话令牌将成为永久令牌，在浏览器关闭后不会销毁此令牌
   * 它位于仅HTTP Cookie中（必须为运算符激活Cookie）

### 安全令牌特性 {#security-token-characteristics}

安全令牌具有以下特征：

* 它是从会话令牌生成的
* 其生命周期为24小时（可在“serverConf.xml”文件中进行配置，默认周期为24小时）
* 它存储在Adobe Campaign控制台中
* 通过Web访问时：

   * 它存储在文档中。__securityToken属性
   * 页面URL已更新以更新安全令牌
   * 表单还通过包含令牌的隐藏字段进行更新

#### 安全令牌移动 {#security-token-movement}

通过控制台访问时，它是：

* 在登录响应中传输（在HTTP标头中）
* 在每个查询（在HTTP标头中）中使用

来自POST和GETHTTP:

* 服务器使用令牌完成链接
* 服务器向表单中添加隐藏字段

从SOAP调用中：

* 它会添加到调用头

### 调用示例 {#call-examples}

* 使用 **HttpSoapConnection/SoapService**:

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

* 使用 **HttpServletRequest**:

>[!NOTE]
>
>以下用户使用的URL **HttpServletRequest** 需要在的url权限部分允许列表 **serverConf.xml** 文件。 服务器本身的URL也是如此。

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
