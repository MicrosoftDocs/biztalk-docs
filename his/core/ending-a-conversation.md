---
title: "Ending a Conversation1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c49373f-d286-444c-9d6b-106e97351dbd
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Ending a Conversation
The following calls end a conversation:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Deallocate](../Topic/Deallocate%20\(CPI-C\)2.md)( **cmdeal**)  
 Deallocates a conversation between two programs. Before deallocating the conversation, this call performs the equivalent of the [Flush](../Topic/Flush%20\(CPI-C\)1.md) or [Confirm](../Topic/Confirm%20\(CPI-C\)1.md) call, depending on the current conversation synchronization level and deallocate type.  
  
 [Set_Deallocate_Type](../Topic/Set_Deallocate_Type%20\(CPI-C\)2.md)( **cmsdt**)  
 Specifies how the conversation is to be deallocated. The deallocation instructions specified by this call take effect when **Deallocate** is issued or when the send type is set to CM_SEND_AND_DEALLOCATE and [Send_Data](../Topic/Send_Data%20\(CPI-C\)1.md) is issued.