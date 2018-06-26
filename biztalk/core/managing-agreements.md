---
title: "Managing Agreements | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.resultsobject.agreement"
ms.assetid: e9c6cdd1-8c17-4b1e-a556-2b287593bb9d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Agreements
A Trading Partner Agreement (TPA) is defined as a definitive and binding agreement between two trading partners for transacting messages over a specific B2B Protocol. See [Trading Partner Agreement](../core/trading-partner-agreement.md). 

This topics shows you how to create, view, edit, enable, disable, or delete an agreement.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

## Create an agreement  

1. Open **BizTalk Server Administration**, expand the BizTalk group, and select **Parties**. 
2. In the **Parties and Business Profiles** page, right-click a business profile that is part of the agreement you are creating, select **New**, and then select **Agreement**.  

3. In the **General Properties**: 

   1. In the **Agreement Parameters** section, do the following:  


      |   Use this   |                                                                                                                                                                                                                                                                                                                                                                                                                                                     To do this                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      |--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |   **Name**   |                                                                                                                                                                                                                                                                                                                                                                                                                                           Enter a name for the agreement                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |    **ID**    |                                                                                                                                                                                                                                                                                                                                                                Lists unique identification for the agreement. This text box is read-only, and display the agreement ID after you select **Apply** for the first time, and the settings are accepted.                                                                                                                                                                                                                                                                                                                                                                |
      |  **Status**  |                                                                                                                                                                                                                                                                                                                                                 Specifies the status of the agreement. By default, an agreement is created in an **Active** state. If you want the agreement to be disabled when it is first created, select **Disabled** from the drop-down list.                                                                                                                                                                                                                                                                                                                                                  |
      | **Protocol** | Specifies the protocol for the agreement.<br /><br /> -   For an X12 encoding protocol, select **X12** from the drop-down list. See [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md)<br />-   For an EDIFACT encoding protocol, select **EDIFACT** from the drop-down list.  See [Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md).<br />-   For an AS2 encoding protocol, select **AS2** from the drop-down list. See [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md). <br/><br/>**Note**<br/>  The agreement properties are provided in the one-way agreement tabs. The one-way agreement tabs appear after you have selected the second profile with which the agreement will be created. You select the second partner in the following steps. |


   2. In the **First Partner** section, do the following:  


      |     Use this     |                                                                                                      To do this                                                                                                       |
      |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **Name**     |                                             Displays the partner name that has the business profile for which you are creating the agreement. This text box is read-only.                                             |
      |   **Profile**    |                                                        Displays the name of the profile for which you are creating the agreement. This text box is read-only.                                                         |
      | **Protocol Set** | If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list. If you did not create an X12 protocol set as part of the business profile, you can leave this empty. |


   3. In the **Second Partner** section, do the following:  

      |Use this|To do this|  
      |--------------|----------------|  
      |**Name**|From the drop-down select a party that has the business profile with which you want to create an agreement.|  
      |**Profile**|From the drop-down select a profile with which you want to create an agreement.|  
      |**Protocol Set**|If you created an X12 protocol set as part of the business profile, you can select that from the drop-down list. If you did not create an X12 protocol set as part of the business profile, you can leave this empty.|  

      > [!TIP]
      >  Press `CTRL`, select the business profiles that will be part of the agreement, right-click either business profile, select **New**, and then select **Agreement**. The values for partner name and business profiles for both the partners are automatically populated in the **Agreement Properties** dialog box.  

      > [!NOTE]
      >  As soon as you select the other profile, two tabs are added next to the **General** tab. Each tab represents a one-way agreement between the two parties. You use the tabs to enter the agreement properties.  

   4. Select the **Enable Agreement** check box to enable the agreement, and do the following:  


      |    Use this     |                                        To do this                                        |
      |-----------------|------------------------------------------------------------------------------------------|
      |    **From**     |               Select the date and time from which the agreement is valid.                |
      | **No End Date** | Select this option if you do not want to set an end date when the agreement is disabled. |
      |   **End By**    |       Select this option to enter the date and time until the agreement is valid.        |


   5. In the **Common Host Settings** section, do the following:  


      |                Use this                 |                                                                                                                                                                     To do this                                                                                                                                                                     |
      |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       **Log errors to event log**       |                                         Select this option if you want to log any errors generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.<br/><br/>**Note**:  Does not apply to AS2 agreements.                                         |
      |      **Log warnings to event log**      |                                       Select this option if you want to log any warnings generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer. <br/><br/>**Note**:  Does not apply to AS2 agreements.                                        |
      |          **Turn ON reporting**          | Select this option to display status entries for all EDI messages (incoming and outgoing) on the **EDI Interchange and Correlated ACK Status** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. If unchecked, no status entries are displayed. |
      | **Store message payload for reporting** |                                                                       If you selected **Turn ON reporting**, select this option to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database. <br/><br/>**Note**:  Does not apply to AS2 agreements.                                                                        |


4. In the **General** tab, on the **Contact Information** page, do the following:  

   1.  In the **Contact1** tab, enter the contact information for the party’s profile with which you are creating an agreement. This data is for information purposes only; it is not used by the BizTalk Runtime.  

   2.  To add another tab for contact, select the **New Contact** tab.  

   3.  To delete a contact tab, select **Delete** from the top right corner of the tab page.  

       > [!NOTE]
       >  You cannot delete the **Contact1** tab. You can only delete the new tabs that you add.  

5. In the **General** tab, on the **Additional Properties** page, do the following:  

   > [!NOTE]
   >  The information you enter on this page is not used by the BizTalk Server for any processing; this data is for information purposes only.  

   1.  In the **Additional Properties** grid, enter name-value pairs for any information that you want to add related to the party or agreement.  Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want.  

        To delete a name-value pair, select the row, and select **Delete** from the top-right corner.  

   2.  In the **Text 1**, **Text 2**, and **Agreement** text boxes, enter information about the agreement with a party.  

   3.  Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action validates the settings.  

## View or change an agreement  

1.  In **BizTalk Server Administration**, select **Parties**. 

2. In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to view or edit.  

3.  In the **Agreements** section, right-click the agreement, and then select **Properties**.  

4.  In the **Agreement Properties**, view or edit the agreement. For the values that can be entered on the different tabs and pages in the **Agreement Properties** dialog box, see the following:  

    |For this|See this|  
    |--------------|--------------|  
    |For X12 agreement|[Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md)|  
    |For EDIFACT agreement|[Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md)|  
    |For AS2 agreement|[Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md)|  

5.  Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action validates the settings. 

## Enable or disable an agreement  

1.  In **BizTalk Server Administration**, select **Parties**. 

2. In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to edit.  

3.  In the **Agreements** section, right-click the agreement, and then select **Enable** or **Disable**. 

    > [!NOTE]
    >  When an agreement is first created, it is always enabled by default. The **Enable** option is available only when the agreement is disabled. The **Disable** option is available only when the agreement is enabled.  

## Delete an agreement  
1.  In **BizTalk Server Administration**, select **Parties**. 

2.  In the **Parties and Business Profiles** page, select any of the two business profile that have the agreement that you want to delete.  

3.  In the **Agreements** section, right-click the agreement that you want to delete, and then select **Delete**.  

4.  In the **Confirm delete agreement** dialog box, select **Yes** to delete the agreement.  


## See Also  
 [Managing EDI and AS2 Solutions](../core/managing-edi-and-as2-solutions.md)