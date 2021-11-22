---
product: campaign
title: 投放报告
description: 投放报告
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 6%

---

# 人员和收件人 {#person-people-and-recipients}

![](../../assets/common.svg)

此示例将帮助您了解Adobe Campaign中的人员和收件人之间的区别。 我们将向多人发送投放内容，以突出显示人员与收件人之间的差异，同时详细说明以下指标的计算方法：

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>这些指标在 **[!UICONTROL Tracking indicators]** 报表。 有关更多信息，请参阅 [跟踪指标](../../reporting/using/delivery-reports.md#tracking-indicators).

投放中添加了三个链接。 它将发送给4个收件人：

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** :此收件人不会打开电子邮件（因此不会单击任何链接）。
* **[!UICONTROL Marie Stuart]** :打开电子邮件，但不会单击任何链接。
* **[!UICONTROL Florian David]** :打开电子邮件并单击链接9次。 他还会将电子邮件转发给打开后单击两次的人。
* **[!UICONTROL Henry Macdonald]** :此收件人已将其internet浏览器配置为拒绝cookie。 他打开电子邮件并点击链接4次。

返回以下跟踪日志：

![](assets/s_ncs_user_indicators_example_2.png)

为了更清晰地了解人员和收件人的计数方式，我们将分析每个用户档案的日志。

## 步骤1:约翰 {#step-1--john}

**[!UICONTROL John Davis]** 不会打开电子邮件（因此不会单击任何链接）。

![](assets/s_ncs_user_indicators_example_8.png)

由于John既未打开也未单击电子邮件，因此他不会显示在日志中。

**中间计算：**

|  | 点击了 | 点击了 | 打开的收件人 |
|---|---|---|---|
| 约翰 | - | - | - |
| 中间总计 | 0 | 0 | 0 |

## 步骤2:玛丽 {#step-2--marie}

**[!UICONTROL Marie Stuart]** 打开电子邮件，但不会单击任何链接。

![](assets/s_ncs_user_indicators_example_7.png)

Marie的打开显示在以下日志中：

![](assets/s_ncs_user_indicators_example_4bis.png)

打开项会分配给收件人：玛丽。 Adobe Campaign因此会向计数中添加新收件人。

**中间计算：**

|  | 点击了 | 点击了 | 打开的收件人 |
|---|---|---|---|
| 约翰 | - | - | - |
| 玛丽 | - | - | +1 |
| 中间总计 | 0 | 0 | 1 |

## 步骤3:弗洛里安 {#step-3--florian}

**[!UICONTROL Florian David]** 打开电子邮件并单击链接9次。 他还会将电子邮件转发给打开后单击两次的人。

![](assets/s_ncs_user_indicators_example_9.png)

Florian的操作（一次打开和9次单击）显示在以下日志中：

![](assets/s_ncs_user_indicators_example_3bis.png)

**收件人**:打开和点击将分配给同一收件人(Florian)。 由于此收件人与上一个(Marie)不同，因此Adobe Campaign会向计数中添加新收件人。

人员：由于此收件人的浏览器接受Cookie，因此我们可以看到为所有点击日志分配了相同的标识符(UUID): **`fe37a503 [...]`**. Adobe Campaign可正确地将这些点击识别为属于同一个人。 新人员会添加到计数中。

**中间计算：**

|  | 点击了 | 点击了 | 打开的收件人 |
|---|---|---|---|
| 约翰 | - | - | - |
| 玛丽 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 中间总计 | 1 | 1 | 2 |

以下日志与Florian将电子邮件转发给的人进行的打开和两次点击一致：

![](assets/s_ncs_user_indicators_example_6bis.png)

**收件人**:其打开和点击量会分配给转发电子邮件的收件人(Florian)。 由于此收件人已被计数，因此收件人计数保持不变。

![](assets/s_ncs_user_indicators_example_12.png)

**人员**:对于单击，我们可以看到为所有日志分配了相同的标识符(UUID): **`9ab648f9 [...]`**. 此标识符尚未被计数。 因此，会向计数中添加新人员。

![](assets/s_ncs_user_indicators_example_13.png)

**中间计算：**

|  | 点击了 | 点击了 | 打开的收件人 |
|---|---|---|---|
| 约翰 | - | - | - |
| 玛丽 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 未知人员 | - | +1 | - |
| 中间总计 | 1 | 2 | 2 |

## 步骤4:亨利 {#step-4--henry}

**[!UICONTROL Henry Macdonald]** 已将其internet浏览器配置为拒绝cookie。 他打开电子邮件并点击链接4次。

![](assets/s_ncs_user_indicators_example_10.png)

Henry执行的打开和4次点击显示在以下日志中：

![](assets/s_ncs_user_indicators_example_5bis.png)

**收件人**:打开和点击被分配给同一收件人(Henry)。 由于此收件人尚未计数，因此Adobe Campaign会向计数中添加一个收件人。

**人员**:由于Henry的浏览器不接受Cookie，因此每次单击都会生成一个新的标识符(UUID)。 4次点击中的每次点击都会被解释为来自不同的人员。 由于这些标识符尚未计数，因此会将其添加到计数中。

**中间计算：**

|  | 点击了 | 点击了 | 打开的收件人 |
|---|---|---|---|
| 约翰 | - | - | - |
| 玛丽 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 未知人员 | - | +1 | - |
| 亨利 | +1 | +4 | +1 |
| 中间总计 | 2 | 6 | 3 |

## 概要 {#summary}

在投放级别，我们获得了以下结果：

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** （点击的收件人）：2
* **[!UICONTROL Distinct clicks for the population reached]** （点击的人员）：6
* **[!UICONTROL Distinct opens for the population reached]** （打开的收件人）：3

原始反应性和前向估计计算如下：

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** （因此为6 - 2 = 4）
* **[!UICONTROL Raw reactivity]** = **A / C** （因此为2 / 3 = 66,67%）

>[!NOTE]
>
>在以下公式中：
>
>* A表示 **[!UICONTROL Clicks]** 指示器（单击的收件人）。
>* B表示 **[!UICONTROL Distinct clicks for the population reached]** 指标（点击的人员）。
>* C表示 **[!UICONTROL Distinct opens for the population reached]** 指示器（打开的收件人）。

