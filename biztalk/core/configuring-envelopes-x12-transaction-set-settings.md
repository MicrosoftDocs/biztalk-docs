---
description: "Learn more about: Configuring Envelopes (X12-Transaction Set Settings)"
title: "Configuring Envelopes (X12-Transaction Set Settings)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Envelopes (X12-Transaction Set Settings)
In the **Envelops** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS and ST segments for an X12-encoded interchange that it sends to the party. A GS segment identifies and specifies a functional group for an X12-encoded interchange. An ST segment is the message header for an X12-encoded interchange.  
  
 In this page, you associate values of the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements with values of the **Transaction Type**, **Version/Release**, and **Target namespace** data elements. When BizTalk determines that a BizTalk XML message has the values set for the **Transaction Type**, **Version/Release**, and **Target namespace** elements in a row of the grid, BizTalk will populate the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements in the envelope of the outgoing interchange with the values from the same row of the grid. The values of the **Transaction Type**, **Version/Release**, and **Target namespace** elements must be unique.  
  
> [!NOTE]
>  If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.  
  
> [!NOTE]
>  This topic applies also to HIPAA-related settings.  
  
> [!IMPORTANT]
>  All properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are enabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To define the GS and ST segments  
  
1.  Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Envelopes**.  
  
3.  In a row of the grid, enter the following:  
  
    -   For the **Transaction Type** field, select a value for the transaction set identifier code from the drop-down list.  
  
    -   For **Version/Release**, enter an alphanumeric value with a minimum of one character and a maximum of 12 characters.  
  
    -   For **Target namespace** elements, select a value from the drop-down list, or enter a namespace.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will compare with the values associated with the interchange it is building.  
  
4.  In the same row of the grid, enter the following:  
  
    -   For **GS1**, select a value for the functional code from the drop-down list. This is an optional field.  
  
    -   For **GS2**, enter an alphanumeric value for the application sender with a minimum of two characters and a maximum of 15 characters. This is a required field.  
  
    -   For **GS3**, enter an alphanumeric value for the application receiver with a minimum of two characters and a maximum of 15 characters. This is a required field.  
  
    -   For **GS4**, select **CCYYMMDD** or **YYMMDD**. This is an optional field  
  
    -   For **GS5**, select **HHMM**, **HHMMSS**, or **HHMMSSdd**. This is an optional field  
  
    -   For **GS7**, select a value for the responsible agency from the drop-down list. This is an optional field.  
  
    -   For **GS8**, enter an alphanumeric value for the document identified with a minimum of one character and a maximum of 12 characters. This is an optional field.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will enter in the GS fields of the interchange it is building if the **Transaction Type**, **Version/Release**, and **Target namespace** elements in the same row are a match for those associated with the interchange.  
  
5.  Repeat steps 3 and 4 to enter additional rows into the grid.  
  
6.  For one row in the grid, click **Default** to designate it as the default row.  
  
    > [!NOTE]
    >  If a message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements in any row, BizTalk Server will populate the message with the values for the **GS1**, **GS2**, **GS3**, **GS5**, **GS7**, and **GS8** elements in the default row. These values will be used even if the message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements of the default row.  
  
    > [!NOTE]
    >  If no default is selected, incoming documents that do not match the **Transaction Type**, **Version/Release**, and **Target namespace** elements of any rows will be suspended.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (X12)](../core/configuring-transaction-set-settings-x12.md)
