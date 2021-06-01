---
product: campaign
title: 配置安全区
description: 了解如何配置安全区
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 1%

---


# 定义安全区（内部部署）{#defining-security-zones}

每个操作员需要链接到区域才能登录到实例，并且操作员IP必须包含在安全区域中定义的地址或地址集中。 安全区域配置在Adobe Campaign服务器的配置文件中执行。

操作员从控制台中的配置文件链接到安全区域，可在&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中访问该安全区域。 [了解详情](#linking-a-security-zone-to-an-operator)。

>[!NOTE]
>
>此过程仅限于&#x200B;**on-premise**&#x200B;部署。
>
>作为&#x200B;**托管的**&#x200B;客户，如果您可以访问[促销活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)，则可以使用Security Zone自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hans)
>
>其他&#x200B;**混合/托管**&#x200B;客户需要联系Adobe支持团队以将IP添加到允许列表。


## 创建安全区{#creating-security-zones}

区域由以下项定义：

* 一个或多个IP地址范围（IPv4和IPv6）
* 与每个IP地址范围关联的技术名称

安全区域是互锁的，这意味着在另一个区域内定义新区域会减少可以登录到该区域的操作员数量，同时增加分配给每个操作员的权限。

必须在服务器配置期间在&#x200B;**serverConf.xml**&#x200B;文件中定义区域。 **serverConf.xml**&#x200B;中可用的所有参数都列在[此部分](../../installation/using/the-server-configuration-file.md)中。

每个区域都定义权限，例如：

* HTTP连接而不是HTTPS
* 错误显示(Java错误、JavaScript、C++等)
* 报表和WebApp预览
* 通过登录/密码进行身份验证
* 非安全连接模式

>[!NOTE]
>
>**每个运算符都必须链接到区域**。如果运算符的IP地址属于区域定义的范围，则运算符可以登录到实例。\
>操作员的IP地址可以在多个区域中定义。 在这种情况下，运算符会接收每个区域的可用权限的&#x200B;**set**。

现成的&#x200B;**serverConf.xml**&#x200B;文件包含三个区域：**公共、VPN和LAN**。

>[!NOTE]
>
>**开箱即用的配置是安全的**。但是，在从旧版Adobe Campaign迁移之前，可能需要临时降低安全性，才能迁移和批准新规则。

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

定义区域的所有权限如下所示：

* **allowDebug**:允许在“调试”模式下执行webApp
* **allowEmptyPassword**:在没有密码的情况下授权与实例的连接
* **allowHTTP**:无需使用HTTPS协议即可创建会话
* **allowUserPassword**:会话令牌可使用以下格式“`<login>/<password>`”
* **sessionTokenOnly**:连接URL中不需要安全令牌
* **showErrors**:服务器端的错误将被转发并显示

>[!IMPORTANT]
>
>在区域定义中，每个具有&#x200B;**true**&#x200B;值的属性都会降低安全性。

在使用消息中心时，如果存在多个执行实例，则需要使用定义为&#x200B;**true**&#x200B;的&#x200B;**sessionTokenOnly**&#x200B;属性创建一个额外的安全区域，其中只需添加必要的IP地址。 有关配置实例的更多信息，请参阅[本文档](../../message-center/using/configuring-instances.md)。

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

我们建议仅在专用于实例的配置文件中为只访问特定实例的运算符直接定义IP地址范围。

在&#x200B;**`config-<instance>.xml`**&#x200B;文件中：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全区域{#sub-networks-and-proxies-in-a-security-zone}中的子网络和代理

**proxy**&#x200B;参数可在&#x200B;**subNetwork**&#x200B;元素中使用，以指定安全区中的代理使用。

当引用代理并且连接通过此代理进入时（通过HTTP X-Forwarded-For标头可见），验证的区域是代理客户端的区域，而不是代理客户端的区域。

>[!IMPORTANT]
>
>如果配置了代理并且可以覆盖该代理（或者如果不存在），则将测试的IP地址将能够被伪造。
>
>此外，中继现在与代理类似。 因此，您可以将IP地址127.0.0.1添加到安全区域配置中的代理列表。
>
>例如：&quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;。

可能会出现各种情况：

* 子网络在安全区域中直接引用，且未配置代理：子网络的用户可以直接连接到Adobe Campaign服务器。

   ![](assets/8101_proxy1.png)

* 为安全区域中的子网络指定代理：来自此子网络的用户可以通过此代理访问Adobe Campaign服务器。

   ![](assets/8101_proxy2.png)

* 代理包含在安全区子网络中：通过此代理具有访问权限的用户（无论其来源如何）可以访问Adobe Campaign服务器。

   ![](assets/8101_proxy3.png)

有可能访问Adobe Campaign服务器的代理的IP地址必须在相关的&#x200B;**`<subnetwork>`**&#x200B;和第一级子网络&#x200B;**`<subnetwork name="all"/>`**&#x200B;中输入。 例如，以下是IP地址为10.131.146.102的代理：

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

定义区域后，每个操作员必须链接到其中一个操作员才能登录到实例，并且该操作员的IP地址必须包含在区域中引用的地址或地址范围中。

区域的技术配置在Campaign Server的配置文件中执行：**serverConf.xml**。

在此之前，您必须首先配置现成的&#x200B;**[!UICONTROL Security zone]**&#x200B;枚举，以将标签链接到&#x200B;**serverConf.xml**&#x200B;文件中定义的区域的内部名称。

此配置在Campaign资源管理器中完成：

1. 单击&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;节点。
1. 选择&#x200B;**[!UICONTROL Security zone (securityZone)]**&#x200B;系统枚举。

   ![](assets/enum_securityzone.png)

1. 对于服务器配置文件中定义的每个安全区域，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Internal name]**&#x200B;字段中，输入在&#x200B;**serverConf.xml**&#x200B;文件中定义的区域名称。 它对应于`<securityzone>`元素的&#x200B;**@name**&#x200B;属性。 在&#x200B;**Label**&#x200B;字段中输入链接到内部名称的标签。

   ![](assets/enum_addsecurityvalue.png)

1. 单击确定并保存修改。

定义区域并配置&#x200B;**[!UICONTROL Security zone]**&#x200B;枚举后，您需要将每个运算符链接到安全区域：

1. 单击&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点。
1. 选择要将安全区域链接到的运算符，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 转到&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Edit access parameters...]**&#x200B;链接。

   ![](assets/zone_operator.png)

1. 从&#x200B;**[!UICONTROL Authorized connection zone]**&#x200B;下拉列表中选择一个区域

   ![](assets/zone_operator_selection.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;并保存修改以应用这些更改。



## 建议

* 确保在subNetwork中不允许使用反向代理。 如果是，将检测到&#x200B;**所有**&#x200B;流量来自此本地IP，因此将受信任。

* 最大限度地减少sessionTokenOnly=&quot;true&quot;的使用：

   * 警告：如果此属性设置为true，则运算符可能会受到&#x200B;**CRSF攻击**。
   * 此外，sessionToken Cookie未使用httpOnly标记进行设置，因此某些客户端Javascript代码可以读取它。
   * 但是，多个执行单元格上的消息中心需要sessionTokenOnly:创建新的安全区域，并将sessionTokenOnly设置为“true”，并在此区域中仅添加所需的IP **。**

* 如果可能，将所有allowHTTP、showErrors设置为false（不适用于localhost）并检查它们。

   * allowHTTP = &quot;false&quot;:强制运算符使用HTTPS
   * showErrors = &quot;false&quot;:隐藏技术错误（包括SQL错误）。 它可以防止显示过多信息，但会降低营销人员解决错误的能力（无需向管理员请求更多信息）

* 仅当营销用户/管理员使用的IP需要创建（事实上是预览）调查、WebApps和报表时，才将allowDebug设置为true。 此标记允许这些IP显示中继规则并对其进行调试。

* 请勿将allowEmptyPassword、allowUserPassword、allowSQLIncompent设置为true。 以下属性仅用于从v5和v6.0顺利迁移：

   * **** allowEmptyPasswordlets运算符的密码为空。如果是这种情况，请通知所有操作员要求他们在截止时间内设置密码。 在此截止日期过后，将此属性更改为false。

   * **** allowUserPasswordlets运算符将其凭据作为参数发送（以便它们将由apache/IIS/proxy记录）。此功能过去曾用于简化API使用。 您可以在指南（或在规范中）中查看某些第三方应用程序是否使用它。 如果是，您必须通知他们更改使用我们API的方式，并尽快删除此功能。

   * **** allowSQLInjection允许用户使用旧语法执行SQL注入。尽快执行[此页面](../../migration/using/general-configurations.md)中描述的更正，以便能够将此属性设置为false。 您可以使用/nl/jsp/ping.jsp?zones=true检查您的安全区域配置。 此页显示当前IP的安全措施（使用这些安全标志计算）的活动状态。

* HttpOnly Cookie/useSecurityToken:请参阅&#x200B;**sessionTokenOnly**&#x200B;标记。

* 最大限度地减少添加到允许列表的IP:我们开箱即用地在安全区中为专用网络添加了3个范围。 您不太可能使用所有这些IP地址。 所以只保留你需要的。

* 更新webApp/internal运算符，使其仅可在本地主机中访问。
