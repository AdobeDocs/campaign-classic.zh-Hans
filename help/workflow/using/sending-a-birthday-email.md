---
title: 发送生日电子邮件
seo-title: 发送生日电子邮件
description: 发送生日电子邮件
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f3006ac7178b4fc3091859ca8a7225864da9524a

---


# 发送生日电子邮件{#sending-a-birthday-email}

## 简介 {#introduction}

此用例介绍如何计划在收件人生日当天向收件人列表发送循环电子邮件。

要设置此用例，我们创建了以下定位工作流：

![](assets/birthday-workflow_usecase_1.png)

此（每日运行）工作流将选择在当前日期有生日的所有收件人。

此用例也可以以视频的形式找到。 有关此内容的详细信息，请参阅创 [建工作流视频](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 。

为此，请创建营销活动，然后单击选 **[!UICONTROL Targeting and workflows]** 项卡。 有关详细信息，请参阅在工 [作流中构建主目标部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) 。

然后，按照以下步骤操作：

## 安排发送 {#configuring-the-scheduler}

1. 首先，添加一个 **调度程序** ，以触发每天发送交付。 在以下示例中，每天清晨6点创建交付。

   ![](assets/recur_delivery2.png)


## 识别生日为谁的收件人 {#identifying-recipients-whose-birthday-it-is}

在配置活 **[!UICONTROL Scheduler]** 动以使工作流每天启动之后，请标识出生日期等于当前日期的所有收件人。

为此，请应用以下步骤：

1. 将活动拖放到 **[!UICONTROL Query]** 工作流中，然后双击它。
1. 单击“编 **辑查询** ”链接并选择 **[!UICONTROL Filtering conditions]**。

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. 单击列的第一个单元 **[!UICONTROL Expression]** 格，然后单 **[!UICONTROL Edit expression]** 击以打开表达式编辑器。

   ![](assets/s_ncs_user_create_exp_exple.png)

1. 单击 **[!UICONTROL Advanced selection]** 以选择筛选模式。

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. 选择并 **[!UICONTROL Edit the formula using an expression]** 单击以 **[!UICONTROL Next]** 显示表达式编辑器。
1. 在函数列表中，双击， **[!UICONTROL Day]**&#x200B;可通过节点访问该函 **[!UICONTROL Date]** 数。 此函数返回表示与作为参数传递的日期相对应的日期的数字。

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. 在可用字段列表中，双击 **[!UICONTROL Birth date]**。 然后，编辑器的上半部分显示以下公式：

   ```
   Day(@birthDate)
   ```

   Click **[!UICONTROL Finish]** to confirm.

1. 在查询编辑器中，在列的第一个单元格 **[!UICONTROL Operator]** 中，选择 **[!UICONTROL equal to]**。

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. 接下来，单击第二列()的第一个单元&#x200B;**[!UICONTROL Value]**&#x200B;格，然后单击以 **[!UICONTROL Edit expression]** 打开表达式编辑器。
1. 在函数列表中，双击， **[!UICONTROL Day]**&#x200B;可通过节点访问该函 **[!UICONTROL Date]** 数。
1. 双击该函 **[!UICONTROL GetDate]** 数以检索当前日期。

   ![](assets/s_ncs_user_create_exp_exple04.png)

   编辑器的上半部分显示以下公式：

   ```
   Day(GetDate())
   ```

   Click **[!UICONTROL Finish]** to confirm.

1. 重复此步骤以检索与当前月份对应的出生月份。 为此，请单击按钮 **[!UICONTROL Add]** 并重复步骤3到10，替换 **[!UICONTROL Day]** 为 **[!UICONTROL Month]**。

   完整的查询如下：

   ![](assets/s_ncs_user_create_exp_exple03.png)

将活动的结果链 **[!UICONTROL Query]** 接到活 **[!UICONTROL Email delivery]** 动，以向所有收件人的生日列表发送电子邮件。

## 包括2月29日出生的收件人（可选） {#including-recipients-born-on-february-29th--optional-}

如果要包含2月29日出生的所有收件人，此用例介绍如何计划向收件人列表发送循环电子邮件以供其生日——无论这是否为闰年。

此用例的主要实施步骤是：

* 选择收件人
* 选择是否为闰年
* 选择2月29日出生的收件人

要设置此用例，我们创建了以下定位工作流：



如果当前年 **度不是闰年** ，而工作流在3月1日运行，则我们需要选择昨天（2月29日）生日的所有收件人，并将其添加到收件人列表。 在任何其他情况下，都不需要执行任何其他操作。

### 第1步：选择收件人 {#step-1--selecting-the-recipients}

在配置活 **[!UICONTROL Scheduler]** 动以使工作流每天开始之后，请标识周年日为当天的所有收件人。

>[!NOTE]
>
>如果当前年份是闰年，则自动包含2月29日出生的所有收件人。

![](assets/birthday-workflow_usecase_2.png)

在“识别生日对应当前日期的收件人”部分中，选择 [其生日对应的收件人](#identifying-recipients-whose-birthday-it-is) 。

### 第2步：选择它是否为闰年 {#step-2--select-whether-or-not-it-is-a-leap-year}

活动 **[!UICONTROL Test]** 允许您检查它是否是闰年以及当前日期是否为3月1日。

如果测试得到验证（年不是闰年——没有2月29日——而当前日期确实是3月1日），则转换将启用，2月29日出生的接收者将添加到3月1日的发送中。 **[!UICONTROL True]** 否则， **[!UICONTROL False]** 将启用过渡，并且只有在当前日期出生的收件人将收到传送。

将下面的代码复制并粘贴到选 **[!UICONTROL Initialization script]** 项卡的部 **[!UICONTROL Advanced]** 分中。

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

在部分中添加以下条 **[!UICONTROL Conditional forks]** 件：

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 第3步：选择2月29日出生的收件人 {#step-3--select-any-recipients-born-on-february-29th}

创建活 **[!UICONTROL Fork]** 动，并将其中一个出站过渡链接到活 **[!UICONTROL Query]** 动。

在此查询中，选择出生日期为2月29日的所有收件人。

![](assets/birthday-workflow_usecase_5.png)

将结果与活动结 **[!UICONTROL Union]** 合。

将两个活动分支的结 **[!UICONTROL Test]****[!UICONTROL Email delivery]** 果关联到一个活动，以向所有收件人的生日列表发送电子邮件，即使是在非闰年的2月29日出生的收件人也是如此。

## 创建重复交付 {#creating-a-recurring-delivery-in-a-targeting-workflow}

根据您 **要发送的生日电子邮件模板** ，添加重复的提交活动。

>[!CAUTION]
>
>要执行工作流，必须启动与营销活动流程相关的技术工作流。 有关详细信息，请参阅营销活动 [流程工作流列表部分](../../workflow/using/campaign.md) 。
>
>如果为营销活动启用了批准步骤，则仅在确认这些步骤后才会发送提交。 有关详细信息，请参阅选 [择要批准的流程一节](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) 。

![](assets/birthday-workflow_usecase_1.png)
