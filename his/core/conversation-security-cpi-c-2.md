---
title: "Conversation Security (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eee5c2f-74a4-4793-9ea6-5b949a640a13
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Conversation Security (CPI-C)
You can use conversation security to require that the invoking transaction program (TP) provides a user identifier and password before Common Programming Interface for Communications (CPI-C) allocates a conversation with the invokable TP.  
  
 For the invoking TP, conversation security is activated and configured (with user identifier and password) through the symbolic destination name in SNA Manager or by the following calls, which override the symbolic destination name:  
  
- [Set_Conversation_Security_Type](./set-conversation-security-type-cpi-c-1.md)  
  
- [Set_Conversation_Security_User_ID](./set-conversation-security-user-id-cpi-c-1.md)  
  
- [Set_Conversation_Security_Password](./set-conversation-security-password-cpi-c-1.md)  
  
  For the invokable TP, conversation security is activated and configured through registry or environment variables on the computer where the invokable TP is located.  
  
  With communication involving more than two TPs, the verification of a user identifier and password can be passed from one TP to another. Suppose that TP A invokes TP B, which requires security information, and TP B in turn invokes TP C, which also requires security information. TP B can inform TP C that conversation security has already been verified.  
  
  For information about the registry or environment variables affecting conversation security, see [Configuring Invokable TPs](../core/configuring-invokable-tps-cpi-c-1.md). For information about symbolic destination names and side information, see [Side Information for CPI-C Programs](../core/side-information-for-cpi-c-programs1.md).