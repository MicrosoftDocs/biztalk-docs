---
title: "Configuring Envelopes (EDIFACT-Transaction Set Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec140def-6155-4b8a-8489-6e0a530bd697
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Envelopes (EDIFACT-Transaction Set Settings)
In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the UNG and UNH segments for an EDIFACT-encoded interchange that it sends to the party.  
  
 The UNG segment is the header that identifies and specifies a functional group of an EDIFACT-encoded interchange. It contains information about the date and time that the functional group was prepared, together with the type and version of the document in the functional group.  
  
 The UNH segment is the message header segment of an EDIFACT-encoded interchange. It provides information about the message type, and the agency responsible for maintaining the publication of the message type. This segment indicates the start of a document in an interchange and the type of document that follows.  
  
 In the **Functional group header (UNG)** section, you associate **UNG** values with **UNH** values and a namespace. When BizTalk Server determines that a BizTalk XML message has the values set for the **UNH** elements and the **Target namespace** in a row of the grid, BizTalk Server will populate the **UNG** data elements with the values from the same row of the grid. The values of the **UNH** elements and the **Target namespace** must be unique.  
  
 If a message does not have a match with the **UNH** elements and the **Target namespace** in any row, BizTalk Server will populate the message with the values of the **UNG** elements in the default row. These values will be used even if the message does not have a match with the **UNH** elements and the **Target namespace** of the default row.  
  
 When the BizTalk engine determines that a BizTalk XML message has the values set for the UNH elements and the Target namespace, the engine will populate the UNG elements in the message with the values set for them in the grid, provided the **Create Grouping Segments** checkbox is checked.  
  
> [!NOTE]
>  In the **Functional group header (UNG)**  section, if you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.  
  
> [!IMPORTANT]
>  All properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are enabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To define the UNG and UNH segments  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Envelopes**.  
  
3.  In a row of the grid, enter the following values:  
  
    -   In the **For message type UNH2.1** column, enter a transaction set type. (Maximum, six characters).  
  
    -   In the **UNH2.2**  column, enter the message version number. (Minimum, one character; maximum, three characters).  
  
    -   In the **UNH2.3** column, enter the message release number. (Minimum, one character; maximum, three characters).  
  
    -   In the **UNH2.5** column, enter the assigned code. (Maximum, six characters. Must be alphanumeric).  
  
    -   In the **Target namespace** column, select the target namespace of the schema. This is a required field.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will compare with the values associated with the interchange it is building.  
  
4.  In the same row of the grid, enter the following values:  
  
    -   For the **UNG1** (Functional group identification), enter an alphanumeric value with a minimum of one character and a maximum of six characters. This is a required field.  
  
    -   For **UNG2.1** (Application sender identification), enter an alphanumeric value with a minimum of one character and a maximum of 35 characters. This is a required field.  
  
    -   For **UNG2.2** (Application sender code qualifier), enter an alphanumeric value, with a maximum of four characters. This is an optional field.  
  
    -   For **UNG3.1** (Application recipient identification), enter an alphanumeric value with a minimum of one character and a maximum of 35 characters. This is a required field.  
  
    -   For **UNG3.2** (Application recipient code qualifier), enter an alphanumeric value, with a maximum of four characters. This is an optional field.  
  
    -   For **UNG6** (Controlling agency), enter an alphanumeric value with a minimum of one and a maximum of two. This is a required field.  
  
    -   For **UNG7.1** (Message type version number), enter an alphanumeric value with a minimum of one character and a maximum of three characters. This is a required field.  
  
    -   For **UNG7.2** (Message type release number), enter an alphanumeric value with a minimum of one character and a maximum of three characters. This is a required field.  
  
    -   For **UNG7.3** (Association assigned code), enter an alphanumeric value with a minimum of 1 character and a maximum of 6 characters. This is a required field.  
  
    -   For **UNG8** (Application password), enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is a required field.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will enter in the UNG fields of the interchange it is building if the  **For message type UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in the same row are a match for those associated with the interchange.  
  
5.  Repeat steps 4 and 5 to enter additional rows into the grid.  
  
6.  For one row in the grid, click **Default** to designate it as the default row.  
  
    > [!NOTE]
    >  If a message does not have a match with the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in any row, BizTalk Server will populate the message with the values for the **UNG1**, **UNG2.1**, **UNG2.2**, **UNG3.1**, **UNG3.2**, **UNG6**, **UNG7.1**, **UNG7.2**, **UNG7.3**, and **UNG8** elements in the default row. These values will be used even if the message does not have a match with the **For message type UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements of the default row.  
  
    > [!NOTE]
    >  If no default row is selected, and the message does not have a match for the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, and **Target namespace** elements in any row, BizTalk will suspend the message.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)