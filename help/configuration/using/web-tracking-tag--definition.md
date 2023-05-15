---
product: campaign
title: 定义Web跟踪标记
description: 定义Web跟踪标记
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---

# Web 跟踪标记：定义{#web-tracking-tag-definition}



Web跟踪标记只是使用相应参数构建的URL，通过HTTP查询发送到重定向服务器。

## 要发送的数据的格式 {#format-of-the-data-to-be-sent}

Web跟踪URL的格式如下： **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>添加到URL的随机数可避免浏览器缓存网页所导致的问题。

下表提供了重定向服务器支持的特殊参数列表。

<table>
                     <thead>
                        <tr>
                           <th>名称</th>
                           <th>类型</th>
                           <th>说明</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>会话Cookie</p> 
                           </td>
                           <td>
                              <p>投放标识符和收件人标识符。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>永久Cookie</p> 
                           </td>
                           <td>
                              <p>收件人标识符（在会话Cookie缺失时有用）。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL参数</p> 
                           </td>
                           <td>
                              <p>跟踪网页的标识符：这是唯一的必需参数。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL参数</p> 
                           </td>
                           <td>
                              <p>没有会话Cookie时要使用的投放标识符。 此值以十六进制表示。
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL参数</p> 
                           </td>
                           <td>
                              <p>用于标识Internet用户的参数。 此参数的格式为“name=value”，其中name是收件人架构的字段。 此参数优先于会话Cookie中包含的标识符。
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**一些Web跟踪URL**

* 访问“home”标识符页面

   **https://myserver.adobe.com/r/9862?tagid=home**

* 收集业务量数据

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 指定用于查找收件人的字段

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帐号为10的收件人将发送到主页。

* 使用默认投放

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件人将发送到主页。 除非随此查询发送包含投放标识符的会话Cookie，否则此信息将以标识符230（数据库16中为e6）存储在投放中。

>[!NOTE]
>
>通过URL参数发送到重定向服务器的所有值都必须进行URL编码。 在给定的示例中，请注意字符“=”和“|”分别编码为“%3D”和“%7C”。

## 数据传输方法 {#data-transmission-methods}

可以使用以下方法：

* 在 **&quot;src&quot;** 属性HTML **`<img>`** 标记包含在要跟踪的网页中。
* 在生成要跟踪的网页时，直接调用重定向服务器。
