---
title: 版本 18.6
seo-title: 版本 18.6
description: 版本 18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---


# 版本 18.6{#release-18-6}

## 版本 18.6.2 - 版本 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>这栋建筑已被收回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或与技 [术支持联系](https://support.neolane.net/)。

**新增功能**

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
   <td> <p>当多个活动用户连接到同一联合数据访问Teradata外部帐户时，您现在可以传递每个用户特有的查询带（键／值对）。 每次活动用户对Teradata查询库执行时，Adobe Campaign现在能够发送与用户相关的元数据。 这些数据包含在一列表键和值中，然后Teradata管理员可以用于审核目的或管理访问权限，例如。</p><p>有关详细信息，请参阅<a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">详细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件归档日志已得到增强，这使得检查哪些电子邮件已通过密送归档成功发送或失败变得更简单、更清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而非客户IP的问题。 (NEO-11295)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了在对扩充活动结果排序时出现的语法错误。 (NEO-11394)
* 修复了在工作流活动中使用计算字段 **[!UICONTROL Survey answers]** 时的问题。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修复了使用PostgreSQL联合数据访问库的连接时LATIN1编码错误。 (NEO-11299)
* 修复了使用投放选项时发 **[!UICONTROL Prepare the personalization data with a workflow]** 生的问题。 (NEO-11047)
* 修复了在使用扩展连接器时无法发送SMS的错误等级问题。
* 改进的包导入／导出（在界面中添加了日志和区域）。
* 修复了在工作流活动未完全配置时，在配置级别日志中 **[!UICONTROL Survey answers]** 显示无用错误的问题。

**技术演进**

查询条带

特定密钥（PROXYUSER或PROXYROLE）用于将Teradata用户或角色与活动用户关联。 已添加新权限以使用此代理用户／角色。 您需要向CONNECT库帐户(Teradata外部帐户中定义的帐户)添加GRANTTHROUGH访问权限。

在Teradata外部帐户中添加了新选项卡。 该选 **[!UICONTROL Query banding]** 项卡包含以下选项：

* **[!UICONTROL Active]**:选中此框可激活特征。
* **[!UICONTROL Default]**:输入默认查询条带，如果用户没有关联的查询条带，则将使用该条带。 如果没有定义默认的查询条带，则没有关联查询条带的用户将无法使用Teradata。
* **[!UICONTROL Users]**:为每个用户指定查询条带。 您可以添加所需数量的键／值对。 例如：“priority=1;workload=high;

有关查询条纹的详细信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 版本 18.6 - 版本 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>这栋建筑已被收回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或与技 [术支持联系](https://support.neolane.net/)。

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 说明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 安全改进<br /> </td> 
   <td> Campaign Classic中增加了一系列安全改进。 以下列出了改进和修复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支持Windows Server 2016<br /> </td> 
   <td> Adobe Campaign现在与Windows Server 2016兼容。 请参阅 <a href="https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性表</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

decryptString

decryptString **函数** 已弃用。 请参阅已弃 [用和已删除功能](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html) 。

对于新客户，此函数现在仅用于解密登陆页中收件人的加密ID。 要解密存储在外部帐户中的口令，请使用新的 **decryptPassword** 函数。

对于现有客户，此函数的行为不会更改，但建议您使用decryptPassword **，而** 不是decryptString ****。 XtkSecurity **_Unsafe_DecryptString兼容性选项由配置程序添加** ，并在默认情况下处于激活状态，这样您就可以继续使用该函数。 如果要取消激活 **decryptString**，请取消激活该选项。

decryptPassword

已 **添加** decryptPassword函数。 它允许您解密存储在外部帐户中的密码。 有关详细 [信息](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html) ，请参阅JSAPI文档。

文件API

对于新安装，通过文件API访问文件夹的权限 **仅限于var**、 **sftp** 和临时Adobe Campaign文件夹。

对于现有客户，文件API不再能访问 **Adobe Campaign** conf文件夹。 XtkSecurity **_Disable_JSFileSandboxing兼容性选项由配置程序添加** ，默认情况下会激活它，这样您就可以继续访问其他文件夹。 如果要限制对Adobe Campaign的var、 **sftp****** 和临时文件夹的访问，请取消激活该选项。

**修补程序**

* 修复了可能影响SMS事务性消息性能的问题。 (NEO-9812)
