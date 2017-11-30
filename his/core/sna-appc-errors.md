---
title: "SNA APPC Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b13602e3-8634-495c-a663-2c1827eab85d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNA APPC Errors
The following table lists SNA network error constants, values, SqlState, SqlCode and a description of the error. An asterisk (*) indicates not in use.  
  
|||||  
|-|-|-|-|  
|**Value**|**SqlState**|**SqlCode**|**Description**|  
|-512|08S01|-512|**Message**: Parameter check (APPC).|  
|-513|08S01|-513|**Message**: Host does not recognize the transaction program specified.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-514|08S01|-514|**Message**: Invalid conversation ID.|  
|-515|08S01|-515|**Message**: Invalid local LU alias.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Local LU Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Local LU Name value matches Host Integration Server SNA Service APPC Local LU Name. For more information, see topic on APPC Local LU Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-516|08S01|-516|**Message**: Invalid data segment.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm and at ms-help://MS.HIS.2010/HIS2010/html/50070b5c-a3f1-4e6d-8ffa-842501d79b45.htm.|  
|-517|08S01|-517|**Message**: Invalid conversation type.|  
|-518|08S01|-518|**Message**: Invalid synchronization level.|  
|-519|08S01|-519|**Message**: Invalid security.<br /><br /> **Reason**: The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action**: Verify connection information to ensure the User Name (User Identifier), Password, APPC Security Type (Program, Same, None) and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-520|08S01|-520|**Message**: Invalid return control.|  
|-521|08S01|-521|**Message**: PIP length is incorrect.|  
|-522|08S01|-522|**Message**: SNASVCMG is not a valid value for mode_name.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Mode Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Mode Name value matches server APPC Mode Name. For more information, see topic on APPC Mode Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-523|08S01|-523|**Message**: Invalid mode name.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Mode Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Mode Name value matches server APPC Mode Name. For more information, see topic on APPC Mode Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-524|08S01|-524|**Message**: Confirm failed. The synchronization level of the current conversation is NONE.|  
|-525|08S01|-525|**Message**: Deallocation type is invalid.|  
|-526|08S01|-526|**Message**: The LL field of the GDS error log variable did not match the actual length of the log data.|  
|-527|08S01|-527|**Message**: Invalid pointer type.|  
|-528|08S01|-528|**Message**: Receive_and_wait has bad fill type.|  
|-529|08S01|-529|**Message**: Receive_Immediately has bad fill type.|  
|-530|08S01|-530|**Message**: Receive_and_post has bad fill type.|  
|-531|08S01|-531|**Message**: Invalid semaphore handle.|  
|-532|08S01|-532|**Message**: Bad return status with data.|  
|-533|08S01|-533|**Message**: Invalid length field.|  
|-534|08S01|-534|**Message**: Send_Data contains invalid type.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm and at ms-help://MS.HIS.2010/HIS2010/html/50070b5c-a3f1-4e6d-8ffa-842501d79b45.htm.|  
|-535|08S01|-535|**Message**: Invalid session ID.|  
|-536|08S01|-536|**Message**: Send_Data_Confirm failed. The synchronization level is NONE.|  
|-537|08S01|-537|**Message**: Invalid partner LU alias.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Remote LU Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Remote LU Name value matches server APPC Partner LU Name. For more information, see topic on APPC Remote LU Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-538|08S01|-538|**Message**: Send_Error has incorrect log data length.|  
|-539|08S01|-539|**Message**: Send_Error contains invalid type.|  
|-540|08S01|-540|**Message**: Invalid error direction.|  
|-541|08S01|-541|**Message**: Too many active transaction programs.|  
|-542|08S01|-542|**Message**: Invalid type.|  
|-543|08S01|-543|**Message**: The specified transaction program name is undefined.<br /><br /> **Reason**: The client failed to connect to the server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-544|08S01|-544|**Message**: Invalid state.|  
|-545|08S01|-545|**Message**: Confirm is issued on bad state.|  
|-546|08S01|-546|**Message**: Confirm on incomplete data.|  
|-547|08S01|-547|**Message**: CONFIRMED is issued on bad state.|  
|-548|08S01|-548|**Message**: Deallocate with flush on bad state.|  
|-549|08S01|-549|**Message**: Deallocate with confirm on bad state.|  
|-550|08S01|-550|**Message**: The TP did not finish sending a logical record.|  
|-551|08S01|-551|**Message**: Cannot flush data. The conversation is not in SEND state.|  
|-552|08S01|-552|**Message**: The local TP did not finish sending a logical record.|  
|-553|08S01|-553|**Message**: The conversation was not in SEND state.|  
|-554|08S01|-554|**Message**: The conversation was not in RECEIVE or SEND state.|  
|-555|08S01|-555|**Message**: The TP did not finish sending a logical record. The conversation is in SEND state.|  
|-556|08S01|-556|**Message**: The conversation was not in RECEIVE state.|  
|-557|08S01|-557|**Message**: The conversation was not in SEND or Receive state.|  
|-558|08S01|-558|**Message**: The conversation was in SEND state, but the TP did not finish sending a logical record.|  
|-559|08S01|-559|**Message**: The conversation is not in an allowed state when REQUEST_TO_SEND was issued.|  
|-560|08S01|-560|**Message**: The conversation was not in SEND state.|  
|-561|08S01|-561|**Message**: The TP started but did not finish sending a logical record.|  
|-562|08S01|-562|**Message**: Attach manager is inactive.|  
|-563|08S01|-563|**Message**: No pending allocation exists.|  
|-564|08S01|-564|**Message**: Invalid process.|  
|-565|08S01|-565|**Message**: Allocation error.|  
|-566|08S01|-566|**Message**: The conversation cannot be allocated because of permanent condition.|  
|-567|08S01|-567|**Message**: The conversation cannot be allocated because of a temporary condition.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Remote LU Alias.<br /><br /> **Action**: Verify connection information to ensure the APPC Remote LU Alias value matches server. For more information, see topic on APPC Remote LU Alias, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-568|08S01|-568|**Message**: Invalid user ID or password.<br /><br /> **Reason**: The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action**: Verify connection information to ensure the User Name (User Identifier), Password and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-569|08S01|-569|**Message**: The remote LU rejected the allocation request because it was unable to start the requested partner TP.|  
|-570|08S01|-570|**Message**: The remote LU rejected the allocation requested because it was unable to start the requested TP. The condition is permanent.|  
|-571|08S01|-571|**Message**: The connection could not be established. Check if the connection parameters are correct.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Transaction Program Name.<br /><br /> **Action**: Verify connection information to ensure the APPC Transaction Program Name value matches the server. For more information, see topic on APPC Transaction Program Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|-572|08S01|-572|**Message**: PIP data either is not required or not supported.|  
|-573|08S01|-573|**Message**: Incorrect PIP data.|  
|-574|08S01|-574|**Message**: The partner LU or TP does not support the conversation type.|  
|-575|08S01|-575|**Message**: The partner TP does not support the synchronization level.|  
|-576|08S01|-576|**Message**: The conversation was deallocated with AP_ABEND.|  
|-577|08S01|-577|**Message**: The conversation was deallocated with AP_ABEND_PROG.|  
|-578|08S01|-578|**Message**: The conversation was deallocated with AP_ABEND_SVC.|  
|-579|08S01|-579|**Message**: The conversation was deallocated with AP_ABEND_TIMER.|  
|-580|08S01|-580|**Message**: The partner TP has deallocated the conversation without requesting confirmation.|  
|-581|08S01|-581|**Message**: Error encountered. Data was not truncated.|  
|-582|08S01|-582|**Message**: Error encountered. Data was truncated.|  
|-583|08S01|-583|**Message**: Error encountered. Data sent to the partner TP may have been purged.|  
|-584|08S01|-584|**Message**: The conversation was terminated because of a temporary error.|  
|-585|08S01|-585|**Message**: The conversation was terminated because of a permanent error.|  
|-586|08S01|-586|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data was not truncated.|  
|-587|08S01|-587|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data was truncated.|  
|-588|08S01|-588|**Message**: The partner TP (or LU) issued SEND_ERROR with err_type set to AP_SVC. Data sent to the partner TP may have been purged.|  
|-589|08S01|-589|**Message**: No data is immediately available from the partner TP.|  
|-590|08S01|-590|**Message**: Basic and Mapped verbs are mixed in the same conversation.|  
|-591|08S01|-591|**Message**: RECEIVE_AND_POSTED is canceled.|  
|-592|08S01|-592|**Message**: Security requested is not supported.|  
|-593|08S01|-593|**Message**: The requested partner TP is busy.|  
|-594|08S01|-594|**Message**: The communication subsystem is abended. Contact your system administrator.|  
|-595|08S01|-595|**Message**: A required communication subsystem's component could not be loaded.|  
|-596|08S01|-596|**Message**: There can only be one outstanding conversation verb at a time on any conversation.|  
|-597|08S01|-597|**Message**: The calling thread is already blocked.|  
|-598|08S01|-598|**Message**: The VCB extended beyond the end of the data segment.|  
|-599|08S01|-599|**Message**: The operating system has returned an error to APPC.|  
|-600|08S01|-600|**Message**: The stack size of the application is too small. Increase the stack size of your application.|  
|-601|08S01|-601|**Message**: Invalid verb.|  
|-1100|HY000|-1100|**Message**: APPC is not supported on this version of Host Integration Server.|