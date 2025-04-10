---
product: campaign
title: 配置安全区域
description: 了解如何配置安全区域
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 0%

---

# 定义安全区（内部部署）{#defining-security-zones}



每个运算符都需要链接到区域才能登录到实例，并且运算符IP必须包含在安全区域中定义的地址或地址集中。 安全区域配置在Adobe Campaign服务器的配置文件中执行。

操作员在控制台中从其配置文件链接到安全区域，可在&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点中访问。 [了解详情](#linking-a-security-zone-to-an-operator)。

>[!NOTE]
>
>此过程仅限于&#x200B;**内部部署**。
>
>作为&#x200B;**托管**&#x200B;客户，如果您可以访问[Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)，则可以使用Security Zone自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hans)
>
>其他&#x200B;**混合/托管**&#x200B;客户需要联系Adobe列入允许列表支持团队以将IP添加到。
>

## 创建安全区域 {#creating-security-zones}

区域由以下定义：

* 一个或多个IP地址范围（IPv4和IPv6）
* 与每个IP地址范围关联的技术名称

安全区域是互锁的，这意味着在另一个区域中定义新区域可以减少可以登录该区域的操作员数量，同时增加分配给每个操作员的权限。

必须在服务器配置期间在&#x200B;**serverConf.xml**&#x200B;文件中定义区域。 **serverConf.xml**&#x200B;中的所有可用参数都列在[此部分](../../installation/using/the-server-configuration-file.md)中。

每个区域都定义了权限，例如：

* HTTP连接，而不是HTTPS
* 错误显示(Java错误、JavaScript、C++等)
* 报表和WebApp预览
* 通过登录/密码进行身份验证
* 非安全连接模式

>[!NOTE]
>
>**每个运算符都必须链接到区域**。 如果运算符的IP地址属于区域定义的范围，则该运算符可以登录到实例。\
>操作员的IP地址可以在多个区域中定义。 在这种情况下，操作员将收到每个区域的&#x200B;**组**&#x200B;可用权限。

现成&#x200B;**serverConf.xml**&#x200B;文件包含三个区域： **公共、VPN和LAN**。

>[!NOTE]
>
>**现成配置是安全的**。 但是，在从早期版本的Adobe Campaign迁移之前，可能需要临时降低安全性，才能迁移和批准新规则。

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

* **allowDebug**：允许在“调试”模式下执行webApp
* **allowEmptyPassword**：授权连接到没有密码的实例
* **allowHTTP**：无需使用HTTPS协议即可创建会话
* **allowUserPassword**：会话令牌可以具有以下形式“`<login>/<password>`”
* **sessionTokenOnly**：连接URL中不需要安全令牌
* **showErrors**：转发并显示服务器端错误

>[!IMPORTANT]
>
>在区域定义中，每个值为&#x200B;**true**&#x200B;的属性都会降低安全性。

使用消息中心时，如果有多个执行实例，则需要使用&#x200B;**sessionTokenOnly**&#x200B;属性创建其他安全区域，该属性定义为&#x200B;**true**，其中仅添加必要的IP地址。 有关配置实例的更多信息，请参阅[本文档](../../message-center/using/configuring-instances.md)。

## 安全区的最佳实践 {#best-practices-for-security-zones}

在&#x200B;**lan**&#x200B;安全区域的定义中，可以添加定义技术访问的IP地址掩码。 此添加将启用对服务器上托管的所有实例的访问。

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

我们建议直接在专用于实例的配置文件中定义仅访问特定实例的操作员的IP地址范围。

在&#x200B;**`config-<instance>.xml`**&#x200B;文件中：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全区域中的子网络和代理 {#sub-networks-and-proxies-in-a-security-zone}

**proxy**&#x200B;参数可在&#x200B;**subNetwork**&#x200B;元素中使用，以指定安全区域中的代理使用。

当引用了代理并且连接通过此代理（通过HTTP X-Forwarded-For标头可见）进入时，验证的区域是代理的客户端而不是代理的客户端。

>[!IMPORTANT]
>
>如果配置了代理并且可以覆盖它（如果不存在，则覆盖它），则将测试的IP地址将能够被伪造。
>
>此外，中继现在像代理一样生成。 因此，您可以将IP地址127.0.0.1添加到安全区域配置的代理列表中。
>
>例如：“`<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`”。

可能会出现各种情况：

* 子网络直接在安全区域中引用，并且未配置代理：子网络的用户可以直接连接到Adobe Campaign服务器。

  ![](assets/8101_proxy1.png)

* 为安全区域中的子网络指定代理：来自此子网络的用户可以通过此代理访问Adobe Campaign服务器。

  ![](assets/8101_proxy2.png)

* 代理包含在安全区域子网络中：无论来自何处，通过此代理进行访问的用户都可以访问Adobe Campaign服务器。

  ![](assets/8101_proxy3.png)

可能访问Adobe Campaign服务器的代理的IP地址必须在相关&#x200B;**`<subnetwork>`**&#x200B;和第一级子网&#x200B;**`<subnetwork name="all"/>`**&#x200B;中输入。 例如，下面是指IP地址为10.131.146.102的代理：

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

## 将安全区域链接到操作员 {#linking-a-security-zone-to-an-operator}

定义区域后，必须将每个运算符链接到其中一个运算符才能登录到实例，并且运算符的IP地址必须包含在区域中引用的地址或地址范围中。

区域的技术配置在Campaign服务器的配置文件中执行： **serverConf.xml**。

在此之前，您必须首先配置现成的&#x200B;**[!UICONTROL Security zone]**&#x200B;枚举，将标签链接到&#x200B;**serverConf.xml**&#x200B;文件中定义的区域的内部名称。

此配置在Campaign资源管理器中完成：

1. 单击&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;节点。
1. 选择&#x200B;**[!UICONTROL Security zone (securityZone)]**&#x200B;系统枚举。

   ![](assets/enum_securityzone.png)

1. 对于在服务器的配置文件中定义的每个安全区域，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Internal name]**&#x200B;字段中，输入&#x200B;**serverConf.xml**&#x200B;文件中定义的区域名称。 它对应于`<securityzone>`元素的&#x200B;**@name**&#x200B;属性。 在&#x200B;**标签**&#x200B;字段中输入链接到内部名称的标签。

   ![](assets/enum_addsecurityvalue.png)

1. 单击“确定”并保存修改。

定义区域并配置&#x200B;**[!UICONTROL Security zone]**&#x200B;枚举后，您需要将每个运算符链接到安全区域：

1. 单击&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点。
1. 选择要将安全区域链接到的操作员，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 转到&#x200B;**[!UICONTROL Access rights]**&#x200B;选项卡并单击&#x200B;**[!UICONTROL Edit access parameters...]**&#x200B;链接。

   ![](assets/zone_operator.png)

1. 从&#x200B;**[!UICONTROL Authorized connection zone]**&#x200B;下拉列表中选择一个区域

   ![](assets/zone_operator_selection.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;并保存修改以应用这些更改。



## 推荐做法

* 确保在subNetwork中不允许使用反向代理。 如果出现这种情况，则将检测到&#x200B;**所有**&#x200B;流量都来自此本地IP，因此将被信任。

* 最小化sessionTokenOnly=&quot;true&quot;的使用：

   * 警告：如果此属性设置为true，则该运算符可能会遭到&#x200B;**CRSF攻击**。
   * 此外，sessionToken Cookie未设置httpOnly标记，因此某些客户端JavaScript代码可以读取它。
   * 但是，多个执行单元格上的Message Center需要sessionTokenOnly：在sessionTokenOnly设置为“true”的情况下创建新的安全区域，并在该区域中仅添加&#x200B;**所需的IP**。

* 如果可能，请将所有allowHTTP、showErrors设置为false（不适用于localhost）并检查它们。

   * allowHTTP = &quot;false&quot;：强制运算符使用HTTPS
   * showErrors = &quot;false&quot;：隐藏技术错误（包括SQL错误）。 它可防止显示过多信息，但会降低营销人员解决错误的能力（无需向管理员请求更多信息）

* 仅当营销用户/管理员使用的IP需要创建（实际上是预览）调查、webApps和报告时，才可将allowDebug设置为true。 此标记允许这些IP显示中继规则并对其进行调试。

   * 当allowDebug设置为false时，输出为：

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * 当allowDebug设置为true时，输出为：

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* 切勿将allowEmptyPassword、allowUserPassword、allowSQLInjection设置为true。

   * **allowEmptyPassword**&#x200B;允许操作员的密码为空。 如果您遇到这种情况，请通知所有操作员要求他们设置带有截止日期的密码。 超过此截止日期后，将此属性更改为false。

   * **allowUserPassword**&#x200B;允许操作员发送其凭据作为参数（以便由apache/IIS/proxy记录它们）。 此功能以前用于简化API的使用。 您可以签入指南（或规范）中是否某些第三方应用程序使用此功能。 如果是这样，您必须通知他们更改使用我们的API的方式，并尽快删除此功能。

   * **allowSQLInjection**&#x200B;允许用户使用旧语法执行SQL注入。 此属性应设置为false。 您可以使用/nl/jsp/ping.jsp？zones=true检查安全区域配置。 此页显示当前IP的安全措施（使用这些安全标志计算）的活动状态。

* HttpOnly Cookie/useSecurityToken：请参阅&#x200B;**sessionTokenOnly**&#x200B;标志。

* 最小化添加到允许列表的IP：开箱即用，在安全区域中，我们为专用网络添加了3个范围。 您不太可能会使用所有这些IP地址。 所以只留你需要的那些吧。

* 将webApp/internal运算符更新为仅可在localhost中访问。
