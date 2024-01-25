---
description: "Learn more about: CPI-C Programmer&#39;s Security Guide"
title: "CPI-C Programmer&#39;s Security Guide2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CPI-C Programmer&#39;s Security Guide
The following topics discuss security as it applies to the CPI-C section of the Host Integration Server SDK.  
  
## About CPI-C Security for Developers  
 The Common Programming Interface for Communications (CPI-C) is a platform-independent API designed to simplify the use APPC verbs, and has many of the same issues and features as APPC.  
  
 This section discusses security practices and issues that apply to C-language applications that you write to use CPI-C to exchange data between a Host Integration Server system and a computer or computers in a Systems Network Architecture (SNA) environment.  
  
### Session Security Configuration Using SNACFG  
 You can use the utility SNACFG to set session security for a remote LU. Possible values are none, use a plaintext key, and use a scrambled key.  
  
### Conversation Security in CPI-C  
 Conversation security in CPI-C controls who can connect to a remote LU. You can find more information in the topic [Conversation Security (CPI-C)](../core/conversation-security-cpi-c-2.md).  
  
 A programmer controls conversation security using the [Set_Conversation_Security_Type (CPI-C)](./set-conversation-security-type-cpi-c-1.md) call and sets user credentials using the [Set_Conversation_Security_User_ID (CPI-C)](./set-conversation-security-user-id-cpi-c-1.md) and [Set_Conversation_Security_Password (CPI-C)](./set-conversation-security-password-cpi-c-1.md) call from the CPI-C SDK.
