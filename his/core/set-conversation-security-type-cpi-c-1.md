---
title: "Set_Conversation_Security_Type (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc5c4d49-9b1c-4934-bb31-3d569947416b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Conversation_Security_Type (CPI-C)
The **Set_Conversation_Security_Type** call (function name **cmscst**) is issued by the invoking program to specify the information the partner logical unit (LU) requires to validate access to the invoked program.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Conversation_Security_Type(   
  unsigned char FAR *conversation_ID,          
  CM_INT32 FAR *conversation_security_type,    
    CM_INT32 FAR *return_code                    
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *conversation_security_type*  
 Supplied parameter. Specifies the information the partner LU requires to validate access to the invoked program. Based on the conversation security established for the invoked program during configuration, use one of the following values:  
  
 CM_SECURITY_NONE  
 To indicate that the invoked program uses no conversation security.  
  
 CM_SECURITY_PROGRAM  
 To indicate that the invoked program uses conversation security and thus requires a user identifier and password.  
  
 CM_SECURITY_SAME  
 To indicate that the user ID is sent on the allocate request to node services in the partner LU. This setting is also used to specify that the invoked program, invoked with a valid user identifier and password, in turn invokes another program (as illustrated in [Communication Between TPs](./communication-between-tps-cpi-c-2.md)). For example, assume that program A invokes program B with a valid user identifier and password, and program B in turn invokes program C. If program B specifies the value CM_SECURITY_SAME, CPI-C will send the LU for program C, the user identifier from program A, and an already-verified indicator. This indicator tells program C not to require the password (if program C is configured to accept an already-verified indicator).  
  
 When CM_SECURITY_SAME is used, your application must always call [Set_Conversation_Security_User_ID](../core/set-conversation-security-user-id-cpi-c-1.md) and [Set_Conversation_Security_Password](../core/set-conversation-security-password-cpi-c-1.md) to provide values for the *security_user_ID* and *security_password* parameters. Depending on the properties negotiated between SNA Server and the peer LU, the **Allocate** function will send one of 3 kinds of Attach (FMH-5) messages, in this order of precedence:  
  
1. If the LUs have negotiated already verified security, the Attach sent by SNA Server will not include the contents of the security_password parameter field specified by Set_Conversation_Security_Password.  
  
2. If the LUs have negotiated persistent verification security, the Attach sent by SNA Server will include the security_password parameter specified by Set_Conversation_Security_Password, but only when the Attach is the first for the specified security_user_ID parameter set by Set_Conversation_Security_User_ID since the start of the LU-LU session, and will omit the security_password parameter on all subsequent Attaches (issued by your application or any other application using this LU-LU-mode triplet).  
  
3. Your application cannot tell which mode of security has been negotiated between the LUs, nor can it tell whether the **Allocate** function it is issuing is the first for that LU-LU-mode triplet. So your application must always call Set_Conversation_Security_User_ID and Set_Conversation_Security_Password to set the security_user_ID and security_password parameters when conversation_security_type is set to CM_SECURITY_SAME.  
  
   For more information on persistent verification and already verified security, see the SNA Formats Guide, section "FM Header 5: Attach (LU 6.2)."  
  
   If the CPI-C automatic logon feature is to be used, this parameter must be set to CM_SECURITY_PROGRAM. For details, see the Remarks section later in this topic.  
  
   *return_code*  
   The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is not in INITIALIZE state.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* or *conversation_security_type* is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.  
  
## Remarks  
 This call overrides the initial security type from the side information specified by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md). This call cannot be issued after [Allocate](../core/allocate-cpi-c-2.md) has been issued.  
  
 If the conversation security type is set to CM_SECURITY_NONE, the user identifier and password are ignored when the conversation is allocated.  
  
 A conversation security type of CM_SECURITY_SAME is intended for use between nodes which have the same set of user IDs and which accept user validation performed on one node as validating the user for all nodes. A password is not used in this case except for the initial validation of the user ID.  
  
 Automatic logon for CPI-C applications is supported by Host Integration Server. This feature requires specific configuration by the network administrator. The CPI-C application must be invoked on the LAN side from a client of SNA Server. The client must be logged into a Microsoft Windows domain, but can be any platform that supports SNA Server CPI-C APIs.  
  
 The client application is coded to use program level security, with a special hard-coded CPI-C user name MS$SAME and password MS$SAME. When this session allocation flows from client to SNA Server, the SNA Server looks up the host account and password corresponding to the Windows account under which the client is logged on, and substitutes the host account information into the APPC attach message it sends to the host.