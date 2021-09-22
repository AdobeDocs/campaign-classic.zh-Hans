---
product: campaign
title: Campaign 18.6发行说明
description: Campaign 18.6发行说明
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---

# 18.6 版{#release-18-6}

![](../../assets/v7-only.svg)

## 18.6.2 版 - 内部版本 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>这栋建筑已被召回。 请[升级到最新内部版本](../../production/using/build-upgrade.md)或联系[Adobe客户关怀团队](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

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
   <td> 查询分段<br /> </td> 
   <td> <p>当多个Campaign用户连接到同一FDATeradata外部帐户时，您现在可以传递特定于每个用户的查询频带（键/值对）。 每次Campaign用户对Teradata数据库执行查询时，Adobe Campaign现在都能够发送与用户关联的元数据。 这些Teradata（包含在键和值列表中）随后可由数据管理员用于审核目的或管理访问权限，例如。</p><p>有关更多信息，请参阅<a href="../../installation/using/external-accounts.md">详细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功发送或通过密送存档失败变得更加容易和清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了对扩充活动结果进行排序时出现的语法错误。 (NEO-11394)
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动中使用计算字段时的问题。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修复了使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;提交选项时发生的问题。 (NEO-11047)
* 修复了在使用扩展连接器时无法发送短信的升级后问题。
* 改进了包导入/导出（界面中添加了日志和区域）。
* 修复了在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流活动未完全配置时，在升级后日志中显示无用错误的问题。

**技术演进**

查询分段

特定键（PROXYUSER或PROXYROLE）用于将Teradata用户或角色与Campaign用户关联。 添加了使用此代理用户/角色的新权限。 您需要将GRANTCONNECTTHROUGH访问权限添加到Teradata库帐户（在数据外部帐户中定义）。

在Teradata外部帐户中添加了新选项卡。 **[!UICONTROL Query banding]**&#x200B;选项卡包含以下选项：

* **[!UICONTROL Active]**:选中此框可激活该功能。
* **[!UICONTROL Default]**:输入默认查询分段，在用户没有关联的查询分段时使用该分段。如果没有定义默认查询分段，则没有关联查询分段的用户将无法使用Teradata。
* **[!UICONTROL Users]**:为每个用户指定查询分段。您可以根据需要添加任意数量的键/值对。 例如：&#39;priority=1;workload=high;&#39;

有关查询分段的详细信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 18.6 版 - 内部版本 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>这栋建筑已被召回。 请[升级到最新版本](../../production/using/build-upgrade.md)或联系[技术支持](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

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
   <td> 安全性改进<br /> </td> 
   <td> 向Campaign Classic添加了一系列安全改进功能。 下面列出了改进和修复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支持Windows Server 2016<br /> </td> 
   <td> Adobe Campaign现在与Windows Server 2016兼容。 请参阅<a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性矩阵</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

decryptString

**decryptString**&#x200B;函数已弃用。 请参阅[已弃用和已删除的功能](deprecated-features.md)一文。

对于新客户，此函数现在仅用于解密登陆页面中收件人的加密ID。 要解密存储在外部帐户中的密码，请使用新的&#x200B;**decryptPassword**&#x200B;函数。

对于现有客户，此函数的行为不会发生更改，但我们建议您使用&#x200B;**decryptPassword**，而不是&#x200B;**decryptString**。 **XtkSecurity_Unsafe_DecryptString**&#x200B;兼容性选项由升级后添加并默认激活，允许您继续使用函数。 如果要停用&#x200B;**decryptString**，请停用选项。

decryptPassword

添加了&#x200B;**decryptPassword**&#x200B;函数。 它允许您解密存储在外部帐户中的密码。 有关更多信息，请参阅[JSAPI](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)文档。

文件API

对于新安装，通过文件API访问文件夹的权限仅限于Adobe Campaign的&#x200B;**var**、**sftp**&#x200B;和临时文件夹。

对于现有客户，文件API无法再访问Adobe Campaign的&#x200B;**conf**&#x200B;文件夹。 **XtkSecurity_Disable_JSFileSandboxing**&#x200B;兼容性选项由升级后添加并默认激活，允许您继续访问其他文件夹。 如果要限制对Adobe Campaign的&#x200B;**var**、**sftp**&#x200B;和临时文件夹的访问，请停用选项。

**修补程序**

* 修复了可能影响短信事务型消息性能的问题。 (NEO-9812)
