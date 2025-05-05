---
title: 在IMS迁移后更新Campaign界面
description: 了解如何激活AdobeIdentity Management系统迁移界面影响
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# 在IMS迁移后更新Campaign界面 {#impact-ims-migration}

在将Campaign技术操作员[迁移到Developer Console](ims-migration.md)并过渡到IMS以进行最终用户身份验证[&#128279;](migrate-users-to-ims.md)后，最后一步是启用用户界面和API限制，以删除特定于本机身份验证的选项和功能。 从Campaign v7.4.1开始提供此更新。

## 启用IMS限制 {#ims-restrictions}

要完成向Adobe标识管理系统(IMS)的迁移，必须阻止本机操作员创建新的本机用户、本机用户登录和API访问。 然后，您的环境将得到保护和标准化。

作为托管Cloud Service/托管用户，请与Adobe联系以启用此限制，并在产品用户界面中启用关联的更新。

对于内部部署/混合部署用户，请执行以下步骤：

1. 浏览到实例配置文件的`<imsConfig>`部分。
1. 要启用UI限制，请将`nonIMSOperatorMgmtInClientConsole`元素中的`nonIMSOperatorMgmtInClientConsoleRestricted`选项更新为`true`，如下所示：


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. 要启用API限制，请将`nonIMSAuthnAPI`元素中的`disableAPI`选项更新为`true`，如下所示：

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

请注意，允许少数操作员使用本机身份验证连接到Adobe Campaign。 这些技术运算符默认处于启用状态，不得修改。 为允许此例外，默认情况下将这些技术运算符添加到允许列表。 您可以在实例配置文件的`<imsConfig>`部分的`nonIMSAuthnAPI`元素内的`allowOperator`选项中找到此列表。

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

如果需要向允许列表添加运算符，请添加带有运算符名称的新`allowOperator`元素。 例如，如果要添加名为`test`的新运算符，请按照以下方式更新此部分：

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## 用户界面中的影响 {#ims-impacts}

完成迁移并按如下所述应用限制后，将对产品及其用户界面应用以下更改。

### 操作员管理 {#manage-admin}

不能再从客户端控制台创建、编辑、更新或删除具有本机身份验证的操作符。

因此，客户端控制台中已禁用这些操作。

操作员的管理集中在Adobe Admin Console中，以下任务现在只能通过此控制台进行管理。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}以了解如何创建用户和分配权限。

### 不可用选项 {#unavailable-migration}

迁移后，客户端控制台中不再提供以下任务：

* 使用[合并所选行选项](../../platform/using/updating-data.md#merge-data)来合并运算符。

* 为您的操作员更新以下字段：
   * 名称
   * 密码
   * 标签
   * 电子邮件

* [重置Campaign密码](../../production/using/lost-password.md)

* 编辑运算符的XML源

* 重复的运算符。


>[!MORELIKETHIS]
>
>* [最终用户迁移到IMS](migrate-users-to-ims.md)
>* [将技术操作员迁移到Adobe Developer控制台](ims-migration.md)
>* [Adobe Campaign Classic v7最新发行说明](../../rn/using/latest-release.md)
>* [什么是AdobeIdentity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}
