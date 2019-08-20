---
title: "Ending a Conversation1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c49373f-d286-444c-9d6b-106e97351dbd
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Ending a Conversation
The following calls end a conversation:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Deallocate](./deallocate-cpi-c-1.md)( **cmdeal**)  
 Deallocates a conversation between two programs. Before deallocating the conversation, this call performs the equivalent of the [Flush](./flush-cpi-c-2.md) or [Confirm](./confirm-cpi-c-2.md) call, depending on the current conversation synchronization level and deallocate type.  
  
 [Set_Deallocate_Type](./set-deallocate-type-cpi-c-1.md)( **cmsdt**)  
 Specifies how the conversation is to be deallocated. The deallocation instructions specified by this call take effect when **Deallocate** is issued or when the send type is set to CM_SEND_AND_DEALLOCATE and [Send_Data](./send-data-cpi-c-2.md) is issued.