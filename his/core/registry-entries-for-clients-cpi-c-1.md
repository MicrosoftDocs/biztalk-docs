---
title: "Registry Entries for Clients (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 722e6477-5280-4432-83f5-80c1900e5d79
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Registry Entries for Clients (CPI-C)
The following list gives details about registry entries for client computers. For each transaction program (TP) type, the applicable variables and their locations are shown in [Configuring Clients to Support TPs (CPI-C)](../core/configuring-clients-to-support-tps-cpi-c-1.md).  
  
 <strong>OtherDependencies:</strong>REG_MULTI_SZ:SnaBase  
 For a TP running as a service, ensures that the SnaBase service is started before the TP is started. This entry belongs under the **Linkage** subkey.  
  
 <strong>SNAServiceType:</strong>REG_DWORD:{ 0x5 &#124; 0x6 &#124; 0x1A }  
 Indicates the type of TP. Use a value of 0x5 for an autostarted queued TP, 0x6 for an autostarted nonqueued TP, and 0x1A for an operator-started TP.  
  
 Note that the value for an autostarted TP running as a service must be 0x5, because these TPs are always queued, as described in [Invokable TPs](../core/invokable-tps-cpi-c-2.md).  
  
 <strong>PathName:</strong>REG_EXPAND_SZ: *path*  
 For an autostarted TP running as an application, specifies the path and file name of the TP. The data type of REG_EXPAND_SZ means that the path can contain an expandable data string For example, %SystemRoot% represents the directory containing the Windows system files. Note that for a TP running as a service, an equivalent entry is inserted by the **CreateService** call. No additional path entry is needed.  
  
 <strong>LocalLU:</strong>REG_SZ: *LUalias*  
 Specifies the alias of the local LU to be used when this TP is started on this computer.  
  
 <strong>Parameters:</strong>REG_SZ: *ParameterList*  
 Lists parameters to be used by the TP. Separate parameters with spaces.  
  
 <strong>Timeout:</strong>REG_DWORD: *number*  
 Specifies the time, in milliseconds, that an [Accept_Conversation](./accept-conversation-cpi-c-2.md) will wait before timing out. Specify *number* in decimal. The registry editor converts this to hexadecimal before displaying it. The default is infinity (no limit).  
  
 <strong>AcceptNames:</strong>REG_SZ: *TPNameList*  
 Lists additional names under which the invokable TP can be invoked. Separate TP names with spaces. The default is none. If an invokable TP does not issue a [Specify_Local_TP_Name](./specify-local-tp-name-cpi-c-2.md) for each name configured under AcceptNames in the registry, that TP will fail.  
  
 <strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }  
 Indicates whether this TP supports conversation security. The default is NO.  
  
 <strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }  
 Indicates whether this TP can be invoked with a user identifier and password that have already been verified. **AlreadyVerified** is ignored if **ConversationSecurity** is set to NO.  
  
 For a diagram of three TPs in a conversation, where the third TP can be invoked with a password that is already verified by the second TP, see [Communication Between TPs](../core/communication-between-tps-cpi-c-2.md). The following table shows the requirements for using password verification in a chain of TPs.  
  
|First TP (an invoking TP)|Second TP (invokable TP that confirms password, and then invokes another TP)|Third and subsequent TPs (invokable TPs that invoke other TPs)|  
|---------------------------------|------------------------------------------------------------------------------------|----------------------------------------------------------------------|  
|Does not need registry or environment variables.|**ConversationSecurity** setting must be YES.|**ConversationSecurity** setting must be YES.|  
|Does not need registry or environment variables.|**AlreadyVerified** setting can be YES or NO.|**AlreadyVerified** setting must be YES.|  
|Symbolic destination name or **Set_Conversation_**<br />**Security_Type** in this TP specifies PROGRAM for the security type. As a result, the TP passes along the user identifier and password supplied in the symbolic destination name (or through calls (1)).|Symbolic destination name or **Set_Conversation_**<br />**Security_Type** in this TP specifies SAME for the security type. As a result, after confirming the user identifier and password, the TP passes along the user identifier and an already-verified flag.|Symbolic destination name or **Set_Conversation_**<br />**Security_Type** in this TP specifies SAME for the security type. As a result, the TP passes along the user identifier as received, along with the already-verified flag.|  
  
> [!NOTE]
>  Set_Conversation_Security_User_ID or **Set_Conversation_Security_Password** overwrites the user identifier and password specified in the symbolic destination name.  
  
> [!NOTE]
>  If you set **AlreadyVerified** to NO, this TP cannot join in a chain of conversations where password verification is already done. (The exception to this is when **ConversationSecurity** is set to NO, in which case the TP could be the final TP in such a chain, because it performs no checking.)  
  
> [!NOTE]
>  If you are configuring a TP that sometimes needs to confirm a password and sometimes accepts an already-verified flag, set AlreadyVerified to YES and configure the *UsernameX* variable appropriately. In this case, whenever the TP is invoked without the already-verified flag set, AlreadyVerified is ignored. Verification is attempted with the user identifier and password configured for the TP.  
  
> [!NOTE]
>  The default for AlreadyVerified is NO. If you set AlreadyVerified to YES, make sure that ConversationSecurity is also set to YES.  
  
 ***Username1***  :REG_SZ: *Password1*... ***UsernameX***:REG_SZ: *PasswordX*  
 Sets one or more user names and passwords to be compared with those sent by the invoking TP. The user name and password can each be as many as 10 characters. Both parameters are case-sensitive.  
  
 This variable is ignored if conversation security is not activated or if the password has already been verified, as described for the AlreadyVerified entry.