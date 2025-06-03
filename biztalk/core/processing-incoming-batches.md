---
description: "Learn more about: Processing Incoming Batches"
title: "Processing Incoming Batches"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Processing Incoming Batches
When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a batched EDI interchange, it can either split the interchange into its transaction sets, processing each one separately, or it can preserve the interchange, processing all transaction sets as a group.  
  
 You determine batch processing in the **Local Host Settings** page of the one-way agreement tabs in the **Agreement Properties** dialog box for both X12 and EDIFACT agreements. When you preserve the interchange, you have the choice to suspend either the interchange or the transaction sets if an error occurs.  
  
## In This Section  
  
-   [Splitting a Batched EDI Interchange](../core/splitting-a-batched-edi-interchange.md)  
  
-   [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md)  
  
-   [Preserving a Received Batched EDI Interchange](../core/preserving-a-received-batched-edi-interchange.md)
