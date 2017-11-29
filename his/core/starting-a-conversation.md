---
title: "Starting a Conversation2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50ab17ce-0e18-483f-89ee-a5333bd96840
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Starting a Conversation
The calls in this category are used to start a conversation between two programs.  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Accept_Conversation](../Topic/Accept_Conversation%20\(CPI-C\)1.md)( **cmaccp**)  
 Issued by the invoked program to accept the incoming conversation and set certain conversation characteristics. Upon successful execution of this call, Common Programming Interface for Communications (CPI-C) generates a conversation identifier.  
  
 [Allocate](../Topic/Allocate%20\(CPI-C\)1.md)( **cmallc**)  
 Issued by the invoking program to allocate a conversation with the partner program, using the current conversation characteristics. CPI-C can also start a session between the local logical unit (LU) and partner LU if one does not already exist. The type of conversation allocated depends on the conversation type characteristic—mapped or basic.  
  
 [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md)( **cminit**)  
 Issued by the invoking program to obtain a conversation identifier and to set the initial values for the conversation's characteristics. The initial values are derived from side information associated with the symbolic destination name or are CPI-C defaults.  
  
 After issuing **Initialize_Conversation**, the invoking program can issue any of the following **Set_** calls to change the initial conversation characteristics. These calls cannot be issued after **Allocate** has been issued.  
  
|Call|Sets|  
|----------|----------|  
|[Set_Conversation_Security_Password](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md) (**cmscsp**)|Security password|  
|[Set_Conversation_Security_Type](../Topic/Set_Conversation_Security_Type%20\(CPI-C\)2.md)(**cmscst**)|Conversation security type|  
|[Set_Conversation_Security_User_ID](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md) (**cmscsu**)|Security user identifier|  
|[Set_Conversation_Type](../Topic/Set_Conversation_Type%20\(CPI-C\)2.md) (**cmsct**)|Conversation type|  
|[Set_Mode_Name](../Topic/Set_Mode_Name%20\(CPI-C\)1.md) (**cmsmn**)|Mode name|  
|[Set_Partner_LU_Name](../Topic/Set_Partner_LU_Name%20\(CPI-C\)1.md) (**cmspln**)|Partner LU name|  
|[Set_Return_Control](../Topic/Set_Return_Control%20\(CPI-C\)1.md) (**cmsrc**)|Return control|  
|[Set_Sync_Level](../Topic/Set_Sync_Level%20\(CPI-C\)2.md) (**cmssl**)|Synchronization level|  
|[Set_TP_Name](../Topic/Set_TP_Name%20\(CPI-C\)2.md) (**cmstpn**)|Program name|