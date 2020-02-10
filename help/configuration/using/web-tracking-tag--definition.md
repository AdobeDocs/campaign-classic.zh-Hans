---
title: “网络跟踪标签：定义”
seo-title: “网络跟踪标签：定义”
description: “网络跟踪标签：定义”
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# Web跟踪标记：定义{#web-tracking-tag-definition}

Web跟踪标记只是使用适当的参数构建的URL，通过HTTP查询发送到重定向服务器。

## 要发送的数据的格式 {#format-of-the-data-to-be-sent}

Web跟踪URL的格式如下： **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>添加到URL的随机数可避免浏览器缓存网页导致的问题。

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
                              <p>交付标识符和收件人标识符。</p> 
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
                              <p>收件人标识符（在会话Cookie不存在时有用）。</p> 
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
                              <p>如果没有会话Cookie，则使用的传送标识符。 此值将以十六进制表示。
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
                              <p>用于标识Internet用户的参数。 此参数的格式为“name=value”，其中name是收件人架构的字段。 此参数优先于会话cookie中包含的标识符。
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**一些Web跟踪URL**

* 访问“主页”标识符页面

   **https://myserver.adobe.com/r/9862?tagid=home**

* 收集业务量数据

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 指定字段以查找收件人

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帐号为10的收件人将发送到主页。

* 使用默认交付

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件人将发送到主页。 除非随该查询发送包含传送标识符的会话cookie，否则该信息将以标识符230（数据库16中的e6）存储在传送中。

>[!NOTE]
>
>通过URL参数发送到重定向服务器的所有值都必须经过URL编码。 在给定的示例中，请注意，字符&#39;=&#39;和&#39;|&#39;分别编码为&#39;%3D&#39;和&#39;%7C&#39;。

## 数据传输方法 {#data-transmission-methods}

可以使用以下方法：

* 在要跟踪的网 **页中合并的HTML标****`<img>`** 记的“src”属性中插入URL。
* 生成要跟踪的网页时直接调用重定向服务器。

