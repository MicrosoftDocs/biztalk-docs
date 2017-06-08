---
title: "Configuring Local Host Settings (X12-Transaction Set Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e31b41c3-49fc-46ef-ab69-889e30dfc58e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Local Host Settings (X12-Transaction Set Settings)
To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange. This consists of determining the target namespace associated with the schema, and determining the schema to be used. In this page of the party agreement, you enter the properties to be used in determining the target namespace. How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!NOTE]
>  This topic applies also to HIPAA-related settings.  
  
> [!IMPORTANT]
>  No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## Determining the Target Namespace  
 In the **Customize Target namespace** grid, you can set the target namespaces to one of the namespaces for the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In the grid, you associate a value of the **Target Namespace** element with values of the application sender (**GS2**) and transaction set identifier code (**ST1**). When BizTalk receives a message whose **GS2** and **ST1** data elements match those in a row of the grid, BizTalk will use the corresponding namespace to process the message. The values of the elements that you enter must be unique.  
  
 If a message does not have a match with the **GS2** and **ST1** data elements in any row of the grid, BizTalk Server will process the message using the namespace in the row for which the **Default** column is checked. That serves as the default target namespace. If no namespace is identified, BizTalk Server will use the default namespace of `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.  
  
> [!NOTE]
>  If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.  
  
> [!NOTE]
>  For an illustration of using this grid, run through the EDI Interface Developer tutorial, specifically setting up a party to receive an interchange from. For more information, see [Step 4: Configure a Party and Business Profile for Your Trading Partner](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md).  
  
### To configure local host settings for transaction sets  
  
1.  Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Local Host Settings**.  
  
3.  Select **Convert implied decimal format Nn to base 10 numeric value** to convert an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.  
  
    > [!NOTE]
    >  After this conversion, the intermediate XML may fail length validation. This occurs because the number in the base-10 numeric format includes a decimal, making its length one greater than the number in Nn format. You can resolve this issue by adding a value of **1** to the minimum/maximum length value.  
  
4.  As part of the transaction set validation settings, if you set **Trailing Separator Policy** to **Optional** or **Mandatory**, you can select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.  
  
5.  In the **Customize Target Namespace** section, do the following:  
  
    1.  Select the **Default** check box for the row that contains the default target namespace that you want to define.  
  
    2.  In the **For ST1** column, select a value for the Transaction set identifier code from the drop-down list.  
  
    3.  In the **GS2** column, enter an alphanumeric value for the Application sender with a minimum of two characters and a maximum of 15 characters. This is a required field.  
  
    4.  In the **Target Namespace** column, select from the drop-down list or enter the target namespace to be used for an interchange when no match is found between the data elements in any row of the grid and the fields in the interchange.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will compare with the values associated with the interchange it received.  
  
    5.  Repeat these steps for any other target namespaces to be used.  
  
    6.  To remove a target namespace from the list, select the row and click **Delete**.  
  
6.  Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (X12)](../core/configuring-transaction-set-settings-x12.md)