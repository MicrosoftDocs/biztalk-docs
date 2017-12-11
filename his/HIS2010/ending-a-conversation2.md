---
title: "Ending a Conversation2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4859c068-7f86-4222-b49b-0f277a3f64e7
caps.latest.revision: 3
---
# Ending a Conversation
The following calls end a conversation:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Deallocate](../HIS2010/deallocate-cpi-c-2.md)( **cmdeal**)  
 Deallocates a conversation between two programs. Before deallocating the conversation, this call performs the equivalent of the [Flush](../HIS2010/flush-cpi-c-1.md) or [Confirm](../HIS2010/confirm-cpi-c-1.md) call, depending on the current conversation synchronization level and deallocate type.  
  
 [Set_Deallocate_Type](../HIS2010/set-deallocate-type-cpi-c-2.md)( **cmsdt**)  
 Specifies how the conversation is to be deallocated. The deallocation instructions specified by this call take effect when **Deallocate** is issued or when the send type is set to CM_SEND_AND_DEALLOCATE and [Send_Data](../HIS2010/send-data-cpi-c-1.md) is issued.