---
title: "CPI-C Calls1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9d19b07-fc28-401b-b76e-ac4f44ed8e48
caps.latest.revision: 3
---
# CPI-C Calls
This section describes the Common Programming Interface for Communications (CPI-C) calls. The following information is supplied for each call:  
  
-   The pseudonym for the call and the actual C function name.  
  
-   A definition of the call.  
  
-   A list of the parameters used by the call and the data type for each parameter. The prototype of each function is declared in the WINCPIC.H file.  
  
-   A description of each input and output parameter. The parameter names are pseudonyms and the actual names for these parameters are declared by the application program. The description includes the possible values of the parameter.  
  
-   The conversation states in which the call can be issued.  
  
-   The states to which the conversation can change upon return from the call. Conditions that do not cause a state change are not noted. For example, parameter checks and state checks do not cause a state change.  
  
-   Additional information describing the use of the call.  
  
 **Data Types**  
  
 The data types for the parameters supplied to and received from CPI-C are established as symbolic constants by **#define** statements in the WINCPIC.H file. For example, CM_INT32 represents **signed long int** and CM_PTR represents **far \***. Using symbolic constants improves the portability of CPI-C applications.  
  
 For ease of understanding, this reference presents the data types in absolute (not **#defined**) terms.  
  
 In writing applications, you should use the symbolic constants from the WINCPIC.H file.  
  
 **Symbolic Constants**  
  
 Most parameters supplied to and returned by CPI-C are 32-bit integers. To simplify coding, the values for these parameters are represented by meaningful symbolic constants, which are established by **#define** statements in the WINCPIC.H header file. For example, the value CM_MAPPED_CONVERSATION represents the integer 1. For the sake of readability, use only the symbolic constants when writing programs.  
  
 **Strings**  
  
 All strings are in ASCII format when passed across the CPI-C interface.  
  
 **Validity of output parameters**  
  
 The parameters returned by CPI-C are valid only if the CPI-C call is executed successfully, as indicated by a return code of CM_OK.  
  
## In This Section  
  
-   [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md)  
  
-   [Allocate](../HIS2010/allocate-cpi-c-1.md)  
  
-   [Cancel_Conversation](../HIS2010/cancel-conversation-cpi-c-1.md)  
  
-   [Confirm](../HIS2010/confirm-cpi-c-1.md)  
  
-   [Confirmed](../HIS2010/confirmed-cpi-c-1.md)  
  
-   [Convert_Incoming](../HIS2010/convert-incoming-cpi-c-2.md)  
  
-   [Convert_Outgoing](../HIS2010/convert-outgoing-cpi-c-2.md)  
  
-   [Deallocate](../HIS2010/deallocate-cpi-c-2.md)  
  
-   [Delete_CPIC_Side_Information](../HIS2010/delete-cpic-side-information-cpi-c-1.md)  
  
-   [Extract_Conversation_Security_Type](../HIS2010/extract-conversation-security-type-cpi-c-1.md)  
  
-   [Extract_Conversation_Security_User_ID](../HIS2010/extract-conversation-security-user-id-cpi-c-2.md)  
  
-   [Extract_Conversation_State](../HIS2010/extract-conversation-state-cpi-c-1.md)  
  
-   [Extract_Conversation_Type](../HIS2010/extract-conversation-type-cpi-c-1.md)  
  
-   [Extract_CPIC_Side_Information](../HIS2010/extract-cpic-side-information-cpi-c-2.md)  
  
-   [Extract_Mode_Name](../HIS2010/extract-mode-name-cpi-c-2.md)  
  
-   [Extract_Partner_LU_Name](../HIS2010/extract-partner-lu-name-cpi-c-2.md)  
  
-   [Extract_Sync_Level](../HIS2010/extract-sync-level-cpi-c-2.md)  
  
-   [Extract_TP_Name](../HIS2010/extract-tp-name-cpi-c-1.md)  
  
-   [Flush](../HIS2010/flush-cpi-c-1.md)  
  
-   [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md)  
  
-   [Prepare_To_Receive](../HIS2010/prepare-to-receive-cpi-c-2.md)  
  
-   [Receive](../HIS2010/receive-cpi-c-1.md)  
  
-   [Request_To_Send](../HIS2010/request-to-send-cpi-c-2.md)  
  
-   [Send_Data](../HIS2010/send-data-cpi-c-1.md)  
  
-   [Send_Error](../HIS2010/send-error-cpi-c-1.md)  
  
-   [Set_Conversation_Security_Password](../HIS2010/set-conversation-security-password-cpi-c-2.md)  
  
-   [Set_Conversation_Security_Type](../HIS2010/set-conversation-security-type-cpi-c-2.md)  
  
-   [Set_Conversation_Security_User_ID](../HIS2010/set-conversation-security-user-id-cpi-c-2.md)  
  
-   [Set_Conversation_Type](../HIS2010/set-conversation-type-cpi-c-2.md)  
  
-   [Set_CPIC_Side_Information](../HIS2010/set-cpic-side-information-cpi-c-1.md)  
  
-   [Set_Deallocate_Type](../HIS2010/set-deallocate-type-cpi-c-2.md)  
  
-   [Set_Error_Direction](../HIS2010/set-error-direction-cpi-c-2.md)  
  
-   [Set_Fill](../HIS2010/set-fill-cpi-c-2.md)  
  
-   [Set_Log_Data](../HIS2010/set-log-data-cpi-c-1.md)  
  
-   [Set_Mode_Name](../HIS2010/set-mode-name-cpi-c-1.md)  
  
-   [Set_Partner_LU_Name](../HIS2010/set-partner-lu-name-cpi-c-1.md)  
  
-   [Set_Prepare_To_Receive_Type](../HIS2010/set-prepare-to-receive-type-cpi-c-2.md)  
  
-   [Set_Processing_Mode](../HIS2010/set-processing-mode-cpi-c-1.md)  
  
-   [Set_Receive_Type](../HIS2010/set-receive-type-cpi-c-1.md)  
  
-   [Set_Return_Control](../HIS2010/set-return-control-cpi-c-1.md)  
  
-   [Set_Send_Type](../HIS2010/set-send-type-cpi-c-1.md)  
  
-   [Set_Sync_Level](../HIS2010/set-sync-level-cpi-c-2.md)  
  
-   [Set_TP_Name](../HIS2010/set-tp-name-cpi-c-2.md)  
  
-   [Specify_Local_TP_Name](../HIS2010/specify-local-tp-name-cpi-c-1.md)  
  
-   [Specify_Windows_Handle](../HIS2010/specify-windows-handle-cpi-c-1.md)  
  
-   [Test_Request_To_Send_Received](../HIS2010/test-request-to-send-received-cpi-c-2.md)  
  
-   [Wait_For_Conversation](../HIS2010/wait-for-conversation-cpi-c-2.md)  
  
-   [CPI-C Functions Not Supported](../HIS2010/cpi-c-functions-not-supported-cpi-c-2.md)