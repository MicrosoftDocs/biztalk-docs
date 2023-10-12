---
title: "Configure Scheduling for a Receive Location"
description: Configure a start date, end date, time zone, add a recurrence for receive locations on BizTalk Server.
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Configure a receive location schedule in BizTalk Server

This topic describes how to use the BizTalk Server Administration console to configure scheduling properties for a receive location. You can specify the dates when you want the receive location to start and stop processing messages. You can also specify certain times of the day during which you want the receive location to process messages.  
  
## Prerequisites

 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Configure scheduling for a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure scheduling for a receive location.  
  
3. Click **Receive Locations**, right-click the receive location, and click **Properties**.  
  
4. In the left pane, click **Schedule**, configure scheduling properties as described in the following table, and then click **OK**.  
  
    - **Time zone**: Select the time zone. This time zone determines all the date time values when using this feature.

      This setting applies to:

      - BizTalk Server 2020 and newer
      - BizTalk Server 2016 with Feature Pack 1 and newer

    - **Automatically Adjust for Daylight Saving Time**: When checked, the schedule automatically adjusts to the daylight saving time of the time zone you chose. This option has no impact on the schedule if the time zone you chose doesn't have a daylight savings time, or daylight savings time isn't observed.

      This setting applies to:

      - BizTalk Server 2020 and newer
      - BizTalk Server 2016 with Feature Pack 1 and newer

    - **Start date**: Select this check box, and then from the pull-down calendar, select the date on which the receive location starts processing messages. To change the year, click the displayed year.  
    - **Stop date**: Select this check box, and then from the pull-down calendar, select the date on which the receive location stops processing messages. This property is optional. If you do not specify a stop date, the receive location remains active until it is disabled.
    - **Enable service window**: Select this check box to configure the receive location to receive messages only at specified times of the day, then specify the times in the **Start time and Stop time** boxes. If the check box is cleared, the receive location receives messages at any time. The default value is false (cleared).
    - **Start time**: Enter the time when the receive location should begin to receive messages. This box is available only when the **Enable service window** check box is selected.
    - **Stop time**: Enter the time when the receive location should cease to receive messages. This box is available only when the **Enable service window** check box is selected.
    - **Recurrence**: See [Enable recurrence schedule](#enable-recurrence-schedule) in this article.

## Enable recurrence schedule

This setting applies to:

- BizTalk Server 2020 and newer
- BizTalk Server 2016 with Feature Pack 1 and newer

1. In the **BizTalk Server Administration**, right-click your receive locations > **Properties**.
2. On the **Scheduling** page, select **Enable service window**. For **Start Time** and **Stop time**, set the initial time the schedule is allowed to run:

    > [!div class="mx-imgBorder"]
    > ![Enable Service Windows for Receive Port to configure scheduling on BizTalk Server](../core/media/enable-service-windows-for-receive-port.PNG)

3. The additional scheduling options are shown:

    > [!div class="mx-imgBorder"]
    > ![Advanced Scheduling for Receive Port on BizTalk Server](../core/media/advanced-scheduling-for-receive-port.PNG)

4. The **Recurrence** property runs the receive port every day, week, or month that you choose:

    1. Use the **Daily** recurrence to run the receive port every *x* number of days, starting on the **From** date you choose, and only within the **service window** you choose:

        > [!div class="mx-imgBorder"]
        > ![Daily recurrence schedule in BizTalk Server](../core/media/daily-schedule.png)

    2. Use the **Weekly** recurrence to run the receive port on a specific day within a week, and only within the **service window** you choose:

        > [!div class="mx-imgBorder"]
        > ![Weekly recurrence schedule in BizTalk Server](../core/media/weekly-schedule.png)

    3. Use the **Monthly** recurrence to run the receive port on a monthly schedule. The **Days** and **On** options are available.

        Use the **Days** recurrence to run the receive port on specific dates within the **months** you choose:

        > [!div class="mx-imgBorder"]
        > ![Run the recurrence schedule on specific dates within a month on BizTalk Server](../core/media/monthly-schedule.PNG)

        Use the **On** recurrence to run the receive port on specific days of the month:

        > [!div class="mx-imgBorder"]
        > ![Run the recurrence schedule on specific days of the month on BizTalk Server](../core/media/monthly-on-schedule.PNG)

5. Select **OK** to save your changes.

## See also

 [Managing Receive Locations](../core/managing-receive-locations.md)
