---
description: "Learn more about: Starting a Conversation"
title: "Starting a Conversation2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50ab17ce-0e18-483f-89ee-a5333bd96840
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Starting a Conversation
The calls in this category are used to start a conversation between two programs.  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Accept_Conversation](./accept-conversation-cpi-c-2.md)( **cmaccp**)  
 Issued by the invoked program to accept the incoming conversation and set certain conversation characteristics. Upon successful execution of this call, Common Programming Interface for Communications (CPI-C) generates a conversation identifier.  
  
 [Allocate](./allocate-cpi-c-2.md)( **cmallc**)  
 Issued by the invoking program to allocate a conversation with the partner program, using the current conversation characteristics. CPI-C can also start a session between the local logical unit (LU) and partner LU if one does not already exist. The type of conversation allocated depends on the conversation type characteristic—mapped or basic.  
  
 [Initialize_Conversation](./initialize-conversation-cpi-c-1.md)( **cminit**)  
 Issued by the invoking program to obtain a conversation identifier and to set the initial values for the conversation's characteristics. The initial values are derived from side information associated with the symbolic destination name or are CPI-C defaults.  
  
 After issuing **Initialize_Conversation**, the invoking program can issue any of the following **Set_** calls to change the initial conversation characteristics. These calls cannot be issued after **Allocate** has been issued.  
  
|Call|Sets|  
|----------|----------|  
|[Set_Conversation_Security_Password](./set-conversation-security-password-cpi-c-1.md) (**cmscsp**)|Security password|  
|[Set_Conversation_Security_Type](./set-conversation-security-type-cpi-c-1.md)(**cmscst**)|Conversation security type|  
|[Set_Conversation_Security_User_ID](./set-conversation-security-user-id-cpi-c-1.md) (**cmscsu**)|Security user identifier|  
|[Set_Conversation_Type](./set-conversation-type-cpi-c-1.md) (**cmsct**)|Conversation type|  
|[Set_Mode_Name](./set-mode-name-cpi-c-2.md) (**cmsmn**)|Mode name|  
|[Set_Partner_LU_Name](./set-partner-lu-name-cpi-c-2.md) (**cmspln**)|Partner LU name|  
|[Set_Return_Control](./set-return-control-cpi-c-2.md) (**cmsrc**)|Return control|  
|[Set_Sync_Level](./set-sync-level-cpi-c-1.md) (**cmssl**)|Synchronization level|  
|[Set_TP_Name](./set-tp-name-cpi-c-1.md) (**cmstpn**)|Program name|
