---
title: 版本18.6
seo-title: 版本18.6
description: 版本18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d046304657f04312d78176c49a650690b05e4c94

---


# 版本18.6{#release-18-6}

## 版本18.6.2 —— 内部版本8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>这栋建筑已被召回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或联系技 [术支持](https://support.neolane.net/)。

**有什么新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 说明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 查询条带<br /> </td> 
   <td> <p>当多个Campaign用户连接到同一个FDA Teradata外部帐户时，您现在可以传递特定于每个用户的查询带（键／值对）。 每次Campaign用户对Teradata数据库执行查询时，Adobe Campaign现在都能够发送与用户关联的元数据。 这些数据包含在密钥和值列表中，然后Teradata管理员可以将其用于审计目的或管理访问权限。</p><p>有关详细信息，请参阅详 <a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件归档日志已得到增强，这样可以更轻松、更清晰地检查哪些电子邮件已通过密件抄送归档成功发送或失败。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了导致错误覆盖交付属性的随机问题。 (NEO-11015)
* 修复了对丰富化活动结果进行排序时出现的语法错误。 (NEO-11394)
* 修复了在工作流活动中使用计算字段 **[!UICONTROL Survey answers]** 的问题。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修复了在使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了使用提交选项时出 **[!UICONTROL Prepare the personalization data with a workflow]** 现的问题。 (NEO-11047)
* 修复了在使用扩展连接器时无法发送SMS的配置升级问题。
* 改进的包导入／导出（在界面中添加了日志和区域）。
* 修复了在工作流活动未完全配置时在配置升级日志中 **[!UICONTROL Survey answers]** 显示无用错误的问题。

**技术演进**

查询条带

特定密钥（PROXYUSER或PROXYROLE）用于将Teradata用户或角色关联到Campaign用户。 已添加新权限以使用此代理用户／角色。 您需要向数据库帐户（在Teradata外部帐户中定义的帐户）添加GRANT CONNECT THROUGH访问权限。

Teradata外部帐户中添加了新选项卡。 该选 **[!UICONTROL Query banding]** 项卡包含以下选项：

* **[!UICONTROL Active]**:选中此框可激活该功能。
* **[!UICONTROL Default]**:输入默认的查询条带，如果用户没有关联的查询条带，则使用该条带。 如果没有定义默认的查询条带，则没有关联的查询条带的用户将无法使用Teradata。
* **[!UICONTROL Users]**:对于每个用户，指定查询条带。 您可以添加所需数量的键／值对。 例如：“优先级=1；工作量=高；”

有关查询条带的详细信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 版本18.6 —— 内部版本8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>这栋建筑已被召回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或联系技 [术支持](https://support.neolane.net/)。

**有什么新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 说明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 安全性改进<br /> </td> 
   <td> 系列安全性改进已添加到Campaign Classic中。 以下列出了改进和修复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支持Windows Server 2016<br /> </td> 
   <td> Adobe Campaign现在与Windows Server 2016兼容。 请参阅 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性表</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

decryptString

decryptString **函数已弃用** 。 请参阅已弃 [用和已删除功能](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) 。

对于新客户，此函数现在仅用于解密登录页面中收件人的加密ID。 要解密存储在外部帐户中的口令，请使用新的decryptPassword **函数** 。

对于现有客户，此函数的行为不会更改，但我们建议您使用decryptPassword **，而不是** decryptString ****。 XtkSecurity_ **Unsafe_DecryptString** 兼容性选项由配置添加并在默认情况下激活，这样您就可以继续使用该函数。 如果要取消激活decryptString ****，请取消激活该选项。

decryptPassword

已 **添加decryptPassword** 函数。 它允许您解密存储在外部帐户中的口令。 有关详细 [信息](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，请参阅JSAPI文档。

文件API

对于新安装，通过文件API访问文件夹的权限仅限于 **Adobe** Campaign的 **var** 、sftp和临时文件夹。

对于现有客户，文件API无法再访问 **Adobe** Campaign的conf文件夹。 XtkSecurity_Disable_JSFileSandboxing兼容性选项由配置添加 **** ，默认情况下会激活它，这样您就可以继续访问其他文件夹。 如果要限制对Adobe Campaign的 **var**、 **sftp** 和临时文件夹的访问，请取消激活此选项。

**修补程序**

* 修复了可能影响SMS交易消息性能的问题。 (NEO-9812)
