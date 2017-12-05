---
title: "How to Use Already Verified Authentication1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe63775f-0935-493c-8cce-2048f21265ea
caps.latest.revision: 3
---
# How to Use Already Verified Authentication
You can set the **Use Already Verified or Persistent Verification authentication** option on the remote environment (RE) Security property page in Transaction Integrator (TI) Manager.  
  
### To view or modify the Security properties for an RE  
  
1.  Start TI Manager.  
  
2.  Right-click the RE, and then click **Properties**.  
  
3.  Click the **Security** tab, and then select the **Set security on** check box.  
  
 When you select the **Use Already Verified or Persistent Verification authentication** check box, only a user ID is sent to the mainframe; that is, no password is sent, provided the mainframe partner allows it. The mainframe relies on the assumption that this user ID has already been authenticated and does not require a password. The SNA mode on the mainframe must specify this type of authentication. For CICS applications, the mode setting is determined by the ATTACHSEC=IDENTIFY parameter of the Sessions definition used for the connection.  
  
## See Also  
 [Security Implications](../core/security-implications2.md)