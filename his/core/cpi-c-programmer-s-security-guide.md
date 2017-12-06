---
title: "CPI-C Programmer&#39;s Security Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f69c4aa-40d0-40c8-b207-c5ea3b4a0c21
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# CPI-C Programmer&#39;s Security Guide
The following topics discuss security as it applies to the CPI-C section of the [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] SDK.  
  
## About CPI-C Security for Developers  
 The Common Programming Interface for Communications (CPI-C) is a platform-independent API designed to simplify the use APPC verbs, and has many of the same issues and features as APPC.  
  
 This section discusses security practices and issues that apply to C-language applications that you write to use CPI-C to exchange data between a Host Integration Server system and a computer or computers in a Systems Network Architecture (SNA) environment.  
  
### Session Security Configuration Using SNACFG  
 You can use the utility SNACFG to set session security for a remote LU. Possible values are none, use a plaintext key, and use a scrambled key.  
  
### Conversation Security in CPI-C  
 Conversation security in CPI-C controls who can connect to a remote LU. You can find more information in the topic [Conversation Security (CPI-C)](../core/conversation-security-cpi-c.md).  
  
 A programmer controls conversation security using the [Set_Conversation_Security_Type (CPI-C)](../Topic/Set_Conversation_Security_Type%20\(CPI-C\)2.md) call and sets user credentials using the [Set_Conversation_Security_User_ID (CPI-C)](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md) and [Set_Conversation_Security_Password (CPI-C)](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md) call from the CPI-C SDK.