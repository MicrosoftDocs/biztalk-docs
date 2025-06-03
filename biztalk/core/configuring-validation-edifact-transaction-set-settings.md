---
description: "Learn more about: Configuring Validation (EDIFACT-Transaction Set Settings)"
title: "Configuring Validation (EDIFACT-Transaction Set Settings)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configuring Validation (EDIFACT-Transaction Set Settings)
The transaction set validation settings define how BizTalk Server validates the transaction sets received from a party. As part of validation settings you can specify which type of validation BizTalk Server will perform on an incoming interchange  
  
> [!IMPORTANT]
>  No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure ACK processing and validation settings  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Validation**.  
  
3.  In the grid, you can define different validation settings for different transaction sets. In the **Validation** page, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Default**|Select the check box to define a default validation setting.|  
    |**UNH2.1**|Click the empty cell in the column and from the drop-down select a transaction type.|  
    |**Edi Type Validation**|Select **EDI type** to enable EDI (data element) validation on the interchange receiver. This validation performs EDI validation on transaction-set data elements, validating data types, length restrictions, and empty data elements and training separators. For more information, see [EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md). **Note:**  Even if this property is not selected, cross-field/segment validation will be performed if it is turned on in the schema annotation.|  
    |**Extended validation**|Select this to enable extended (BizTalk XSD) validation of interchanges received from the interchange sender. This includes validation of field length, optionality, and repeat count in addition to XSD data type validation. For more information, see [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md). **Note:**  You can select this check box only if **Edi Type Validation** is selected.|  
    |**Allow leading and trailing zeroes and spaces**|Select to specify that an EDI interchange received from the party will not fail validation if a data element in an EDI interchange does not conform to its length requirement because of leading (or trailing) zeroes or trailing spaces, but does conform to its length requirement when they are removed. **Note:**  You can select this check box only if **Edi Type Validation** is selected.|  
    |**Trailing Separator Policy**|-   Select **Not Allowed** if you do not want to allow trailing delimiters and separators in an interchange received from the interchange sender. If the interchange contains trailing delimiters and separators, it will be declared invalid.<br />-   Select **Optional** to accept interchanges with or without trailing delimiters and separators.<br />-   Select **Mandatory** if the received interchange must contain trailing delimiters and separators.|  
  
     You can add as many rows as you want to define validation settings for specific interchanges.  
  
     To delete a validation setting, select the row and click **Delete**.  
  
    > [!NOTE]
    >  Editing the properties in the grid can be a little difficult. Instead, you can select the row to be editing and then edit the same properties in the **Edit Selected Row** section. The settings you provide here are reflected in the selected row.  
  
4.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)
