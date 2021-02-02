---
description: "Learn more about: Configuring Batching (EDIFACT)"
title: "Configuring Batching (EDIFACT) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f711ff4b-702b-419b-9c17-dce60ea437a0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Batching (EDIFACT)
Batches define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an EDI batches to the party.  
  
> [!IMPORTANT]
>  All properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement. The **New Batch** button is disabled on this page.  
>   
>  The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the **New Batch** button is disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure batching settings  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Interchange Settings** section, click **Batching Configuration**.  
  
3.  From the **Batch Configuration** page click **New Batch** to create a new batch configuration. A **Batch1** tab is added.  
  
4.  In the **Identification** section of the tab perform the following steps:  
  
    1.  Enter the **Batch** name. This value is used as the tab identifier for this batch configuration.  
  
    2.  Enter a description of this batch configuration in **Batch description**.  
  
    3.  **Batch ID** is a read-only text box that displays a unique batch ID after you apply the settings for the batch.  
  
    4.  **Orchestration instance ID** is a read-only text box that displays the batching orchestration instance ID that the batch is associated with. An orchestration instance ID is displayed after a batch is started.  
  
5.  In the **Filter** section of the tab perform the following steps:  
  
    1.  Click **Filter**.  
  
    2.  In the **Batch Filter** dialog box, enter the property, operator and values to build the subscription filter for the batching orchestration. These filter clauses determine which transaction sets the routing orchestration will route to the MessageBox for batching.  
  
        > [!NOTE]
        >  To specify that all messages to a group will be batched, set the party property in the batch filter to the party name.  
  
        > [!NOTE]
        >  For more information about the batching process, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).  
  
    3.  To delete a row, select the row and click **Delete**.  
  
    4.  To move a row up or down, click the **Move Up** or **Move Down** buttons.  
  
6.  In the **Release** section of the tab perform the following steps:  
  
    1.  Select **Schedule** to create and send a batch according to a predetermined schedule. To define the schedule, click **Scheduler** and then proceed as follows:  
  
        > [!NOTE]
        >  A batch schedule may be affected by special events. An example is the onset of daylight savings time. If a batch were scheduled on an hourly basis less than an hour after the onset of daylight savings time, the batch would not be created and sent after clocks were reset by incrementing the hour. You can compensate for special events that result in a skipped batch by clicking the **Start** button on the **Batches** page to start the batching orchestration manually. You may also have to stop a duplicated batch.  
  
        -   To send a batch on an hourly basis, select **Hourly**. From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time. For **Subsequent release every**, select from the drop-down list whether the period is in **Hours** or **Minutes**, and then enter the number of hours or minutes that will separate each batch.  
  
        -   To send a batch on a daily basis, select **Daily**. From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time. For **Subsequent release every**, enter the number of days that will separate each batch.  
  
        -   To send a batch on a weekly basis, select **Weekly**. From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time. For **Subsequent release every**, enter the number of weeks between the week of the first release and the week of each subsequent release. Then select the days of the week that the batch will be released on.  
  
            > [!NOTE]
            >  The first release will be made at the date and set in the **First release at** field, even if that day of the week was not selected in the dialog box.  
  
            > [!NOTE]
            >  If you selected one or more days of the week in the dialog box, a release will be made on any selected day of that first week that comes after the first release. For example, if Monday and Friday have been selected, and the first release was on a Wednesday, a release will be made on Friday of the first week. Subsequent releases will occur *n* weeks after the first week, with *n* determined by the value in the **Subsequent release every** field. Release will occur on each day of the week selected in the dialog box.  
  
        -   Select **Send empty batch signal** to send an empty batch signal if no messages have been received by the batching orchestration when the batch is scheduled to be sent.  
  
    2.  Select **Maximum number of transaction sets in** to create and send a batch whenever a certain number of transaction sets or messages has been routed to the MessageBox for batching. Select the part of the message to count the transaction sets in (either **Group** or **Interchange**), and then enter the maximum number of transaction sets to be in the batched group or interchange.  
  
         For example, if you want to batch two interchanges into one batch select **Interchange** from the drop-down and enter `2` in the text box.  
  
    3.  Select **Maximum number of characters in an interchange** to create and send a batch when a specific number of characters are available for batch processing. Enter the maximum number of characters in the batched group or interchange.  
  
         The batching orchestration will accumulate batching elements until the character count in those elements (minus the count in the envelope) exceeds the maximum count. It will then batch all but the last element (which caused the count to exceed the maximum count).  
  
        > [!NOTE]
        >  For the maximum number of characters, enter a number large enough that you will generate meaningful batches. That number should at least be greater than the total number of characters in the batch headers and the maximum number of characters in a message. A number that is too small could result in empty batches.  
  
    4.  Select **External release trigger** to create and then send a batch when an external trigger is executed by an application external to BizTalk Server. For more information about how to set up this mechanism, see [Implementing an External Batch Release Mechanism](../core/implementing-an-external-batch-release-mechanism.md).  
  
        > [!NOTE]
        >  The **Override** button and **Activation range** controls remain valid if the **External release** trigger property has been selected.  
  
7.  In the **Activation** section of the tab perform the following steps:  
  
    1.  Select **Start Immediately** to have the batching orchestration begin batching messages immediately.  
  
         To start the batching orchestration on a specific date, clear the **Start Immediately** box and select a date and time to activate the batching orchestration.  
  
8.  In the **Termination** section of the tab perform the following steps:  
  
    1.  Keep **No end date** selected if you do not want to specify an end date for the batching orchestration to be deactivated.  
  
    2.  Select **End after (occurrences)** to specify that the batching orchestration will be deactivated after a certain number of batches have been generated. Enter the number desired in the text box.  
  
    3.  Select **End by** to specify an end date that the batching orchestration will be deactivated. Messages will no longer be collected for batching as of this time. Select an end date from the calendar or change the date or time directly in the text box.  
  
9. Click **Apply** to apply the batch settings you provided in the previous steps. After you click **Apply**, a batch ID is created and is displayed in the **Batch ID** text field in the **Identification** section.  
  
    > [!NOTE]
    >  A message **Batching is not activated** will be displayed under the **Start** button.  
  
10. Click **Start** to activate a batching orchestration manually.  
  
    > [!NOTE]
    >  To make sure that the batching orchestration will be promptly activated when you click the **Start** button, update the polling interval for the SQL adapter in the BatchControlMessageReccvLoc receive location. For more information, see [Walkthrough (X12): Sending Batched EDI Interchanges](../core/walkthrough-x12-sending-batched-edi-interchanges.md).  
  
    > [!NOTE]
    >  After you click **Start**, click **Refresh**. It can take a while to associate the batch with the orchestration instance. If you click **Refresh** before the batch is associated with the orchestration, you see the message **Batching is activated, Batching orchestration not instantiated yet**. Click **Refresh** again to see the associated orchestration’s instance ID in the **Orchestration instance ID** text box. The message **Batching is activated** is displayed under the **Start** button.  
  
11. Click **Override** to forces the batching orchestration to send a batch, whether or not the release criteria have been met. Using this option overrides the existing batch criteria, with the result that a batch is created using existing elements and then sent immediately. After this, the batching orchestration resumes batch processing according to the established settings.  
  
12. Click **Stop** to terminate an active batching orchestration without sending a batch and deactivate the batching orchestration manually.  
  
13. Click **Refresh** to refresh the status of the batching orchestration.  
  
    > [!NOTE]
    >  You can use the drop-down list at the top of **the Batch Configuration** page to filter the batch configuration tabs displayed by selecting **All** (to see tabs for all batches), **Active** (to see tabs for active batches), or **Inactive** (to see tabs for inactive batches).  
  
    > [!NOTE]
    >  If you change the configuration settings while the orchestration is processing a batch, the new settings will not be applied to that batch. This can result in validation errors in the send pipeline.  
  
    > [!NOTE]
    >  To speed up activation of the batching orchestration party on a development server, you can decrease the polling interval for the batching SQL adapter receive location (BatchControlMessageRecvLoc) on that server. We recommend you set the polling interval for a development server to 30 seconds.  
  
14. Click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (EDIFACT)](../core/configuring-interchange-settings-edifact.md)
