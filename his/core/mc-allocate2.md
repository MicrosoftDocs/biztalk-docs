---
title: "MC_ALLOCATE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85eea9c3-a925-4719-9fd2-6411e61de865
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MC_ALLOCATE
The **MC_ALLOCATE** verb is issued by the invoking transaction program (TP). It allocates a session between the local logical unit (LU) and partner LU and (in conjunction with [RECEIVE_ALLOCATE](../core/receive-allocate1.md)) establishes a conversation between the invoking TP and the invoked TP. After this verb executes successfully, APPC generates a conversation identifier (**conv_id**). The **conv_id** is a required parameter for all other APPC conversation verbs.  
  
 The following structure describes the verb control block (VCB) used by the **MC_ALLOCATE** verb.  
  
## Syntax  
  
```  
  
struct mc_allocate {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    reserv2;  
    unsigned short   primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned char    reserv3;  
    unsigned char    synclevel;  
    unsigned char    reserv4[2];  
    unsigned char    rtn_ctl;  
    unsigned char    reserv5;  
    unsigned long    conv_group_id;  
    unsigned long    sense_data;  
    unsigned char    plu_alias[8];  
    unsigned char    mode_name[8];  
    unsigned char    tp_name[64];  
    unsigned char    security;  
    unsigned char    reserv6[11];  
    unsigned char    pwd[10];  
    unsigned char    user_id[10];  
    unsigned short   pip_dlen;  
    unsigned char FAR * pip_dptr;  
    unsigned char    reserv7;  
    unsigned char    fqplu_name[17];  
    unsigned char    reserv8[8];  
    unsigned long    proxy_user;  
    unsigned long    proxy_domain;  
    unsigned char    reserv9[16];  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code; AP_M_ALLOCATE.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_MAPPED_CONVERSATION. If the AP_EXTD_VCB bit is set, this indicates that an extended version of the verb control block is used. In this case, the **MC_ALLOCATE** structure includes Sync Point support or privileged proxy feature support.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md).  
  
 *conv_id*  
 Returned parameter. Identifies the conversation established between the two TPs.  
  
 *reserv3*  
 A reserved field.  
  
 *synclevel*  
 Supplied parameter. Specifies the synchronization level of the conversation. It determines whether the TPs can request confirmation of receipt of data and confirm receipt of data.  
  
- AP_NONE specifies that confirmation processing will not be used in this conversation.  
  
- AP_CONFIRM_SYNC_LEVEL specifies that the TPs can use confirmation processing in this conversation.  
  
- AP_SYNCPT specifies that TPs can use Sync Point Level 2 confirmation processing in this conversation.  
  
  *reserv4*  
  A reserved field.  
  
  *reserv5*  
  A reserved field.  
  
  *rtn_ctl*  
  Supplied parameter. Specifies when the local LU, acting on a session request from the local TP, should return control to the local TP. For information about sessions, see [Transaction Programs Overview](./transaction-programs-overview1.md).  
  
- AP_IMMEDIATE specifies that the LU allocates a contention-winner session, if one is immediately available, and returns control to the TP.  
  
- AP_WHEN_SESSION_ALLOCATED specifies that the LU does not return control to the TP until it allocates a session or encounters one of the errors documented in Return Codes in this topic. (If the session limit is zero, the LU returns control immediately.) If a session is not available, the TP waits for one.  
  
- AP_WHEN_SESSION_FREE specifies that the LU allocates a contention-winner or contention-loser session, if one is available or able to be activated, and returns control to the TP. If an error occurs, (as documented in Return Codes in this topic) the call will return immediately with the error in the **primary_rc** and **secondary_rc** fields.  
  
- AP_WHEN_CONWINNER_ALLOC specifies that the LU does not return control until it allocates a contention-winner session or encounters one of the errors documented in Return Codes in this topic. (If the session limit is zero, the LU returns control immediately.) If a session is not available, the TP waits for one.  
  
- AP_WHEN_CONV_GROUP_ALLOC specifies that the LU does not return control to the TP until it allocates the session specified by **conv_group_id**or encounters one of the errors documented in Return Codes in this topic. If a session is not available, the TP waits for it to become free.  
  
> [!NOTE]
>  AP_IMMEDIATE is the only value for **rtn_ctl** that never causes a new session to start. For values other than AP_IMMEDIATE, if an appropriate session is not immediately available, Microsoft® Host Integration Server  tries to start one. This causes the on-demand connection to be activated.  
  
 *conv_group_id*  
 Supplied/returned parameter. Specifies the identifier of the conversation group from which the session should be allocated. The **conv_group_id** is required only if **rtn_ctl**is set to WHEN_CONV_GROUP_ALLOC. When**rtn_ctl** specifies a different value and the **primary_rc** is AP_OK, this is a returned value.  
  
 *sense_data*  
 Returned parameter. Indicates an allocation error (retry or no-retry) and contains sense data.  
  
 *plu_alias*  
 Supplied parameter. Specifies the alias by which the partner LU is known to the local TP.  
  
 The **plu_alias** must match the name of a partner LU established during configuration.  
  
 The parameter is an 8-byte ASCII character string. It can consist of the following ASCII characters:  
  
- Uppercase letters  
  
- Numerals 0 through 9  
  
- Spaces  
  
- Special characters $, #, %, and @  
  
  The first character of this string cannot be a space.  
  
  If the value of this parameter is fewer than eight bytes, pad it on the right with ASCII spaces (0x20).  
  
  If you want to specify the partner LU with the **fqplu_name** parameter, fill this parameter with binary zeros.  
  
  For a user or group using TPs, 5250 emulators, and/or APPC applications, the system administrator can assign default local and remote LUs. In this case, the field is left blank or null and the default LUs are accessed when the user or group member starts an APPC program.  
  
  *mode_name*  
  Supplied parameter. Specifies the name of a set of networking characteristics defined during configuration.  
  
  The value of **mode_name** must match the name of a mode associated with the partner LU during configuration.  
  
  The parameter is an 8-byte EBCDIC character string. It can consist of characters from the type A EBCDIC character set:  
  
- Uppercase letters  
  
- Numerals 0 through 9  
  
- Special characters $, #, and @  
  
  The first character in the string must be an uppercase letter or a special character.  
  
  Do not use SNASVCMG in a mapped conversation. SNASVCMG is a reserved **mode_name** used internally by APPC.  
  
  *tp_name*  
  Supplied parameter. Specifies the name of the invoked TP. The value of **tp_name** specified by **MC_ALLOCATE** in the invoking TP must match the value of **tp_name** specified by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
  The parameter is a 64-byte EBCDIC character string and is case-sensitive. The **tp_name** parameter can consist of the following EBCDIC characters:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 through 9  
  
- Special characters $, #, @, and period (.)  
  
  If **tp_name** is fewer than 64 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  The SNA convention is that a service TP name can have up to four characters. The first character is a hexadecimal byte between 0x00 and 0x3F. The other characters are from the type AE EBCDIC character set.  
  
  *security*  
  Supplied parameter. Provides the information that the partner LU requires to validate access to the invoked TP. See the section **Possible values for the Security parameter** in this topic.  
  
  *Reserv6*  
  A reserved field.  
  
  *pwd*  
  Supplied parameter. Specifies the password associated with **user_id**.  
  
  The **pwd** parameter is required only if **security** is set to AP_PGM or AP_SAME. It must match the password for **user_id** that was established during configuration.  
  
  The **pwd** parameter is a 10-byte EBCDIC character string and is case-sensitive. It can consist of the following EBCDIC characters:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 through 9  
  
- Special characters $, #, @, and period (.)  
  
  If the password is fewer than 10 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  If the APPC automatic logon feature is to be used, the **pwd** character string must be hard-coded to MS$SAME. See the Remarks section for details.  
  
  *user_id*  
  Supplied parameter. Specifies the user identifier required to access the partner TP. It is required only if the security parameter is set to AP_PGM or AP_SAME.  
  
  The **user_id** parameter is a 10-byte EBCDIC character string and is case-sensitive. It must match one of the user identifiers configured for the partner TP.  
  
  The parameter can consist of the following EBCDIC characters:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 through 9  
  
- Special characters $, #, @, and period (.)  
  
  If **user_id** is fewer than 10 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  If the APPC automatic logon feature is to be used, the **user_id** character string must be hard-coded to MS$SAME. See the Remarks section for details.  
  
  *pip_dlen*  
  Supplied parameter. Specifies the length of the program initialization parameters (PIP) to be passed to the partner TP. The range is from 0 through 32767.  
  
  *pip_dptr*  
  Supplied parameter. Specifies the address of the buffer containing PIP data. Use this parameter only if **pip_dlen** is greater than zero.  
  
  PIP data can consist of initialization parameters or environmental setup information required by a partner TP or remote operating system. The PIP data must follow the general data stream (GDS) format. For more information, see your IBM SNA manual(s).  
  
  For Microsoft Windows, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
  *reserv7*  
  A reserved field.  
  
  *fqplu_name*  
  Supplied parameter. Specifies the fully qualified name of the partner LU. This must match the fully qualified name of the local LU defined in the remote node. The parameter consists of two type A EBCDIC character strings for the NETID and the LU name of the partner LU. The names are separated by an EBCDIC period (.).  
  
  This name must be provided if no **plu_alias** is specified. It can consist of the following EBCDIC characters:  
  
- 18Uppercase letters  
  
- Numerals 0 through 9  
  
- Special characters $, #, and @  
  
  If the value of this parameter is fewer than 17 bytes, pad it on the right with EBCDIC spaces (0x40).  
  
  *reserv8*  
  A reserved field.  
  
  *proxy_user*  
  Supplied parameter. Specifies a LPWSTR pointing to a Unicode string containing the user name to be impersonated using the privileged proxy feature. This field can only be used when the AP_EXTD_VCB bit is set on the **opext** field, indicating an extended VCB.  
  
  *proxy_domain*  
  Supplied parameter. Specifies a LPWSTR pointing to a Unicode string containing the domain name of the user to be impersonated using the privileged proxy feature. This field can only be used when the AP_EXTD_VCB bit is set on the **opext** field, indicating an extended VCB.  
  
  *reserv9*  
  A reserved field.  
  
## Possible Values for the Security Parameter  
 Based on the conversation security established for the invoked TP during configuration, use one of the following values:  
  
-   AP_NONE for an invoked TP that uses no conversation security.  
  
-   AP_PGM for an invoked TP that uses conversation security and thus requires a user identifier and password. Supply this information through the **user_id** and **pwd** parameters.  
  
-   AP_PROXY_PGM for an invoked TP with privileged proxy that uses conversation security and thus requires a user identifier and password. Pointers must be set up for **proxy_user** and **proxy_domain** to point to Unicode strings containing the user name and domain name of the user to be impersonated. The application does not need to set the **user_id** and **pwd** fields.  
  
-   AP_PROXY_SAME for a TP that has been invoked using privileged proxy with a valid user identifier and password supplied by the proxy, which in turn invokes another TP. Pointers must be set up for **proxy_user** and **proxy_domain** to point to Unicode strings containing the user name and domain name of the user to be impersonated. The application does not need to set the **user_id** and **pwd** fields.  
  
     For example, assume that TP A invokes TP B with a valid user identifier and password supplied by the privileged proxy, and TP B in turn invokes TP C. If TP B specifies the value AP_PROXY_SAME, APPC will send the LU for TP C the user identifier from TP A and an already-verified indicator. This indicator tells TP C to not require the password (if TP C is configured to accept an already-verified indicator).  
  
-   AP_PROXY_STRONG for an invoked TP with privileged proxy that uses conversation security and thus requires a user identifier and password provided by the privileged proxy mechanism. Pointers must be set up for **proxy_user** and **proxy_domain** to point to Unicode strings containing the user name and domain name of the user to be impersonated. The application does not need to set the **user_id** and **pwd** fields. AP_PROXY_STRONG differs from AP_PROXY_PGM in that AP_PROXY_STRONG does not allow clear-text passwords. If the remote system does not support encrypted passwords (strong conversation security), then this call fails.  
  
-   AP_SAME for a TP that has been invoked with a valid user identifier and password, which in turn invokes another TP.  
  
     For example, assume that TP A invokes TP B with a valid user identifier and password, and TP B in turn invokes TP C. If TP B specifies the value AP_SAME, APPC will send the LU for TP C the user identifier from TP A and an already-verified indicator. This indicator tells TP C to not require the password (if TP C is configured to accept an already-verified indicator).  
  
     When AP_SAME is used in an **MC_ALLOCATE** verb, your application must always provide values for the **user_id** and **pwd** parameters in the verb control block. Depending on the properties negotiated between Host Integration Server and the peer LU, the **MC_ALLOCATE** verb will send one of three kinds of Attach (FMH-5) messages, in this order of precedence:  
  
    1.  If the LUs have negotiated "already verified" security, then the Attach sent by Host Integration Server will not include the contents of the **pwd** parameter field specified in the VCB.  
  
    2.  If the LUs have negotiated "persistent verification" security, then the Attach sent by Host Integration Server will include the **pwd** parameter specified in the VCB, but only when the Attach is the first for the specified **user_id** parameter since the start of the LU-LU session, and will omit the **pwd** parameter on all subsequent Attaches (issued by your application or any other application using this LU-LU-mode triplet).  
  
    3.  If the LUs have not negotiated either of the above, then the Attach sent by Host Integration Server will omit both the **user_id** and **pwd** parameters on all Attaches.  
  
         Your application cannot tell which mode of security has been negotiated between the LUs, nor can it tell whether the **MC_ALLOCATE** verb it is issuing is the first for that LU-LU-mode triplet. So your application must always set the **user_id** and **pwd** parameter fields in the VCB when **security** is set to AP_SAME.  
  
         For more information on persistent verification and already verified security, see the SNA Formats Guide, section "FM Header 5:  Attach (LU 6.2)".  
  
-   AP_STRONG for an invoked TP that uses conversation security and thus requires a user identifier and password. Supply this information through the **user_id** and **pwd** parameters. AP_STRONG differs from AP_PGM in that AP_STRONG does not allow clear-text passwords. If the remote system does not support encrypted passwords (strong conversation security), then this call fails.  
  
     If the APPC automatic logon feature is to be used, **security** must be set to AP_PGM. See the Remarks section for details.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_UNSUCCESSFUL  
 Primary return code; the supplied parameter **rtn_ctl** specified immediate (AP_IMMEDIATE) return of control to the TP, and the local LU did not have an available contention-winner session.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_RETURN_CONTROL  
  
 Secondary return code; the value specified for **rtn_ctl** was not valid.  
  
 AP_BAD_SECURITY  
  
 Secondary return code; the value specified for **security** was not valid.  
  
 AP_BAD_SYNC_LEVEL  
  
 Secondary return code; the value specified for **sync_level** was not valid.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value specified for **tp_id** was not valid.  
  
 AP_PIP_LEN_INCORRECT  
  
 Secondary return code; the value of **pip_dlen** was greater than 32767.  
  
 AP_UNKNOWN_PARTNER_MODE  
  
 Secondary return code; the value specified for **mode_name** was not valid.  
  
 AP_BAD_PARTNER_LU_ALIAS  
  
 Secondary return code; APPC did not recognize the supplied **partner_lu_alias**.  
  
 AP_NO_USE_OF_SNASVCMG  
  
 Secondary return code; SNASVCMG is not a valid value for **mode_name**.  
  
 AP_INVALID_DATA_SEGMENT  
  
 Secondary return code; the PIP data was longer than the allocated data segment, or the address of the PIP data buffer was wrong.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after **MC_ALLOCATE**.  
  
 AP_ALLOCATION_FAILURE_NO_RETRY  
  
 Secondary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
 AP_ALLOCATION_FAILURE_RETRY  
  
 Secondary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with **MC_ALLOCATE**, it can indicate that no communications system could be found to support the local LU. (For example, the local LU alias specified with [TP_STARTED](../core/tp-started2.md) is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **MC_ALLOCATE** request.  
  
  When **MC_ALLOCATE** produces this return code for a Host Integration Server system configured with multiple nodes, there are two secondary return codes as follows:  
  
  0xF0000001  
  
  Secondary return code; no nodes have been started.  
  
  0xF0000002  
  
  Secondary return code; at least one node has been started, but the local LU (when **TP_STARTED** is issued) is not configured on any active nodes. The problem could be either of the following:  
  
- The node with the local LU is not started.  
  
- The local LU is not configured.  
  
  AP_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_CONV_BUSY  
  Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 **MC_ALLOCATE** establishes a mapped conversation.  
  
 The conversation state is RESET when the TP issues this verb. After successful execution (**primary_rc** is AP_OK), the state changes to SEND. If the verb does not execute, the state remains unchanged.  
  
 Several parameters of **MC_ALLOCATE** are EBCDIC or ASCII strings. A TP can use the CSV [CONVERT](../core/convert2.md) to translate a string from one character set to the other.  
  
 To send the **MC_ALLOCATE** request immediately, the invoking TP can issue [MC_FLUSH](../core/mc-flush1.md) or [MC_CONFIRM](../core/mc-confirm2.md) immediately after **MC_ALLOCATE**. Otherwise, the **MC_ALLOCATE** request accumulates with other data in the local LU's send buffer until the buffer is full.  
  
 By issuing **MC_CONFIRM** after **MC_ALLOCATE**, the invoking TP can immediately determine whether the allocation was successful (if **synclevel** is set to AP_CONFIRM_SYNC_LEVEL).  
  
 Normally, the value of the **MC_ALLOCATE** verb's **mode_name** parameter must match the name of a mode configured for the invoked TP's node and associated during configuration with the partner LU.  
  
 If one of the modes associated with the partner LU on the invoked TP's node is an implicit mode, the session established between the two LUs will be of the implicit mode when no mode name associated with the partner LU matches the value of **mode_name**.  
  
 Host Integration Server supports a feature called password substitution. This is a security feature supported by the latest version of the OS/400 operating system (V3R1) that encrypts any password that flows between two nodes on an Attach message. A password flows on an Attach whenever someone invokes an APPC transaction program specifying a user identifier and password. For example, this happens whenever anyone logs on to an AS/400.  
  
 Support for password substitution is indicated by setting bit 5 in byte 23 of the BIND request to 1 (which indicates that password substitution is supported). If the remote system sets this bit in the BIND response, Host Integration Server automatically encrypts the LU 6.2 conversation security password included in the FMH-5 Attach message. Host Integration Server APPC applications automatically take advantage of this feature by setting the **security** field of the VCB to AP_PGM or AP_STRONG in the **MC_ALLOCATE** request.  
  
 If an APPC application wants to force an encrypted password to flow, the application can specify AP_STRONG for the **security** field in the VCB in the **MC_ALLOCATE** request. This option is implemented as defined in OS/400 V3R1, and is documented in the OS/400 CPI-C programmer reference as CM_SECURITY_PROGRAM_STRONG, where the LU 6.2 **pwd** (password) field is encrypted before it flows over the physical network.  
  
 The password substitution feature is currently only supported by OS/400 V3R1 or later. If the remote system does not support this feature, Host Integration Server will UNBIND the session with the sense code of 10060006. The two nodes negotiate whether or not they support this feature in the BIND exchange. Host Integration Server sets a bit in the BIND, and also adds some random data on the BIND for encryption. If the remote node supports password substitution, it sets the same bit in the BIND response, and adds some (different) random data for decryption.  
  
 Host Integration Server supports automatic logon for APPC applications. This feature requires specific configuration by the network administrator: The APPC application must be invoked on the LAN side from a client of Host Integration Server. The client must be logged into a Windows domain, but can be any platform that supports the Host Integration Server APPC APIs.  
  
 The client application is coded to use "program" level security, with a special hard-coded APPC user name MS$SAME and password MS$SAME. When this session allocation flows from client to Host Integration Server, the Host Integration Server server looks up the host account and password corresponding to the Windows account under which the client is logged in, and substitutes the host account information into the APPC attach message it sends to the host.  
  
> [!NOTE]
>  It is illegal for the remote node to set the bit specifying password substitution and not add the random data.  
  
 According to IBM, there are implementations of LU 6.2 password substitution that do not support password substitution but do echo the password substitution bit back to Host Integration Server, without specifying any random data. When they do this, Host Integration Server will UNBIND the session with the sense code 10060006.This sense code is interpreted as:  
  
- 1006 = Required field or parameter missing.  
  
- 0006 = A required subfield of a control vector was omitted.  
  
  Host Integration Server should also log an Event 17 (APPC session activation failure: BIND negative response sent).  
  
  The correct solution is for the failing implementation to be fixed. However, as a short-term workaround, the following Host Integration Server SNA Service registry setting can be set:   **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\snaservr\parameters\NOPWDSUB: REG_SZ: YES**  
  
  When this parameter is specified in the registry, Host Integration Server password substitution support will be disabled.  
  
  Several updates have been made to Host Integration Server to allow a privileged APPC application to open an APPC conversation using the Single Sign-On feature on behalf of any defined Windows user. This is referred to as the privileged proxy feature. An extension has been added to the APPC **MC_ALLOCATE** verb to invoke this feature.  
  
  An APPC application becomes privileged by being started in a Windows user account that is a member of a special Windows group. When a Host Security Domain is configured, SNA Manager will define a second Windows group for use with the host security features of Host Integration Server. If the user account under which the actual client is running is a member of this second Windows group, the client is privileged to initiate an APPC conversation on behalf of any user account defined in the Host Account Cache.  
  
  The following illustrates how the privileged proxy feature works:  
  
  The Host Integration Server administrator creates a Host Security Domain called APP. SNA Manager now creates two Windows groups. The first group is called APP and the second is called APP_PROXY for this example. Users that are assigned to the APP group are enabled for Single Sign-On. Users assigned to the APP_PROXY group are privileged proxies. The administrator adds the Windows user AppcUser to the APP_PROXY group using the Users button on the Host Security Domain property dialog box in SNA Manager.  
  
  The administrator then sets up an APPC application on the Host Integration Server server to run as a Windows service called APPCAPP, and that service has been set up to operate under the AppcUser user account. When APPCAPP runs, it opens an APPC session via an **ALLOCATE** verb using the extended VCB format and specifies the Windows user name of the desired user, UserA (for example).  
  
  The SNA Service sees the session request coming from a connection that is a member of the Host Security Domain APP. The Client/Server interface tells the SNA Service that the actual client is AppcUser.  
  
  The SNA Service checks to see if AppcUser is a member of the APP_PROXY group. Because AppcUser is a member of APP_PROXY, the SNA Service inserts the Username/Password for UserA in the APPC Attach (FMH-5) command and sends it off to the partner TP.  
  
  In order to support the privileged proxy feature, the APPC application must implement the following program logic:  
  
  The APPC application must determine the Windows user ID and domain name that it wishes to impersonate.  
  
  The APPC application must set the following parameters before calling the **MC_ALLOCATE** verb:  
  
  Enable the use of the extended **MC_ALLOCATE** verb control block structure by setting the AP_EXTD_VCB flag in the **opext** field.  
  
  Set security to AP_PROXY_SAME, AP_PROXY_PGM, or AP_PROXY_STRONG.  
  
  Set up the pointers for **proxy_user** and **proxy_domain** to point to Unicode strings containing the user name and domain name of the user to be impersonated.  
  
> [!NOTE]
>  The application does not need to set up the **user_id** and **pwd** fields in the **MC_ALLOCATE** VCB.  
  
 When the APPC application performs the above steps and issues the **MC_ALLOCATE** verb, the Host Integration Server server will perform a lookup in the host security domain for the specified Windows user and set the user ID and password fields in the FMH-5 Attach message sent to the remote system.