---
title: "Configuring General Settings (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75c1ca3e-19a0-42f7-910e-dd07c24d1ed4
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring General Settings (X12)
As part of the general settings, you specify agreement name, the protocol it will use (X12 or EDIFACT), the parties and profiles that the agreement is between, and whether to have reporting enabled for all messages processed through the agreement. You can also specify the party contact information as part of the agreement.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

### To configure general agreement settings  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click a business profile that must be part of the agreement that you are creating, point to **New**, and then click **Agreement**.  

2. The following tables list the different properties and the values to be specified for the properties in the **General Properties** page.  

   1. In the **Agreement Parameters** section, do the following:  


      |   Use this   |                                                                                                     To do this                                                                                                     |
      |--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |   **Name**   |                                                                                          Specify a name for the agreement                                                                                          |
      |    **ID**    |               Lists unique identification for the agreement. This text box is not editable and will display the agreement ID after you click **Apply** for the first time and settings are accepted.               |
      |  **Status**  | Specifies the status of the agreement. By default, an agreement is created in an **Active** state. If you want the agreement to be disabled when it is first created, select **Disabled** from the drop-down list. |
      | **Protocol** |                                                  Specifies the protocol for the agreement. For an X12 encoding protocol, select **X12** from the drop-down list.                                                   |


   2. In the **First Partner** section, do the following:  


      |     Use this     |                                                                                                      To do this                                                                                                       |
      |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **Name**     |                                           Displays the partner name that has the business profile for which you are creating the agreement. This text box is not editable.                                            |
      |   **Profile**    |                                                       Displays the name of the profile for which you are creating the agreement. This text box is not editable.                                                       |
      | **Protocol Set** | If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list. If you did not create an X12 protocol set as part of the business profile, you can leave this empty. |


   3. In the **Second Partner** section, do the following:  

      |Use this|To do this|  
      |--------------|----------------|  
      |**Name**|From the drop-down select a party that has the business profile with which you want to create an agreement.|  
      |**Profile**|From the drop-down select a profile with which you want to create an agreement.|  
      |**Protocol Set**|If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list. If you did not create an X12 protocol set as part of the business profile, you can leave this empty.|  

      > [!TIP]
      >  Press `CTRL`, select the business profiles that will be part of the agreement, right-click either business profile, point to **New**, and then click **Agreement**. The values for partner name and business profiles for both the partners will be automatically populated in the **Agreement Properties** dialog box.  

      > [!NOTE]
      >  As soon as you select the other profile, two tabs are added next to the **General** tab. Each tab represents a one-way X12 agreement between the two parties. You use the tabs to specify interchange and transaction set related settings in the tabs. For more information, see [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md) and [Configuring Transaction Set Settings (X12)](../core/configuring-transaction-set-settings-x12.md).  

   4. Select the **Enable Agreement** check box to enable the agreement and do the following:  


      |    Use this     |                                        To do this                                         |
      |-----------------|-------------------------------------------------------------------------------------------|
      |    **From**     |             Select the date and time from which the agreement will be valid.              |
      | **No End Date** | Select this option if you do not want to set an end date when the agreement is disabled.  |
      |   **End By**    | Select this option and specify the date and time until which the agreement will be valid. |


   5. In the **Common Host Settings** section, do the following:  


      |                Use this                 |                                                                                                                                                                       To do this                                                                                                                                                                       |
      |-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       **Log errors to event log**       |                                                                      Select this option if you want to log any errors generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.                                                                      |
      |      **Log warnings to event log**      |                                                                     Select this option if you want to log any warnings generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.                                                                     |
      |          **Turn ON reporting**          | Select this option to display status entries for all EDI messages (incoming and outgoing) on the **EDI Interchange and Correlated ACK Status** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. If unchecked, no status entries will be displayed. |
      | **Store message payload for reporting** |                                                                                                     If you selected **Turn ON reporting**, select this option to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.                                                                                                     |


3. In the **General** tab, on the **Contact Information** page, do the following:  

   1.  In the **Contact1** tab, enter the contact information for the party’s profile with which you are creating an agreement. This data is for information purposes only; it will not be used by the BizTalk Runtime.  

   2.  To add another tab for contact, click the **New Contact** tab.  

   3.  To delete a contact tab, click **Delete** from the top right corner of the tab page.  

       > [!NOTE]
       >  You cannot delete the **Contact1** tab. You can only delete the new tabs that you add.  

4. In the **General** tab, on the **Additional Properties** page, do the following:  

   > [!NOTE]
   >  The information you specify on this page is not used by the BizTalk Server for any processing; this data is for information purposes only.  

   1.  In the **Additional Properties** grid, enter name-value pairs for any information that you want to add related to the party or agreement.  Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want.  

        To delete a name-value pair, select the row and click **Delete** from the top-right corner.  

   2.  In the **Text 1**, **Text 2**, and **Agreement** text boxes, enter information about the agreement with a party.  

       > [!IMPORTANT]
       >  If you click **OK** or **Apply** after providing all the values listed in this page, you will get an error. That is because the mandatory values to create an agreement are not yet provided. These are ISA5 to ISA8 values on the **Identifiers** page of each one-way agreement tab.  

## Next Steps  
 You must now configure the interchange or transaction set settings for the agreement. For instructions see [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md) or [Configuring Transaction Set Settings (X12)](../core/configuring-transaction-set-settings-x12.md).  

## See Also  
 [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md)