---
title: "CPI-C Calls2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b1371ec-6d65-406c-b044-7315c459afc9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CPI-C Calls
This section describes the Common Programming Interface for Communications (CPI-C) calls. The following information is supplied for each call:  
  
- The pseudonym for the call and the actual C function name.  
  
- A definition of the call.  
  
- A list of the parameters used by the call and the data type for each parameter. The prototype of each function is declared in the WINCPIC.H file.  
  
- A description of each input and output parameter. The parameter names are pseudonyms and the actual names for these parameters are declared by the application program. The description includes the possible values of the parameter.  
  
- The conversation states in which the call can be issued.  
  
- The states to which the conversation can change upon return from the call. Conditions that do not cause a state change are not noted. For example, parameter checks and state checks do not cause a state change.  
  
- Additional information describing the use of the call.  
  
  **Data Types**  
  
  The data types for the parameters supplied to and received from CPI-C are established as symbolic constants by **#define** statements in the WINCPIC.H file. For example, CM_INT32 represents **signed long int** and CM_PTR represents **far \\***. Using symbolic constants improves the portability of CPI-C applications.  
  
  For ease of understanding, this reference presents the data types in absolute (not **#defined**) terms.  
  
  In writing applications, you should use the symbolic constants from the WINCPIC.H file.  
  
  **Symbolic Constants**  
  
  Most parameters supplied to and returned by CPI-C are 32-bit integers. To simplify coding, the values for these parameters are represented by meaningful symbolic constants, which are established by **#define** statements in the WINCPIC.H header file. For example, the value CM_MAPPED_CONVERSATION represents the integer 1. For the sake of readability, use only the symbolic constants when writing programs.  
  
  **Strings**  
  
  All strings are in ASCII format when passed across the CPI-C interface.  
  
  **Validity of output parameters**  
  
  The parameters returned by CPI-C are valid only if the CPI-C call is executed successfully, as indicated by a return code of CM_OK.  
  
## In This Section  
  
-   [Accept_Conversation](../core/accept-conversation-cpi-c-2.md)  
  
-   [Allocate](../core/allocate-cpi-c-2.md)  
  
-   [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md)  
  
-   [Confirm](../core/confirm-cpi-c-2.md)  
  
-   [Confirmed](../core/confirmed-cpi-c-2.md)  
  
-   [Convert_Incoming](../core/convert-incoming-cpi-c-1.md)  
  
-   [Convert_Outgoing](../core/convert-outgoing-cpi-c-1.md)  
  
-   [Deallocate](../core/deallocate-cpi-c-1.md)  
  
-   [Delete_CPIC_Side_Information](../core/delete-cpic-side-information-cpi-c-2.md)  
  
-   [Extract_Conversation_Security_Type](../core/extract-conversation-security-type-cpi-c-2.md)  
  
-   [Extract_Conversation_Security_User_ID](../core/extract-conversation-security-user-id-cpi-c-1.md)  
  
-   [Extract_Conversation_State](../core/extract-conversation-state-cpi-c-2.md)  
  
-   [Extract_Conversation_Type](../core/extract-conversation-type-cpi-c-2.md)  
  
-   [Extract_CPIC_Side_Information](../core/extract-cpic-side-information-cpi-c-1.md)  
  
-   [Extract_Mode_Name](../core/extract-mode-name-cpi-c-1.md)  
  
-   [Extract_Partner_LU_Name](../core/extract-partner-lu-name-cpi-c-1.md)  
  
-   [Extract_Sync_Level](../core/extract-sync-level-cpi-c-1.md)  
  
-   [Extract_TP_Name](../core/extract-tp-name-cpi-c-2.md)  
  
-   [Flush](../core/flush-cpi-c-2.md)  
  
-   [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md)  
  
-   [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md)  
  
-   [Receive](../core/receive-cpi-c-2.md)  
  
-   [Request_To_Send](../core/request-to-send-cpi-c-1.md)  
  
-   [Send_Data](../core/send-data-cpi-c-2.md)  
  
-   [Send_Error](../core/send-error-cpi-c-2.md)  
  
-   [Set_Conversation_Security_Password](../core/set-conversation-security-password-cpi-c-1.md)  
  
-   [Set_Conversation_Security_Type](../core/set-conversation-security-type-cpi-c-1.md)  
  
-   [Set_Conversation_Security_User_ID](../core/set-conversation-security-user-id-cpi-c-1.md)  
  
-   [Set_Conversation_Type](../core/set-conversation-type-cpi-c-1.md)  
  
-   [Set_CPIC_Side_Information](../core/set-cpic-side-information-cpi-c-2.md)  
  
-   [Set_Deallocate_Type](../core/set-deallocate-type-cpi-c-1.md)  
  
-   [Set_Error_Direction](../core/set-error-direction-cpi-c-1.md)  
  
-   [Set_Fill](../core/set-fill-cpi-c-1.md)  
  
-   [Set_Log_Data](../core/set-log-data-cpi-c-2.md)  
  
-   [Set_Mode_Name](../core/set-mode-name-cpi-c-2.md)  
  
-   [Set_Partner_LU_Name](../core/set-partner-lu-name-cpi-c-2.md)  
  
-   [Set_Prepare_To_Receive_Type](../core/set-prepare-to-receive-type-cpi-c-1.md)  
  
-   [Set_Processing_Mode](../core/set-processing-mode-cpi-c-2.md)  
  
-   [Set_Receive_Type](../core/set-receive-type-cpi-c-2.md)  
  
-   [Set_Return_Control](../core/set-return-control-cpi-c-2.md)  
  
-   [Set_Send_Type](../core/set-send-type-cpi-c-2.md)  
  
-   [Set_Sync_Level](../core/set-sync-level-cpi-c-1.md)  
  
-   [Set_TP_Name](../core/set-tp-name-cpi-c-1.md)  
  
-   [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-2.md)  
  
-   [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md)  
  
-   [Test_Request_To_Send_Received](../core/test-request-to-send-received-cpi-c-1.md)  
  
-   [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md)  
  
-   [CPI-C Functions Not Supported](../core/cpi-c-functions-not-supported-cpi-c-1.md)