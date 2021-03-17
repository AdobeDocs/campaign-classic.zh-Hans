---
solution: Campaign Classic
product: campaign
title: 配置安全区域
description: 了解如何配置安全区域
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# 定义安全区域{#defining-security-zones}

每个操作员需要链接到一个区域才能登录到实例，并且操作员IP必须包含在安全区域中定义的地址或地址集中。 安全区配置在Adobe Campaign服务器的配置文件中执行。

操作符从控制台（**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点）中的用户档案链接到安全区域。 了解如何将区域链接到[本节](#linking-a-security-zone-to-an-operator)中的活动运算符。

## 创建安全区域{#creating-security-zones}

区域由以下对象定义：

* 一个或多个IP地址范围（IPv4和IPv6）
* 链接到各种IP地址的技术名称

安全区域是互锁的，这意味着在另一个区域内定义新区域会减少可以登录到它的运算符数量，同时增加分配给每个运算符的权限。

在服务器配置过程中，必须在&#x200B;**serverConf.xml**&#x200B;文件中定义区域。 **serverConf.xml**&#x200B;中可用的所有参数均列在[此部分](../../installation/using/the-server-configuration-file.md)中。

每个区域定义权限，如：

* HTTP连接而非HTTPS
* 错误显示（Java错误、JavaScript、C++等）
* 报告和webApp预览
* 通过登录名/密码进行身份验证
* 非安全连接模式

>[!NOTE]
>
>**每个运算符都必须链接到区域**。如果操作员的IP地址属于区域定义的范围，则操作员可以登录到实例。\
>操作员的IP地址可以在多个区域中定义。 在这种情况下，操作员接收每个区域的可用权限的&#x200B;**set**。

现成的&#x200B;**serverConf.xml**&#x200B;文件包括三个区域：**public、VPN和LAN**。

>[!NOTE]
>
>**开箱即用的配置是安全的**。但是，在从较早版本的Adobe Campaign迁移之前，可能需要暂时降低安全性，以便迁移和批准新规则。

如何在&#x200B;**serverConf.xml**&#x200B;文件中定义区域的示例：

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

定义区域的所有权利如下：

* **allowDebug**:允许在“调试”模式下执行webApp
* **allowEmptyPassword**:授权与实例的连接时不使用密码
* **allowHTTP**:无需使用HTTPS协议即可创建会话
* **allowUserPassword**:会话令牌可以具有以下格式“`<login>/<password>`”
* **sessionTokenOnly**:连接URL中不需要安全令牌
* **showErrors**:转发并显示服务器端的错误

>[!IMPORTANT]
>
>在区域定义中，每个具有&#x200B;**true**&#x200B;值的属性都会降低安全性。

使用消息中心时，如果有多个执行实例，则需要使用定义为&#x200B;**true**&#x200B;的&#x200B;**sessionTokenOnly**&#x200B;属性创建额外的安全区域，其中只需添加必要的IP地址。 有关配置实例的详细信息，请参阅[此文档](../../message-center/using/creating-a-shared-connection.md)。

## 安全区域{#best-practices-for-security-zones}的最佳实践

在&#x200B;**lan**&#x200B;安全区的定义中，可以添加定义技术访问的IP地址掩码。 此添加将允许访问服务器上托管的所有实例。

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

我们建议仅在访问特定实例的操作员专用的配置文件中直接定义IP地址范围。

在&#x200B;**`config-<instance>.xml`**&#x200B;文件中：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全区域{#sub-networks-and-proxies-in-a-security-zone}中的子网络和代理

**proxy**&#x200B;参数可用于&#x200B;**subNetwork**&#x200B;元素中，以指定在安全区中的代理使用。

当引用代理并且连接通过此代理进入时（通过HTTP X-Forwarded-For头可见），验证区域是代理客户端，而不是代理客户端。

>[!IMPORTANT]
>
>如果配置了代理，并且可以覆盖它（或者如果不存在），则将测试的IP地址将能够被伪造。
>
>此外，中继现在也像代理一样生成。 因此，您可以将IP地址127.0.0.1添加到安全区域配置中的代理列表。
>
>例如：&quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;。

可能会出现多种情况：

* 子网络在安全区域中直接引用，未配置代理：子网络的用户可以直接连接到Adobe Campaign服务器。

   ![](assets/8101_proxy1.png)

* 为安全区域中的子网络指定代理：来自此子网络的用户可以通过此代理访问Adobe Campaign服务器。

   ![](assets/8101_proxy2.png)

* 代理包含在安全区子网络中：有权通过此代理访问的用户，无论其来源如何，都可以访问Adobe Campaign服务器。

   ![](assets/8101_proxy3.png)

可能访问Adobe Campaign服务器的代理的IP地址必须在相关的&#x200B;**`<subnetwork>`**&#x200B;和一级子网络&#x200B;**`<subnetwork name="all"/>`**&#x200B;中输入。 例如，下面是IP地址为10.131.146.102的代理：

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## 将安全区域链接到运算符{#linking-a-security-zone-to-an-operator}

定义区域后，必须将每个操作员链接到其中一个操作员才能登录到实例，并且该操作员的IP地址必须包含在区域中引用的地址或地址范围中。

区域的技术配置在活动服务器的配置文件中执行：**serverConf.xml**。

在此之前，您必须通过配置现成的&#x200B;**[!UICONTROL Security zone]**&#x200B;明细列表来开始，以便将标签链接到&#x200B;**serverConf.xml**&#x200B;文件中定义的区域的内部名称。

此配置在活动资源管理器中完成：

1. 单击&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;节点。
1. 选择&#x200B;**[!UICONTROL Security zone (securityZone)]**&#x200B;系统明细列表。

   ![](assets/enum_securityzone.png)

1. 对于在服务器配置文件中定义的每个安全区域，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Internal name]**&#x200B;字段中，输入在&#x200B;**serverConf.xml**&#x200B;文件中定义的区域名称。 它对应于`<securityzone>`元素的&#x200B;**@name**&#x200B;属性。 在&#x200B;**标签**&#x200B;字段中输入链接到内部名称的标签。

   ![](assets/enum_addsecurityvalue.png)

1. 单击“确定”并保存修改。

定义区域并配置&#x200B;**[!UICONTROL Security zone]**&#x200B;明细列表后，您需要将每个运算符链接到一个安全区域：

1. 单击&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点。
1. 选择要将安全区域链接到的运算符，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 转到&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡并单击&#x200B;**[!UICONTROL Edit access parameters...]**&#x200B;链接。

   ![](assets/zone_operator.png)

1. 从&#x200B;**[!UICONTROL Authorized connection zone]**&#x200B;下拉列表中选择区域

   ![](assets/zone_operator_selection.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;并保存修改以应用这些更改。
