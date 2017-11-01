---
title: "Initial Conversation Characteristics1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99bc34b9-e870-46be-a4c2-605624e7e417
caps.latest.revision: 3
---
# Initial Conversation Characteristics
Common Programming Interface for Communications (CPI-C) maintains a set of internal values called characteristics for each conversation. Some characteristics affect the overall operation of the conversation, such as the conversation type. Others affect the behavior of specific calls, such as the receive type.  
  
 Many of these characteristics are initially derived from the side information table (see [Side Information for CPI-C Programs](../core/side-information-for-cpi-c-programs.md)) in memory. [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md) specifies the symbolic destination name (*sym_dest_name*) associated with the wanted side information table entry.  
  
 The following table lists the initial values of the conversation characteristics and tells which call can change a given value.  
  
|Characteristic|Initial value set by Initialize_Conversation|Initial value set by Accept_Conversation|Can be changed by|  
|--------------------|---------------------------------------------------|-----------------------------------------------|-----------------------|  
|Conversation state|CM_INITIALIZE_STATE|CM_RECEIVE_STATE|Depends on call|  
|Conversation type|CM_MAPPED_ CONVERSATION|The value specified by the invoking program.|[Set_Conversation_Type](../Topic/Set_Conversation_Type%20\(CPI-C\)2.md)|  
|Deallocate type|CM_DEALLOCATE_ SYNC_LEVEL|CM_DEALLOCATE_ SYNC_LEVEL|[Set_Deallocate_Type](../Topic/Set_Deallocate_Type%20\(CPI-C\)2.md)|  
|Error direction|CM_RECEIVE_ERROR|CM_RECEIVE_ ERROR|[Set_Error_Direction](../Topic/Set_Error_Direction%20\(CPI-C\)2.md)|  
|Fill|CM_FILL_LL|CM_FILL_LL|[Set_Fill](../Topic/Set_Fill%20\(CPI-C\)2.md)|  
|Log data|Null|Null|[Set_Log_Data](../Topic/Set_Log_Data%20\(CPI-C\)1.md)|  
|Log data length|0|0|[Set_Log_Data](../Topic/Set_Log_Data%20\(CPI-C\)1.md)|  
|Mode name|The mode name contained in the side information. If no *sym_dest_name* is specified, this is a null string.|The mode name for the session on which the conversation startup request arrived.|[Set_Mode_Name](../Topic/Set_Mode_Name%20\(CPI-C\)1.md)|  
|Mode name length|Length of mode name. If no *sym_dest_name* is specified, this is zero.|Length of mode name.|[Set_Mode_Name](../Topic/Set_Mode_Name%20\(CPI-C\)1.md)|  
artner LU name|The partner logical unit (LU) name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The partner LU name for the session on which the conversation startup request arrived.|[Set_Partner_LU_Name](../Topic/Set_Partner_LU_Name%20\(CPI-C\)1.md)|  
|Partner LU name length|Length of partner LU name. If no *sym_dest_name* is specified, this is 1.|Length of partner LU name.|[Set_Partner_LU_Name](../Topic/Set_Partner_LU_Name%20\(CPI-C\)1.md)|  
|Partner program name|The program name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|Not applicable.|[Set_TP_Name](../Topic/Set_TP_Name%20\(CPI-C\)2.md)|  
|Partner program name length|Length of partner program name. If no *sym_dest_name* is specified, this is 1.|Not applicable.|[Set_TP_Name](../Topic/Set_TP_Name%20\(CPI-C\)2.md)|  
|Password|The password contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_Password](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md)|  
|Password length|Length of password. If no *sym_dest_name* is specified, this is 1.|Length of password.|[Set_Conversation_Security_Password](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md)|  
|Prepare-to-receive type|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|[Set_Prepare_To_Receive_Type](../Topic/Set_Prepare_To_Receive_Type%20\(CPI-C\)2.md)|  
eceive type|CM_RECEIVE_AND_ WAIT|CM_RECEIVE_AND_ WAIT|[Set_Receive_Type](../Topic/Set_Receive_Type%20\(CPI-C\)1.md)|  
|Return control|CM_WHEN_SESSION_ ALLOCATED|Not applicable.|[Set_Return_Control](../Topic/Set_Return_Control%20\(CPI-C\)1.md)|  
|Security type|The security type contained in the side information.|The value specified by the invoking program.|[Set_Conversation_Security_Type](../Topic/Set_Conversation_Security_Type%20\(CPI-C\)2.md)|  
|Send type|CM_BUFFER_DATA|CM_BUFFER_DATA|[Set_Send_Type](../Topic/Set_Send_Type%20\(CPI-C\)1.md)|  
|Synchronization level|CM_NONE|The value specified by the invoking program.|[Set_Sync_Level](../Topic/Set_Sync_Level%20\(CPI-C\)2.md)|  
|User identifier|The user identifier contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_User_ID](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md)|  
|User identifier length|Length of user identifier. If no *sym_dest_name* is specified, this is 1.|Length of user identifier.|[Set_Conversation_Security_User_ID](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md)|