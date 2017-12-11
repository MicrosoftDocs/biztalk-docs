---
title: "Initial Conversation Characteristics2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29b516d8-9799-4a40-855e-344d1d72b930
caps.latest.revision: 3
---
# Initial Conversation Characteristics
Common Programming Interface for Communications (CPI-C) maintains a set of internal values called characteristics for each conversation. Some characteristics affect the overall operation of the conversation, such as the conversation type. Others affect the behavior of specific calls, such as the receive type.  
  
 Many of these characteristics are initially derived from the side information table (see [Side Information for CPI-C Programs](../HIS2010/side-information-for-cpi-c-programs2.md)) in memory. [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md) specifies the symbolic destination name (*sym_dest_name*) associated with the wanted side information table entry.  
  
 The following table lists the initial values of the conversation characteristics and tells which call can change a given value.  
  
|Characteristic|Initial value set by Initialize_Conversation|Initial value set by Accept_Conversation|Can be changed by|  
|--------------------|---------------------------------------------------|-----------------------------------------------|-----------------------|  
|Conversation state|CM_INITIALIZE_STATE|CM_RECEIVE_STATE|Depends on call|  
|Conversation type|CM_MAPPED_ CONVERSATION|The value specified by the invoking program.|[Set_Conversation_Type](../HIS2010/set-conversation-type-cpi-c-2.md)|  
|Deallocate type|CM_DEALLOCATE_ SYNC_LEVEL|CM_DEALLOCATE_ SYNC_LEVEL|[Set_Deallocate_Type](../HIS2010/set-deallocate-type-cpi-c-2.md)|  
|Error direction|CM_RECEIVE_ERROR|CM_RECEIVE_ ERROR|[Set_Error_Direction](../HIS2010/set-error-direction-cpi-c-2.md)|  
|Fill|CM_FILL_LL|CM_FILL_LL|[Set_Fill](../HIS2010/set-fill-cpi-c-2.md)|  
|Log data|Null|Null|[Set_Log_Data](../HIS2010/set-log-data-cpi-c-1.md)|  
|Log data length|0|0|[Set_Log_Data](../HIS2010/set-log-data-cpi-c-1.md)|  
|Mode name|The mode name contained in the side information. If no *sym_dest_name* is specified, this is a null string.|The mode name for the session on which the conversation startup request arrived.|[Set_Mode_Name](../HIS2010/set-mode-name-cpi-c-1.md)|  
|Mode name length|Length of mode name. If no *sym_dest_name* is specified, this is zero.|Length of mode name.|[Set_Mode_Name](../HIS2010/set-mode-name-cpi-c-1.md)|  
artner LU name|The partner logical unit (LU) name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The partner LU name for the session on which the conversation startup request arrived.|[Set_Partner_LU_Name](../HIS2010/set-partner-lu-name-cpi-c-1.md)|  
|Partner LU name length|Length of partner LU name. If no *sym_dest_name* is specified, this is 1.|Length of partner LU name.|[Set_Partner_LU_Name](../HIS2010/set-partner-lu-name-cpi-c-1.md)|  
|Partner program name|The program name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|Not applicable.|[Set_TP_Name](../HIS2010/set-tp-name-cpi-c-2.md)|  
|Partner program name length|Length of partner program name. If no *sym_dest_name* is specified, this is 1.|Not applicable.|[Set_TP_Name](../HIS2010/set-tp-name-cpi-c-2.md)|  
|Password|The password contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_Password](../HIS2010/set-conversation-security-password-cpi-c-2.md)|  
|Password length|Length of password. If no *sym_dest_name* is specified, this is 1.|Length of password.|[Set_Conversation_Security_Password](../HIS2010/set-conversation-security-password-cpi-c-2.md)|  
|Prepare-to-receive type|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|[Set_Prepare_To_Receive_Type](../HIS2010/set-prepare-to-receive-type-cpi-c-2.md)|  
eceive type|CM_RECEIVE_AND_ WAIT|CM_RECEIVE_AND_ WAIT|[Set_Receive_Type](../HIS2010/set-receive-type-cpi-c-1.md)|  
|Return control|CM_WHEN_SESSION_ ALLOCATED|Not applicable.|[Set_Return_Control](../HIS2010/set-return-control-cpi-c-1.md)|  
|Security type|The security type contained in the side information.|The value specified by the invoking program.|[Set_Conversation_Security_Type](../HIS2010/set-conversation-security-type-cpi-c-2.md)|  
|Send type|CM_BUFFER_DATA|CM_BUFFER_DATA|[Set_Send_Type](../HIS2010/set-send-type-cpi-c-1.md)|  
|Synchronization level|CM_NONE|The value specified by the invoking program.|[Set_Sync_Level](../HIS2010/set-sync-level-cpi-c-2.md)|  
|User identifier|The user identifier contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_User_ID](../HIS2010/set-conversation-security-user-id-cpi-c-2.md)|  
|User identifier length|Length of user identifier. If no *sym_dest_name* is specified, this is 1.|Length of user identifier.|[Set_Conversation_Security_User_ID](../HIS2010/set-conversation-security-user-id-cpi-c-2.md)|