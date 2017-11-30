---
title: "SNA Network Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2494e9d-6bb5-4ae5-8023-876811c25c6b
caps.latest.revision: 6
---
# SNA Network Errors
The following table lists SNA network error constants, values, SqlState, SqlCode and a description of the error. An asterisk (*) indicates not in use.  
  
||||||  
|-|-|-|-|-|  
|**Const**|**Value**|**SqlState**|**SqlCode**|**Description**|  
|DB2OLEDB_COMM_PARAMETER_CHECK|-512|08S01|-512|**Message**: Parameter check (APPC).|  
|DB2OLEDB_COMM_BAD_TP_ID|-513|08S01|-513|**Message**: Host does not recognize the transaction program specified.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_BAD_CONV_ID|-514|08S01|-514|**Message**: Invalid conversation ID.|  
|DB2OLEDB_COMM_BAD_LU_ALIAS|-515|08S01|-515|**Message**: Invalid local LU alias.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Local LU Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Local LU Name value matches Host Integration Server SNA Service APPC Local LU Name. For more information, see topic on APPC Local LU Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_INVALID_DATA_SEGMENT|-516|08S01|-516|**Message**: Invalid data segment.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm and at ms-help://MS.HIS.2010/HIS2010/html/50070b5c-a3f1-4e6d-8ffa-842501d79b45.htm.|  
|DB2OLEDB_COMM_BAD_CONV_TYPE|-517|08S01|-517|**Message**: Invalid conversation type.|  
|DB2OLEDB_COMM_BAD_SYNC_LEVEL|-518|08S01|-518|**Message**: Invalid synchronization level.|  
|DB2OLEDB_COMM_BAD_SECURITY|-519|08S01|-519|**Message**: Invalid security.<br /><br /> **Reason**: The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action**: Verify connection information to ensure the User Name (User Identifier), Password, APPC Security Type (Program, Same, None) and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_BAD_RETURN_CONTROL|-520|08S01|-520|**Message**: Invalid return control.|  
|DB2OLEDB_COMM_PIP_LEN_INCORRECT|-521|08S01|-521|**Message**: PIP length is incorrect.|  
|DB2OLEDB_COMM_NO_USE_OF_SNASVCMG|-522|08S01|-522|**Message**: SNASVCMG is not a valid value for mode_name.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Mode Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Mode Name value matches server APPC Mode Name. For more information, see topic on APPC Mode Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_UNKNOWN_PARTNER_MODE|-523|08S01|-523|**Message**: Invalid mode name.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Mode Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Mode Name value matches server APPC Mode Name. For more information, see topic on APPC Mode Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_CONFIRM_ON_SYNC_LEVEL_NONE|-524|08S01|-524|**Message**: Confirm failed. The synchronization level of the current conversation is NONE.|  
|DB2OLEDB_COMM_DEALLOC_BAD_TYPE|-525|08S01|-525|**Message**: Deallocation type is invalid.|  
|DB2OLEDB_COMM_DEALLOC_LOG_LL_WRONG|-526|08S01|-526|**Message**: The LL field of the GDS error log variable did not match the actual length of the log data.|  
|DB2OLEDB_COMM_P_TO_R_INVALID_TYPE|-527|08S01|-527|**Message**: Invalid pointer type.|  
|DB2OLEDB_COMM_RCV_AND_WAIT_BAD_FILL|-528|08S01|-528|**Message**: Receive_and_wait has bad fill type.|  
|DB2OLEDB_COMM_RCV_IMMD_BAD_FILL|-529|08S01|-529|**Message**: Receive_Immediately has bad fill type.|  
|DB2OLEDB_COMM_RCV_AND_POST_BAD_FILL|-530|08S01|-530|**Message**: Receive_and_post has bad fill type.|  
|DB2OLEDB_COMM_INVALID_SEMAPHORE_HANDLE|-531|08S01|-531|**Message**: Invalid semaphore handle.|  
|DB2OLEDB_COMM_BAD_RETURN_STATUS_WITH_DATA|-532|08S01|-532|**Message**: Bad return status with data.|  
|DB2OLEDB_COMM_BAD_LL|-533|08S01|-533|**Message**: Invalid length field.|  
|DB2OLEDB_COMM_SEND_DATA_INVALID_TYPE|-534|08S01|-534|**Message**: Send_Data contains invalid type.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm and at ms-help://MS.HIS.2010/HIS2010/html/50070b5c-a3f1-4e6d-8ffa-842501d79b45.htm.|  
|DB2OLEDB_COMM_INVALID_SESSION_ID|-535|08S01|-535|**Message**: Invalid session ID.|  
|DB2OLEDB_COMM_SEND_DATA_CONFIRM_SYNC_NONE|-536|08S01|-536|**Message**: Send_Data_Confirm failed. The synchronization level is NONE.|  
|DB2OLEDB_COMM_BAD_PARTNER_LU_ALIAS|-537|08S01|-537|**Message**: Invalid partner LU alias.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Remote LU Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Remote LU Name value matches server APPC Partner LU Name. For more information, see topic on APPC Remote LU Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_SEND_ERROR_LOG_LL_WRONG|-538|08S01|-538|**Message**: Send_Error has incorrect log data length.|  
|DB2OLEDB_COMM_SEND_ERROR_BAD_TYPE|-539|08S01|-539|**Message**: Send_Error contains invalid type.|  
|DB2OLEDB_COMM_BAD_ERROR_DIRECTION|-540|08S01|-540|**Message**: Invalid error direction.|  
|DB2OLEDB_COMM_TOO_MANY_TPS|-541|08S01|-541|**Message**: Too many active transaction programs.|  
|DB2OLEDB_COMM_BAD_TYPE|-542|08S01|-542|**Message**: Invalid type.|  
|DB2OLEDB_COMM_UNDEFINED_TP_NAME|-543|08S01|-543|**Message**: The specified transaction program name is undefined.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_STATE_CHECK|-544|08S01|-544|**Message**: Invalid state.|  
|DB2OLEDB_COMM_CONFIRM_BAD_STATE|-545|08S01|-545|**Message**: Confirm is issued on bad state.|  
|DB2OLEDB_COMM_CONFIRM_NOT_LL_BDY|-546|08S01|-546|**Message**: Confirm on incomplete data.|  
|DB2OLEDB_COMM_CONFIRMED_BAD_STATE|-547|08S01|-547|**Message**: CONFIRMED is issued on bad state.|  
|DB2OLEDB_COMM_DEALLOC_FLUSH_BAD_STATE|-548|08S01|-548|**Message**: Deallocate with flush on bad state.|  
|DB2OLEDB_COMM_DEALLOC_CONFIRM_BAD_STATE|-549|08S01|-549|**Message**: Deallocate with confirm on bad state.|  
|DB2OLEDB_COMM_DEALLOC_NOT_LL_BDY|-550|08S01|-550|**Message**: The TP did not finish sending a logical record.|  
|DB2OLEDB_COMM_FLUSH_NOT_SEND_STATE|-551|08S01|-551|**Message**: Cannot flush data. The conversation is not in SEND state.|  
|DB2OLEDB_COMM_P_TO_R_NOT_LL_BDY|-552|08S01|-552|**Message**: The local TP did not finish sending a logical record.|  
|DB2OLEDB_COMM_P_TO_R_NOT_SEND_STATE|-553|08S01|-553|**Message**: The conversation was not in SEND state.|  
|DB2OLEDB_COMM_RCV_AND_WAIT_BAD_STATE|-554|08S01|-554|**Message**: The conversation was not in RECEIVE or SEND state.|  
|DB2OLEDB_COMM_RCV_AND_WAIT_NOT_LL_BDY|-555|08S01|-555|**Message**: The TP did not finish sending a logical record. The conversation is in SEND state.|  
|DB2OLEDB_COMM_RCV_IMMD_BAD_STATE|-556|08S01|-556|**Message**: The conversation was not in RECEIVE state.|  
|DB2OLEDB_COMM_RCV_AND_POST_BAD_STATE|-557|08S01|-557|**Message**: The conversation was not in SEND or Receive state.|  
|DB2OLEDB_COMM_RCV_AND_POST_NOT_LL_BDY|-558|08S01|-558|**Message**: The conversation was in SEND state, but the TP did not finish sending a logical record.|  
|DB2OLEDB_COMM_R_T_S_BAD_STATE|-559|08S01|-559|**Message**: The conversation is not in an allowed state when REQUEST_TO_SEND was issued.|  
|DB2OLEDB_COMM_SEND_DATA_NOT_SEND_STATE|-560|08S01|-560|**Message**: The conversation was not in SEND state.|  
|DB2OLEDB_COMM_SEND_DATA_NOT_LL_BDY|-561|08S01|-561|**Message**: The TP started but did not finish sending a logical record.|  
|DB2OLEDB_COMM_ATTACH_MANAGER_INACTIVE|-562|08S01|-562|**Message**: Attach manager is inactive.|  
|DB2OLEDB_COMM_ALLOCATE_NOT_PENDING|-563|08S01|-563|**Message**: No pending allocation exists.|  
|DB2OLEDB_COMM_INVALID_PROCESS|-564|08S01|-564|**Message**: Invalid process.|  
|DB2OLEDB_COMM_ALLOCATION_ERROR|-565|08S01|-565|**Message**: Allocation error.|  
|DB2OLEDB_COMM_ALLOCATION_FAILURE_NO_RETRY|-566|08S01|-566|**Message**: The conversation cannot be allocated because of permanent condition.|  
|DB2OLEDB_COMM_ALLOCATION_FAILURE_RETRY|-567|08S01|-567|**Message**: The conversation cannot be allocated because of a temporary condition.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Remote LU Alias.<br /><br /> **Action**: Verify connection information to ensure the APPC Remote LU Alias value matches server. For more information, see topic on APPC Remote LU Alias, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_SECURITY_NOT_VALID|-568|08S01|-568|**Message**: Invalid user ID or password.<br /><br /> **Reason**: The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action**: Verify connection information to ensure the User Name (User Identifier), Password and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_TRANS_PGM_NOT_AVAIL_RETRY|-569|08S01|-569|**Message**: The remote LU rejected the allocation request because it was unable to start the requested partner TP.|  
|DB2OLEDB_COMM_TRANS_PGM_NOT_AVAIL_NO_RETRY|-570|08S01|-570|**Message**: The remote LU rejected the allocation requested because it was unable to start the requested TP. The condition is permanent.|  
|DB2OLEDB_COMM_TP_NAME_NOT_RECOGNIZED|-571|08S01|-571|**Message**: The connection could not be established. Check if the connection parameters are correct.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_COMM_PIP_NOT_ALLOWED|-572|08S01|-572|**Message**: PIP data either is not required or not supported.|  
|DB2OLEDB_COMM_PIP_NOT_SPECIFIED_CORRECTLY|-573|08S01|-573|**Message**: Incorrect PIP data.|  
|DB2OLEDB_COMM_CONVERSATION_TYPE_MISMATCH|-574|08S01|-574|**Message**: The partner LU or TP does not support the conversation type.|  
|DB2OLEDB_COMM_SYNC_LEVEL_NOT_SUPPORTED|-575|08S01|-575|**Message**: The partner TP does not support the synchronization level.|  
|DB2OLEDB_COMM_DEALLOC_ABEND|-576|08S01|-576|**Message**: The conversation was deallocated with AP_ABEND.|  
|DB2OLEDB_COMM_DEALLOC_ABEND_PROG|-577|08S01|-577|**Message**: The conversation was deallocated with AP_ABEND_PROG.|  
|DB2OLEDB_COMM_DEALLOC_ABEND_SVC|-578|08S01|-578|**Message**: The conversation was deallocated with AP_ABEND_SVC.|  
|DB2OLEDB_COMM_DEALLOC_ABEND_TIMER|-579|08S01|-579|**Message**: The conversation was deallocated with AP_ABEND_TIMER.|  
|DB2OLEDB_COMM_DEALLOC_NORMAL|-580|08S01|-580|**Message**: The partner TP has deallocated the conversation without requesting confirmation.|  
|DB2OLEDB_COMM_PROG_ERROR_NO_TRUNC|-581|08S01|-581|**Message**: Error encountered. Data was not truncated.|  
|DB2OLEDB_COMM_PROG_ERROR_TRUNC|-582|08S01|-582|**Message**: Error encountered. Data was truncated.|  
|DB2OLEDB_COMM_PROG_ERROR_PURGING|-583|08S01|-583|**Message**: Error encountered. Data sent to the partner TP may have been purged.|  
|DB2OLEDB_COMM_CONV_FAILURE_RETRY|-584|08S01|-584|**Message**: The conversation was terminated because of a temporary error.|  
|DB2OLEDB_COMM_CONV_FAILURE_NO_RETRY|-585|08S01|-585|**Message**: The conversation was terminated because of a permanent error.|  
|DB2OLEDB_COMM_SVC_ERROR_NO_TRUNC|-586|08S01|-586|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data was not truncated.|  
|DB2OLEDB_COMM_SVC_ERROR_TRUNC|-587|08S01|-587|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data was truncated.|  
|DB2OLEDB_COMM_SVC_ERROR_PURGING|-588|08S01|-588|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data sent to the partner TP may have been purged.|  
|DB2OLEDB_COMM_UNSUCCESSFUL|-589|08S01|-589|**Message**: No data is immediately available from the partner TP.|  
|DB2OLEDB_COMM_CONVERSATION_TYPE_MIXED|-590|08S01|-590|**Message**: Basic and Mapped verbs are mixed in the same conversation.|  
|DB2OLEDB_COMM_CANCELLED|-591|08S01|-591|**Message**: RECEIVE_AND_POSTED is canceled.|  
|DB2OLEDB_COMM_SECURITY_REQ_NOT_SUPPORTED|-592|08S01|-592|**Message**: Security requested is not supported.|  
|DB2OLEDB_COMM_TP_BUSY|-593|08S01|-593|**Message**: The requested partner TP is busy.|  
|*DB2OLEDB_COMM_COMM_SUBSYSTEM_ABENDED|-594|08S01|-594|**Message**: The communication subsystem is abended. Contact your system administrator.|  
|*DB2OLEDB_COMM_COMM_SUBSYSTEM_NOT_LOADED|-595|08S01|-595|**Message**: A required communication subsystem's component could not be loaded.|  
|*DB2OLEDB_COMM_CONV_BUSY|-596|08S01|-596|**Message**: There can only be one outstanding conversation verb at a time on any conversation.|  
|DB2OLEDB_COMM_THREAD_BLOCKING|-597|08S01|-597|**Message**: The calling thread is already blocked.|  
|DB2OLEDB_COMM_INVALID_VERB_SEGMENT|-598|08S01|-598|**Message**: The VCB extended beyond the end of the data segment.|  
|DB2OLEDB_COMM_UNEXPECTED_DOS_ERROR|-599|08S01|-599|**Message**: The operating system has returned an error to APPC.|  
|DB2OLEDB_COMM_STACK_TOO_SMALL|-600|08S01|-600|**Message**: The stack size of the application is too small. Increase the stack size of your application.|  
|DB2OLEDB_COMM_INVALID_VERB|-601|08S01|-601|**Message**: Invalid verb.|  
|DB2OLEDB_APPC_NOT_SUPPORTED|-1100|HY000|-1100|**Message**: APPC is not supported on this version of Host Integration Server.|