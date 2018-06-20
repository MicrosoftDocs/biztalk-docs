---
title: "RECEIVE_ALLOCATE_EX1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 704c7ad1-7e68-42af-b2ae-26e016cd6937
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RECEIVE_ALLOCATE_EX
The RECEIVE_ALLOCATE_EX verb accepts a new VCB structure to allow registration of an attach manager.  
  
## Syntax  
  
```  
  
typedef struct receive_allocate_ex {  
    unsigned short    opcode;  
        unsigned char     opext;   
        unsigned char     format;  
        unsigned short    primary_rc;  
        unsigned long    secondary_rc;  
       unsigned char     tp_name[64];  
       unsigned char     tp_id[8];  
       unsigned long     conv_id;  
       unsigned char     sync_level;  
        unsigned char    conv_type;  
        unsigned char     user_id[10];  
       unsigned char     lu_alias[8];  
       unsigned char     plu_alias[8];  
       unsigned char     mode_name[8];  
       unsigned char     reserv3[2];  
       unsigned long     conv_group_id;  
       unsigned char     fqplu_name[17];  
       unsigned char     pip_incoming;  
       unsigned long     timeout;  
       unsigned char     password[10];  
       unsigned char     reserv5[2];  
       unsigned char     attach_id[8];  
 }  
```  
  
## Members  
 `opcode`  
 Supplied parameter: RECEIVE_ALLOCATE_EX  
  
 `opext`  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 `format`  
 Reserved parameter.  
  
 `primary_rc`  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued.  
  
 `secondary_rc`  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued.  
  
 `tp_name`  
 Supplied parameter. The **tp_name** is a returned parameter only. However, the application must allocate sufficient buffer space to hold the **tp_name** (that is, 64 characters) and initialize the name to EBCDIC spaces (hexadecimal X'40')  
  
 The returned verb will contain the actual TP name sent by the remote system.  
  
 `tp_id`  
 Returned parameter. Identifies the local TP.  
  
 `conv_id`  
 Returned parameter. Provides the conversation identifier. It identifies the conversation APPC has established between the two partner TPs.  
  
 `sync_level`  
 Returned parameter. Specifies the synchronization level of the conversation. It determines whether the TPs can request confirmation of receipt of data and confirm receipt of data.  
  
- **AP_NONE** specifies that confirmation processing will not be used in this conversation.  
  
- **AP_CONFIRM_SYNC_LEVEL** specifies that the TPs can use confirmation processing in this conversation.  
  
  **AP_SYNCPT** specifies that TPs can use Sync Point Level 2 confirmation processing in this conversation.  
  
  `conv_type`  
  Returned parameter. Specifies the type of conversation chosen by the partner TP, using **MC_ALLOCATE** or **ALLOCATE**. The following are possible values:  
  
  **AP_BASIC_CONVERSATION**  
  
  **AP_MAPPED_CONVERSATION**  
  
  `user_id`  
  This is the EBCDIC user_id sent by the remote system  
  
  `lu_alias`  
  Supplied parameter. Local LU alias. Must be supplied to register an attach manager. Only one attach manager may be registered for a given Local LU alias within the Host Integration Server subdomain. If another attach manager process is already registered for this lu_alias, the following error will be returned:  
  
  primary_rc = AP_STATE_CHECK (0x0002) secondary_rc = AP_LU_ALREADY_REGISTERED (0x0000050A)  
  
  This indicates that Host Integration Server was unable to register this attach manager.  
  
  `plu_alias`  
  Returned parameter. Provides the alias by which the partner LU (which initiated the incoming allocate) is known to the local TP. It is an ASCII character string.  
  
  `mode_name`  
  Returned parameter. Provides the mode name specified by **MC_ALLOCATE** or **ALLOCATE** in the partner TP. It is the name of a set of networking characteristics defined during configuration. The mode_name is a type A EBCDIC character string.  
  
  `reserv3`  
  Reserved parameter.  
  
  `conv_group_id`  
  Conversation group identifier.  
  
  `fqplu_name`  
  This returned parameter provides the fully qualified LU name.  
  
  `pip_incoming`  
  Supplied parameter. If this attach manager will accept incoming FMH-5 Attaches which include PIP data, then set this to **AP_YES**. Otherwise, set this to **AP_NO**.  
  
  Returned parameter: If PIP data is present in the incoming Attach, this is set to **AP_YES**. If no PIP data is present, this will be set to **AP_NO**.  
  
  `timeout`  
  Timeout, in seconds. A value of 0xFFFFFFFF can be used to wait forever.  
  
  `password`  
  Returned parameter: This is the EBCDIC password sent by the remote system. If the remote system supports "Password substitution" (password encryption), the encrypted password will be received in **RECEIVE_ALLOCATE_EX**. There is no facility to decrypt this password, so the application will not be able to verify the user credentials.  
  
  `reserv5`  
  Reserved parameter.  
  
  `attach_id`  
  Returned parameter. Always set to 0. This field is defined for source compatibility with non-Microsoft SNA products.  
  
## Remarks  
 Host Integration Server supports APPC **RECEIVE_ALLOCATE_EX** and **RECEIVE_ALLOCATE_EX_END** to simplify the design and implementation of some invokable transaction programs. This function allows an APPC application to receive all incoming FMH-5 Attach requests received by Host Integration Server over a specific Local APPC LU, allowing an application to act as an "attach manager." An attach manager is a program that handles an incoming FMH-5 Attach request to start an LU6.2 conversation. When an APPC application calls **RECEIVE_ALLOCATE** (as opposed to **RECEIVE_ALLOCATE_EX**), Host Integration Server handles the attach manager functionality. To implement the attach manager functionality within an APPC application, the following occurs:  
  
- The application supplies a Local APPC LU alias to the **RECEIVE_ALLOCATE_EX** function, with a tp_name of EBCDIC spaces (hexadecimal X'40').  
  
- When Host Integration Server receives an incoming FMH-5 Attach request over an LU6.2 session using that Local APPC LU, Host Integration Server will route the request to the application.  
  
- When the **RECEIVE_ALLOCATE_EX** completes, the application is responsible for the following:  
  
  1.  Accepting or rejecting the FMH-5 Attach  
  
  2.  Verifying any conversation level security, and  
  
  3.  If accepting the attach request, completely handling the request within its Win32 process context.  
  
- To stop listening for new incoming attach requests, the application calls **RECEIVE_ALLOCATE_EX_END**.  
  
- After a process issues **RECEIVE_ALLOCATE_EX**, the process should not call **RECEIVE_ALLOCATE** with a specific TP name. Likewise, if a process calls **RECEIVE_ALLOCATE**, that process should not later call **RECEIVE_ALLOCATE_EX**. In other words, for the duration of a process supporting an invokable TP, the process should exclusively call **RECEIVE_ALLOCATE**, or **RECEIVE_ALLOCATE_EX**, but not both.  
  
  It is not possible for the application to dispatch the incoming attach request to another process, as the conversation ID is only valid within its own application context.  
  
> [!NOTE]
>  : Host Integration Server does not support auto starting an attach manager application. In other words, if an application calls **RECEIVE_ALLOCATE_EX**, the application must be started before any incoming Attach requests arrive over the Local LU.  
  
 The current specification does not return the Security Indicator (Byte 4 of the FMH-5 Attach). So, the application will need to accommodate incoming attach requests that contain the following:  
  
1. Neither a user_id or password (when no security is sent in the attach),  
  
2. A user_id only (such as for "already verified" attaches), or  
  
3. Both a user_id and password (if user authorization is required).  
  
   In the LU6.2 BIND request, Host Integration Server indicates support for incoming FMH-5 Attach requests that contain user security, already verified, and password substitution. Host Integration Server does not support incoming attaches which request persistent verification.  
  
   The **RECEIVE_ALLOCATE_EX** function allows an application to register as an attach manager if the tp_name is set to all EBCDIC spaces (X'40') and a Local LU alias is supplied in the lu_alias field. When registered as an attach manager for a given lu_alias, Host Integration Server will route all incoming attaches received over the lu_alias to the application. See below for more information on how Host Integration Server routes incoming FMH-5 attach requests.  
  
   The application may call **RECEIVE_ALLOCATE_EX** more than once to register as the attach manager for one or more Local LU. However, only one attach manager may be registered on a given lu_alias within the SNA subdomain (that is, across all Host Integration Servers and attached Host Integration Server clients). The application cannot supply a blank tp_name and blank lu_alias. In other words, an application cannot register as the default attach manager to receive all incoming attach requests for an SNA subdomain.  
  
   When **RECEIVE_ALLOCATE_EX** completes, the application is responsible for the following:  
  
- Deciding whether the attach will be accepted or not. Host Integration Server provides no mechanism for configuring transaction programs (TPs). The application must have its own means of defining which tp names it will support.  
  
- If accepted, the application must verify conversation security attributes (user_id, password) and for handling the processing of the new conversation.  
  
- The tp_id and conv_id cannot be passed to a separate process for handling. All TP processing must be provided by the application.  
  
  If the application chooses to reject the attach request, **[MC_]DEALLOCATE** must be called, specifying the conv_id received in the completed **RECEIVE_ALLOCATE_EX**, along with an appropriate reason code in the dealloc_type parameter, using these new extended codes:  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_PASSWORD_EXPIRED 0x10`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_PASSWORD_INVALID 0x11`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_USERID_REVOKED 0x12`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_USERID_INVALID 0x13`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_USERID_MISSING 0x14`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_PASSWORD_MISSING 0x15`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_GROUP_INVALID 0x16`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_USERID_REVOKED_IN_GROUP 0x17`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_USERID_NOT_DEFD_TO_GROUP 0x18`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_NOT_AUTHORIZED_AT_REMOTE_LU 0x19`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_NOT_AUTHORIZED_FROM_LOCAL_LU 0x1A`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_NOT_AUTHORIZED_TO_TRANSACTION_PROGRAM 0x1B`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_INSTALLATION_EXIT_FAILED 0x1C`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_PROCESSING_FAILURE 0x1D`  
  
  `#define AP_DEALLOC_SECURITY_NOT_VALID_PROTOCOL_VIOLATION 0x1E`  
  
  When the application sets the above dealloc_type, the Host Integration Server then sends the corresponding sense code within the FMH-7 error sent to the remote system when rejecting the FMH-5 Attach request:  
  
  `#define AP_SECURITY_NOT_VALID_PASSWORD_EXPIRED APPC_FLIPL(x080fff00)`  
  
  `#define AP_SECURITY_NOT_VALID_PASSWORD_INVALID APPC_FLIPL(x080fff01)`  
  
  `#define AP_SECURITY_NOT_VALID_USERID_REVOKED APPC_FLIPL(x080fff02)`  
  
  `#define AP_SECURITY_NOT_VALID_USERID_INVALID APPC_FLIPL(x080fff03)`  
  
  `#define AP_SECURITY_NOT_VALID_USERID_MISSING APPC_FLIPL(x080fff04)`  
  
  `#define AP_SECURITY_NOT_VALID_PASSWORD_MISSING APPC_FLIPL(x080fff05)`  
  
  `#define AP_SECURITY_NOT_VALID_GROUP_INVALID APPC_FLIPL(x080fff06)`  
  
  `#define AP_SECURITY_NOT_VALID_USERID_REVOKED_IN_GROUP APPC_FLIPL(x080fff07)`  
  
  `#define AP_SECURITY_NOT_VALID_USERID_NOT_DEFD_TO_GROUP APPC_FLIPL(x080fff08)`  
  
  `#define AP_SECURITY_NOT_VALID_NOT_AUTHORIZED_AT_REMOTE_LU APPC_FLIPL(x080fff09)`  
  
  `#define AP_SECURITY_NOT_VALID_NOT_AUTHORIZED_FROM_LOCAL_LU APPC_FLIPL(x080fff0A)`  
  
  `#define AP_SECURITY_NOT_VALID_NOT_AUTHORIZED_TO_TRANSACTION_PROGRAM APPC_FLIPL(x080fff0B)`  
  
  `#define AP_SECURITY_NOT_VALID_INSTALLATION_EXIT_FAILED APPC_FLIPL(x080fff0C)`  
  
  `#define AP_SECURITY_NOT_VALID_PROCESSING_FAILURE APPC_FLIPL(x080fff0D)`  
  
  `#define AP_SECURITY_NOT_VALID_PROTOCOL_VIOLATION APPC_FLIPL(x080fff0E)`  
  
  Before calling **RECEIVE_ALLOCATE_EX**, the application may want to verify the configuration settings for the Local APPC LU to determine if the LU supports sync level 2, or is a member of the default LU pool. To do this, use the enhanced **GET_LU_STATUS** API.  
  
  To deregister as the attach manager for a given Local APPC LU, the application must call **RECEIVE_ALLOCATE_EX_END**, documented below. If an application has registered as the attach manager for more than one lu_alias, **RECEIVE_ALLOCATE_EX_END** must be called for each lu_alias.  
  
  The application should try to have a **RECEIVE_ALLOCATE_EX** pending at all times, in order to handle incoming attach requests in a timely manner. If the application fails to post new **RECEIVE_ALLOCATE_EX**, Host Integration Server queues up to 2,048 incoming attaches against the application, if the application is running on the Host Integration Server, or 256 if running on an HIS client. If the limit is exceeded, Host Integration Server rejects the attach request with sense code X'084B6031', or **AP_TRANS_PGM_NOT_AVAIL_RETRY**.