---
title: "Support for CPI-C Automatic Logon1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb3e53d8-1751-43e5-958e-8ef1c8835a9e
caps.latest.revision: 3
---
# Support for CPI-C Automatic Logon
This section describes the support for automatic logon for Common Programming Interface for Communications (CPI-C) applications that is available in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. This feature requires specific configuration by the network administrator. The CPI-C application must be invoked on the local area network (LAN) side from a client of Host Integration Server. The client must be logged into a Windows domain, and the client application must be running on a supported version of Windows.  
  
 To use this feature, the CPI-C client application is coded to use program level security, with a special hard-coded user name of MS$SAME and password of MS$SAME. When this session allocation flows from client to SNA services, Host Integration Server looks up the host account and password corresponding to the Windows account under which the client is logged on, and substitutes the host account information into the APPC attach message it sends to the host.  
  
 Use the following function calls to use CPI-C:  
  
-   Call the [Set_Conversation_Security_Type](../Topic/Set_Conversation_Security_Type%20\(CPI-C\)2.md) function with the *conversation_security_type* parameter set to CM_SECURITY_PROGRAM.  
  
-   Call the [Set_Conversation_Security_User_ID](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md) function with the *security_user_ID* parameter set to the MS$SAME string and the *security_user_ID_length* parameter set to 7.  
  
-   Call the [Set_Conversation_Security_Password](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md) function with the *security_password* parameter set to the MS$SAME string and the *security_password_length* parameter set to 7.