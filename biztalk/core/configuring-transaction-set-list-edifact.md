---
description: "Learn more about: Configuring Transaction Set List (EDIFACT)"
title: "Configuring Transaction Set List (EDIFACT)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configuring Transaction Set List (EDIFACT)
BizTalk Server enables you to define a list of transaction sets that must always be included or excluded while processing an EDI interchange. This section provides instructions on how to create the transaction set list.  
  
> [!IMPORTANT]
>  No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure a transaction set list  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Transaction Set Settings** section, click **Transaction Set List**.  
  
3.  Select **Support Transaction Sets from the List** option if you want to create a list of transaction sets that must always be processed.  
  
    > [!NOTE]
    >  You would use this option if you typically receive interchanges with specific transaction types, say APERAK. In that case, you add that transaction type to the list so that the transaction sets of other types are not processed at all.  
  
4.  Select **Exclude Transaction Sets from the List** option if you want to create a list of transaction sets that must not be processed.  
  
    > [!NOTE]
    >  You would use this option if you typically receive interchanges with varied transaction types. In that case, you add those transaction type to the list for which you do not get any transaction sets.  
  
5.  Click the empty cell in the **UNH2.1** column and from the drop-down select the transaction set type you want to support on exclude.  
  
6.  To delete a transaction type from the list, select the row for the transaction type, and click **Delete**.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Transaction Set Settings (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)
