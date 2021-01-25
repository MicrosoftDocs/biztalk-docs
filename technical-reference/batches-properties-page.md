---
description: "Learn more about: Batches Properties Page"
title: Batches Properties Page
TOCTitle: Batches Properties Page
ms:assetid: 881a356b-88f9-42c4-a52d-0348ea2638e8
ms:mtpsurl: https://msdn.microsoft.com/library/Dd210274(v=BTS.80)
ms:contentKeyID: 51529475
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.EDI.party.batches
---

# Batches Properties Page

 

The properties included in this page define how BizTalk Server generates and sends an EDI batch to the party. The role of the party is as an interchange receiver from BizTalk Server; the role of BizTalk Server is as an interchange sender to the party.

This page of the **EDI Properties** dialog box is displayed by right-clicking a party in the **Parties** node of the BizTalk Server Administration Console, clicking **EDI Properties** and then clicking **Batches**.


> [!NOTE]
> <P>If you change batch configuration settings while the batching orchestration is processing a batch, the new configuration settings will not be picked up for that batch. This can result in validation errors in the send pipeline.</P>




> [!NOTE]
> <P>To speed up activation of the batching orchestration party on a development server, you can decrease the polling interval for the batching SQL adapter receive location (BatchControlMessageRecvLoc) on that server. We recommend you set the polling interval for a development server to 30 seconds.</P>



## Batches

**Batches**  
Select **All** to display all batch configurations for this party.

Select **Active** or **Inactive** to display only the active or inactive batch configurations.

The default value is **All**.

**New Batch**  
Click to create a new batch configuration.

**Batch Name tab**  
Select a tab to view a specific batch configuration. Selecting **New Batch** creates a new batch configuration.

The default value is **Batch\#**.


> [!NOTE]
> <P>The default Batch Name is ‘Batch’ followed by a number. If a batch configuration already exists that uses this name, the number will be incremented. For example, if you already have a batch named Batch1 and select <STRONG>New Batch</STRONG>, the default name for the new batch will be Batch2.</P>




> [!NOTE]
> <P>The value of this tab is set to the same value as the <STRONG>Batch name</STRONG> field in the Identification section.</P>



**Refresh**  
Click to refresh the status of the batching orchestration of the batch configuration currently displayed.

**Start**  
Starts a batching orchestration instance based on this batch configuration. Messages will be collected for batching after the time specified in the **Activation** section.

**Override**  
Click to override the existing batch criteria, with the result that a batch is created using existing elements and then sent immediately. After this, the batching orchestration resumes batch processing according to the established settings.

**Stop**  
Click to deactivate the batching orchestration manually.

**Delete**  
Click to delete the currently selected batching configuration.

## Identification

**Batch name**  
Enter the name of the batch configuration.

The default value is **Batch\#**.


> [!NOTE]
> <P>The default Batch Name is ‘Batch’ followed by a number. If a batch configuration already exists that uses this name, the number will be incremented. For example, if you already have a batch named Batch1 and select <STRONG>New Batch</STRONG>, the default name for the new batch will be Batch2.</P>



**Document standard**  
Select X12/HIPAA or EDIFACT/EANCOM to specify the EDI message type that will be processed by this batch configuration.

The default value is X12/HIPAA.

**Batch Id**  
The ID of this batch configuration, used as part of the batching orchestration subscription.

**Orchestration instance id**  
The instance ID of the batch orchestration instance that is currently activated for this batch configuration.

## Filter

**Batch filter**  
Click **Filter**, and then enter filter criteria for batching. For more information, see [Batch Filter Page](batch-filter-page.md).

The text box below **Batch filter** displays the current filter.


> [!NOTE]
> <P>When making changes to the batch filter, it will take 15 minutes for the new filter settings to take effect. This refresh time cannot be changed.</P>



## Release

**Schedule**  
Select to create and send a batch according to a predetermined schedule. To enter the schedule, click **Scheduler**.

**Scheduler**  
If you selected **Schedule**, click **Scheduler** to display the **Batch Schedule** dialog box, in which you can enter the specific batch scheduling information. For more information, see [Batch Schedule Page](batch-schedule-page.md).

**Maximum number of transaction sets in**  
Select to create and then send a batch when a specific number of transaction sets is available for batch processing. After checking the **Maximum number of transaction sets in** field, select the part of the message to count the transaction sets in (either **Group** or **Interchange**), and then enter the maximum number of transaction sets to be in the batched group or interchange.

The maximum number of transaction sets allowed in an interchange is 2147483647.

**Maximum number of characters in an interchange**  
Select to create and then send a batch when a specific number of characters is available for batch processing. After checking the **Maximum number of characters in an interchange** field, enter the maximum number of characters in the batched group or interchange.

The batching orchestration will accumulate batching elements until the character count in those elements (minus the count in the envelope) exceeds the maximum count. It will then batch all but the last element (which caused the count to exceed the maximum count).

For the maximum number of characters, enter a number large enough that you will generate meaningful batches. That number should at least be greater than the maximum number of characters in a message. A number that is too small could result in suspended messages, as any message larger than the limit will be suspended.

The maximum number of characters allowed in an interchange is 9223372036854775807.

**External release trigger**  
Select to create and then send a batch when an external trigger is executed by an application external to BizTalk Server.


> [!NOTE]
> <P>This property indicates that an external release message is required for batch release. The <STRONG>Override</STRONG> button and <STRONG>Activation</STRONG> range controls remain valid if the <STRONG>External release trigger</STRONG> property has been selected.</P>



## Activation

**Start immediately**  
Select to begin batching messages as soon as the orchestration instance is started. If unchecked, select a date and time for the activation of the batching orchestration and messages will be collected for batching after this time.

The default value is checked.

## Termination

**No end date**  
Select to specify that there will be no end date at which the batching orchestration will be deactivated.

This is the default for the batch end date.

**End after (occurrences)**  
Select to specify that the batching orchestration will be deactivated after a certain number of batches have been generated.

In the associated field, enter the number of batches after which the batching orchestration will be deactivated. The maximum number of occurrences allowed is 2147483647.

The default value is empty.

**End by**  
Select a date and time for the deactivation of the batching orchestration. Messages will no longer be collected for batching as of this time.

Select a date from the calendar, and enter the time.

The default value is the date and time that the dialog box was opened.

## In This Section

  - [Batch Filter Page](batch-filter-page.md)

  - [Batch Schedule Page](batch-schedule-page.md)

