---
title: "Managing Batches | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82755840-4e00-4fed-80e0-1a22b248c0bf
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Batches
How to control manually the release of batched interchanges, using the controls at the top of the **Batch Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box (in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console) for both X12 and EDIFACT encoding. This involves the following controls:  
  
- **Starting a batch**. Activates an instance of the batching orchestration. After you select the **Start** button, batching elements are collected when the instance is within the activation range.  
  
- **Overriding a batch**. Creates a batch using existing elements and immediately sends it. After the batch is sent, the batching orchestration resumes batch processing according to the established settings.  
  
- **Stopping a batch**. Deactivates an activated instance of the batching orchestration. After you select the **Stop** button, the orchestration creates a batch from existing batch elements, delivers the interchange to the EDI send pipeline, and terminates.  
  
  The controls act upon a single batch configuration.  
  
  The actions that BizTalk takes when you press the **Start** button depend upon the **Filter** criteria, **Release** criteria, and **Activation** range settings on the **Batch Configuration** page. The filter criteria determine which messages are batched. The release criteria determine when batches are released. The activation range properties determine whether an activated instance of the batching orchestration will collect elements for batching. For more information about these settings, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).  

This topic shows you how to start, stop, override, and delete batches.  

> [!NOTE]
>  For instructions on how to configure batches, see [Configuring X12 Batching](../core/configuring-batching-x12.md) or [Configuring EDIFACT Batching](../core/configuring-batching-edifact.md). 
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
> [!NOTE]
>  A member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group can start, stop, or override a batch, but cannot change any configuration setting related to batching. You must be a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to change batch configuration.  
  
## Start, stop, and override batches  
  
1. Open **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand the BizTalk group, and select **Parties**.  
  
2. In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to start, stop, or override.  
  
3. In the one-way agreement tab of the **Agreement Properties**, select the **Batch Configuration** page.  
  
4. On the **Batch Configuration** page, select the tab for the batch that you want to start, stop, or override.  
  
5. Verify that the filter criteria, release criteria, and activation range properties are as they should be.  
  
   > [!NOTE]
   >  If you are a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, but not the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group, you can start, stop, or override batches. But, you cannot change batch configuration settings. The settings are visible to you, but if you change a setting, and then select **OK**, you get a permissions error.  
  
6. If an instance of the batching orchestration has not been activated, select **Start** to activate an instance.  
  
   > [!NOTE]
   >  - You can tell that an instance of the batching orchestration has not been activated if the **Start** button is enabled, and **Batching is not activated** is displayed just beneath the **Start** control.  
   >  - If you have clicked the **Start** button, and an instance of the batching orchestration has been activated, but no elements are being collected for the batch, then verify that the datetime in the **Activation** text box has transpired. If not, the **Activation** date must be set to the current date or earlier.  
  
7. To send a batched interchange when the release criteria have not been met, select **Override**.  
  
   > [!NOTE]
   >  Selecting **Override** results in a batched interchange being sent, but does not affect the activation status of the batching orchestration instance, the activation criteria, or the release criteria.  
  
8. To deactivate the instance of the batching orchestration, select **Stop**.  
  
   > [!NOTE]
   >  Selecting **Stop** results in a batched interchange being sent, and the batching orchestration instance being terminated.  
  
9. Select **OK** or **Cancel** to close the **Agreement Properties**.  

## Delete batches  
  
1. In **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, select **Parties**.  
  
2. In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to delete.  
  
3. In the one-way agreement tab of the **Agreement Properties** dialog box, select the **Batch Configuration** page.  
  
4. On the **Batch Configuration** page, select the tab for the batch that you want to delete.  
  
5. On the right-hand corner of the tab page, select **Delete**.  
  
6. Select **OK** to close the **Agreement Properties**.  

  
## See Also  
 [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md)  
 [Managing EDI and AS2 Solutions](../core/managing-edi-and-as2-solutions.md)