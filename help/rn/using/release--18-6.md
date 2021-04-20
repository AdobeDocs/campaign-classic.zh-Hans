---
solution: Campaign Classic
product: campaign
title: 活动 18.6发行说明
description: 活动 18.6发行说明
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: Business Practitioner
level: Beginner
translation-type: tm+mt
source-git-commit: ce60b2bd0a9d75ca429af2f740832b408ce3c48b
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 6%

---


# 18.6 版{#release-18-6}

## 18.6.2 版 - 内部版本 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>这栋建筑已被召回。 请[升级到最新版本](../../production/using/build-upgrade.md)或与[Adobe客户服务部门](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系。

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
   <td> <p>当多个活动用户连接到同一联合数据访问Teradata外部帐户时，您现在可以传递特定于每个用户的查询带（键/值对）。 每次活动用户对Teradata库执行查询时，Adobe Campaign现在能够发送与用户相关联的元数据。 例如，这些包含在密钥和值列表中的Teradata管理员随后可以将其用于审计目的或管理访问权限。</p><p>有关详细信息，请参阅<a href="../../installation/using/external-accounts.md">详细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件归档日志已得到增强，这使得检查哪些电子邮件已成功发送或未通过密件抄送归档变得更轻松、更清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而非客户IP的问题。 (NEO-11295)
* 修复了导致错误覆盖投放属性的随机问题。 (NEO-11015)
* 修复了对扩充活动结果排序时出现的语法错误。 (NEO-11394)
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动中使用计算字段时的问题。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修复了在使用联合数据访问连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;投放选项时出现的问题。 (NEO-11047)
* 修复了在使用扩展连接器时无法发送SMS的错误等级问题。
* 改进的包导入/导出（在界面中添加了日志和区域）。
* 修复了在未完全配置&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动时，在配置级别日志中显示无用错误的问题。

**技术演进**

查询条带

特定密钥（PROXYUSER或PROXYROLE）用于将Teradata用户或角色与活动用户关联。 添加了新权限以使用此代理用户/角色。 您需要向CONNECT库帐户(Teradata外部帐户中定义的帐户)添加GRANT  THROUGH访问权限。

新选项卡已添加到Teradata外部帐户中。 **[!UICONTROL Query banding]**&#x200B;选项卡包含以下选项：

* **[!UICONTROL Active]**:选中此框可激活特征。
* **[!UICONTROL Default]**:输入默认查询条带，如果用户没有关联的查询条带，则将使用该条带。如果没有定义默认的查询条带，则没有关联的查询条带的用户将无法使用Teradata。
* **[!UICONTROL Users]**:对于每个用户，指定查询条带。您可以添加所需数量的键/值对。 例如：&#39;priority=1;workload=high;&#39;

有关查询条纹的详细信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 18.6 版 - 内部版本 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>这栋建筑已被召回。 请[升级到最新版本](../../production/using/build-upgrade.md)或与[技术支持](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系。

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
   <td> Adobe Campaign现在与Windows Server 2016兼容。 请参阅<a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性矩阵</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

decryptString

**decryptString**&#x200B;函数已弃用。 请参阅[已弃用和已删除功能](https://helpx.adobe.com/cn/campaign/kb/deprecated-and-removed-features.html)文章。

对于新客户，此函数现在仅用于解密登陆页中收件人的加密ID。 要解密存储在外部帐户中的密码，请使用新的&#x200B;**decryptPassword**&#x200B;函数。

对于现有客户，此函数的行为不会更改，但建议您使用&#x200B;**decryptPassword**&#x200B;而不是&#x200B;**decryptString**。 缺省情况下，配置程序会添加&#x200B;**XtkSecurity_Unsafe_DecryptString**&#x200B;兼容选项并激活该选项，以便您继续使用该函数。 如果要取消激活&#x200B;**decryptString**，请取消激活该选项。

decryptPassword

已添加&#x200B;**decryptPassword**&#x200B;函数。 它允许您解密存储在外部帐户中的密码。 有关详细信息，请参阅[JSAPI](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)文档。

文件API

对于新安装，通过文件API访问文件夹仅限于&#x200B;**var**、**sftp**&#x200B;和临时Adobe Campaign文件夹。

对于现有客户，文件API不再能访问Adobe Campaign的&#x200B;**conf**&#x200B;文件夹。 默认情况下，将添加&#x200B;**XtkSecurity_Disable_JSFileSandboxing**&#x200B;兼容性选项，并激活该选项以继续访问其他文件夹。 如果要限制对&#x200B;**var**、**sftp**&#x200B;和临时Adobe Campaign文件夹的访问，请取消激活该选项。

**修补程序**

* 修复了可能影响SMS事务性消息性能的问题。 (NEO-9812)
