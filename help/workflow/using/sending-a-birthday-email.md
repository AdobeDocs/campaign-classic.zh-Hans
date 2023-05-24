---
product: campaign
title: 发送生日电子邮件
description: 了解如何使用工作流发送生日电子邮件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 2%

---

# 发送生日电子邮件{#sending-a-birthday-email}



## 简介 {#introduction}

此用例介绍了如何规划在收件人的生日当天向收件人列表发送定期电子邮件。

为了设置此用例，我们创建了以下定位工作流：

![](assets/birthday-workflow_usecase_1.png)

此（每日运行）工作流会选择在当前日期生日的所有收件人。

![](assets/do-not-localize/how-to-video.png) 此用例也可以通过视频的形式找到。 有关详情，请参阅 [创建工作流](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) 视频。

要实现此目的，请创建营销策划，然后单击 **[!UICONTROL Targeting and workflows]** 选项卡。 有关详情，请参阅 [在工作流中构建主目标](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) 部分。

然后按照以下步骤操作：

## 计划发送 {#configuring-the-scheduler}

1. 首先，添加 **调度程序** 以触发每天发送投放。 在以下示例中，每天早上6:00创建投放。

   ![](assets/recur_delivery2.png)


## 确定生日为的收件人 {#identifying-recipients-whose-birthday-it-is}

配置之后 **[!UICONTROL Scheduler]** 活动以便工作流每天开始一次，标识其出生日期等于当前日期的所有收件人。

要执行此操作，请应用以下步骤：

1. 拖放 **[!UICONTROL Query]** 活动并将其双击到工作流中。
1. 单击 **编辑查询** 链接并选择 **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. 单击 **[!UICONTROL Expression]** 列并单击 **[!UICONTROL Edit expression]** 以打开表达式编辑器。

   ![](assets/s_ncs_user_create_exp_exple.png)

1. 单击 **[!UICONTROL Advanced selection]** 以选择过滤模式。

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. 选择 **[!UICONTROL Edit the formula using an expression]** 并单击 **[!UICONTROL Next]** 以显示表达式编辑器。
1. 在函数列表中，双击 **[!UICONTROL Day]**，可通过 **[!UICONTROL Date]** 节点。 此函数返回数字，该数字表示与作为参数传递的日期对应的日期。

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. 在可用字段列表中，双击 **[!UICONTROL Birth date]**. 然后，该编辑器的上半部分显示以下公式：

   ```
   Day(@birthDate)
   ```

   单击 **[!UICONTROL Finish]** 确认。

1. 在查询编辑器的第一个单元格中， **[!UICONTROL Operator]** 列，选择 **[!UICONTROL equal to]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. 接下来，单击第二列的第一个单元格(**[!UICONTROL Value]**)，然后单击 **[!UICONTROL Edit expression]** 以打开表达式编辑器。
1. 在函数列表中，双击 **[!UICONTROL Day]**，可通过 **[!UICONTROL Date]** 节点。
1. 双击 **[!UICONTROL GetDate]** 函数以检索当前日期。

   ![](assets/s_ncs_user_create_exp_exple04.png)

   编辑器的上半部分显示以下公式：

   ```
   Day(GetDate())
   ```

   单击 **[!UICONTROL Finish]** 确认。

1. 重复此过程以检索对应于当前月份的出生月份。 要执行此操作，请单击 **[!UICONTROL Add]** 按钮并重复步骤3至10，更换 **[!UICONTROL Day]** 替换为 **[!UICONTROL Month]**.

   完整的查询如下所示：

   ![](assets/s_ncs_user_create_exp_exple03.png)

链接结果 **[!UICONTROL Query]** 活动到 **[!UICONTROL Email delivery]** 活动，以在所有收件人的生日当天向其列表发送电子邮件。

## 包括2月29日出生的收件人（可选） {#including-recipients-born-on-february-29th--optional-}

如果您希望包含所有在2月29日出生的收件人，则此用例将介绍如何计划向生日收件人的列表发送定期电子邮件 — 无论是否为闰年。

此用例的主要实施步骤包括：

* 选择收件人
* 选择是否为闰年
* 选择2月29日出生的任何收件人

为了设置此用例，我们创建了以下定位工作流：



如果当前年份 **不是闰年** 并且工作流在3月1日运行，我们需要选择昨天生日（2月29日）的所有收件人，并将其添加到收件人列表。 在任何其他情况下，无需执行其他操作。

### 步骤1：选择收件人 {#step-1--selecting-the-recipients}

配置之后 **[!UICONTROL Scheduler]** 活动以便工作流每天启动，标识其周年纪念日为当天的所有收件人。

>[!NOTE]
>
>如果今年是闰年，则所有在2月29日出生的收件人都会自动包含在内。

![](assets/birthday-workflow_usecase_2.png)

选择其生日对应于当前日期的收件人将显示在 [确定生日为的收件人](#identifying-recipients-whose-birthday-it-is) 部分。

### 步骤2：选择是否为闰年 {#step-2--select-whether-or-not-it-is-a-leap-year}

此 **[!UICONTROL Test]** 活动允许您检查是否为闰年，以及当前日期是否为3月1日。

如果测试得到验证（该年不是闰年 — 没有2月29日 — 并且当前日期确实是3月1日）， **[!UICONTROL True]** 已启用过渡，并将在2月29日出生的收件人添加到3月1日的投放中。 否则， **[!UICONTROL False]** 已启用过渡，只有生于当前日期的收件人才会收到投放。

将下面的代码复制并粘贴到 **[!UICONTROL Initialization script]** 部分 **[!UICONTROL Advanced]** 选项卡。

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

将以下条件添加到 **[!UICONTROL Conditional forks]** 部分：

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 步骤3：选择2月29日出生的任何收件人 {#step-3--select-any-recipients-born-on-february-29th}

创建 **[!UICONTROL Fork]** 活动，并将其中一个叫客过渡链接到 **[!UICONTROL Query]** 活动。

在此查询中，选择出生日期为2月29日的所有收件人。

![](assets/birthday-workflow_usecase_5.png)

将结果与 **[!UICONTROL Union]** 活动。

链接两个结果的结果 **[!UICONTROL Test]** 活动分支到 **[!UICONTROL Email delivery]** 活动，向所有生日收件人的列表发送电子邮件，即使那些在非闰年出生于2月29日的人也不例外。

## 创建循环投放 {#creating-a-recurring-delivery-in-a-targeting-workflow}

添加 **循环投放** 活动基于要发送的生日电子邮件模板。

>[!CAUTION]
>
>要执行工作流，必须启动与Campaign包相关的技术工作流。 有关详情，请参阅 [技术工作流列表](about-technical-workflows.md) 部分。
>
>如果为营销活动启用了批准步骤，则仅在确认这些步骤后才会发送投放。 有关详情，请参阅 [选择要批准的流程](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) 部分。

![](assets/birthday-workflow_usecase_1.png)
