---
description: "Learn more about: Initial Conversation Characteristics"
title: "Initial Conversation Characteristics1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Initial Conversation Characteristics
Common Programming Interface for Communications (CPI-C) maintains a set of internal values called characteristics for each conversation. Some characteristics affect the overall operation of the conversation, such as the conversation type. Others affect the behavior of specific calls, such as the receive type.  
  
 Many of these characteristics are initially derived from the side information table (see [Side Information for CPI-C Programs](../core/side-information-for-cpi-c-programs1.md)) in memory. [Initialize_Conversation](./initialize-conversation-cpi-c-1.md) specifies the symbolic destination name (*sym_dest_name*) associated with the wanted side information table entry.  
  
 The following table lists the initial values of the conversation characteristics and tells which call can change a given value.  
  
|Characteristic|Initial value set by Initialize_Conversation|Initial value set by Accept_Conversation|Can be changed by|  
|--------------------|---------------------------------------------------|-----------------------------------------------|-----------------------|  
|Conversation state|CM_INITIALIZE_STATE|CM_RECEIVE_STATE|Depends on call|  
|Conversation type|CM_MAPPED_ CONVERSATION|The value specified by the invoking program.|[Set_Conversation_Type](./set-conversation-type-cpi-c-1.md)|  
|Deallocate type|CM_DEALLOCATE_ SYNC_LEVEL|CM_DEALLOCATE_ SYNC_LEVEL|[Set_Deallocate_Type](./set-deallocate-type-cpi-c-1.md)|  
|Error direction|CM_RECEIVE_ERROR|CM_RECEIVE_ ERROR|[Set_Error_Direction](./set-error-direction-cpi-c-1.md)|  
|Fill|CM_FILL_LL|CM_FILL_LL|[Set_Fill](./set-fill-cpi-c-1.md)|  
|Log data|Null|Null|[Set_Log_Data](./set-log-data-cpi-c-2.md)|  
|Log data length|0|0|[Set_Log_Data](./set-log-data-cpi-c-2.md)|  
|Mode name|The mode name contained in the side information. If no *sym_dest_name* is specified, this is a null string.|The mode name for the session on which the conversation startup request arrived.|[Set_Mode_Name](./set-mode-name-cpi-c-2.md)|  
|Mode name length|Length of mode name. If no *sym_dest_name* is specified, this is zero.|Length of mode name.|[Set_Mode_Name](./set-mode-name-cpi-c-2.md)|  
Partner LU name|The partner logical unit (LU) name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The partner LU name for the session on which the conversation startup request arrived.|[Set_Partner_LU_Name](./set-partner-lu-name-cpi-c-2.md)|  
|Partner LU name length|Length of partner LU name. If no *sym_dest_name* is specified, this is 1.|Length of partner LU name.|[Set_Partner_LU_Name](./set-partner-lu-name-cpi-c-2.md)|  
|Partner program name|The program name contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|Not applicable.|[Set_TP_Name](./set-tp-name-cpi-c-1.md)|  
|Partner program name length|Length of partner program name. If no *sym_dest_name* is specified, this is 1.|Not applicable.|[Set_TP_Name](./set-tp-name-cpi-c-1.md)|  
|Password|The password contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_Password](./set-conversation-security-password-cpi-c-1.md)|  
|Password length|Length of password. If no *sym_dest_name* is specified, this is 1.|Length of password.|[Set_Conversation_Security_Password](./set-conversation-security-password-cpi-c-1.md)|  
|Prepare-to-receive type|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|CM_PREP_TO_ RECEIVE_SYNC_ LEVEL|[Set_Prepare_To_Receive_Type](./set-prepare-to-receive-type-cpi-c-1.md)|  
Receive type|CM_RECEIVE_AND_ WAIT|CM_RECEIVE_AND_ WAIT|[Set_Receive_Type](./set-receive-type-cpi-c-2.md)|  
|Return control|CM_WHEN_SESSION_ ALLOCATED|Not applicable.|[Set_Return_Control](./set-return-control-cpi-c-2.md)|  
|Security type|The security type contained in the side information.|The value specified by the invoking program.|[Set_Conversation_Security_Type](./set-conversation-security-type-cpi-c-1.md)|  
|Send type|CM_BUFFER_DATA|CM_BUFFER_DATA|[Set_Send_Type](./set-send-type-cpi-c-2.md)|  
|Synchronization level|CM_NONE|The value specified by the invoking program.|[Set_Sync_Level](./set-sync-level-cpi-c-1.md)|  
|User identifier|The user identifier contained in the side information. If no *sym_dest_name* is specified, this is a single blank.|The value specified by the invoking program.|[Set_Conversation_Security_User_ID](./set-conversation-security-user-id-cpi-c-1.md)|  
|User identifier length|Length of user identifier. If no *sym_dest_name* is specified, this is 1.|Length of user identifier.|[Set_Conversation_Security_User_ID](./set-conversation-security-user-id-cpi-c-1.md)|
