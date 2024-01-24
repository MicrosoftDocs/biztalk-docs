---
description: "Learn more about: Configuring Local Host Settings (EDIFACT-Transaction Set Settings)"
title: "Configuring Local Host Settings (EDIFACT-Transaction Set Settings)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Local Host Settings (EDIFACT-Transaction Set Settings)
To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange. This consists of determining the target namespace associated with the schema, and determining the schema to be used. In this page of the party agreement, you enter the properties to be used in determining the target namespace. How BizTalk Server determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!IMPORTANT]
>  No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## Determining the Target Namespace  
 In the **Customize Target Namespace** grid, you can set the target namespace to one of the namespaces for the standard schemas shipped with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In the grid, you associate a value of the **Target Namespace** element with values of the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements. When BizTalk receives a message whose **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements match those in a row of the grid, BizTalk will use the corresponding namespace to determine the schema that it will use to process the message. The values of the elements that you enter must be unique.  
  
 If a message does not have a match with the **UNH2.1**, **UNH2.2**, **UNH2.3**, **UNH2.5**, **UNG2.1**, and **UNG2.2** elements in any row of the grid, BizTalk Server will process the message using the namespace in the row for which the **Default** column is checked. That serves as the default target namespace. If no namespace is identified, BizTalk will use the default namespace of `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006`.  
  
> [!NOTE]
>  If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.  
  
### To configure local host settings for transaction sets  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Local Host Settings**.  
  
3.  As part of the transaction set validation settings, if you set **Trailing Separator Policy** to **Optional** or **Mandatory**, you can select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.  
  
4.  Select **Use Dot (.) as decimal separator** to enable BizTalk Server include a dot (.) in the XML message created out of an interchange that contains a decimal number.  
  
5.  In the **Customize Target Namespace** section, do the following:  
  
    1.  Select the **Default** check box for the row that contains the default target namespace that you want to define.  
  
    2.  In the **UNH2.1** column, specify the message type. (maximum, six characters).  
  
    3.  In the **UNH2.2**  column, specify the message version number. (minimum, one character; maximum, three characters).  
  
    4.  In the **UNH2.3** column, specify the message release number. (minimum, one character; maximum, three characters).  
  
    5.  In the **UNH2.5** column, specify the assigned code. (maximum, six characters. Must be alphanumeric).  
  
    6.  In the **UNG2.1** column, enter an alphanumeric value for the application sender identification with a minimum of one character and a maximum of 35 characters. This field is required.  
  
    7.  In the **UNG2.2** column, enter an alphanumeric value for the application sender code qualifier with a minimum of one character and a maximum of four characters. This field is optional.  
  
    8.  In the **Target Namespace** column, select from the drop-down list or enter the target namespace to be used for an interchange when no match is found between the data elements in any row of the grid and the fields in the interchange.  
  
        > [!NOTE]
        >  These will be the values that BizTalk Server will compare with the values associated with the interchange it received.  
  
    9. Repeat these steps for any other target namespaces to be used.  
  
    10. To remove a target namespace from the list, select the row and click **Delete**.  
  
6.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)
