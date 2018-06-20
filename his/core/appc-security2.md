---
title: "APPC Security2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b3cc852-bcd1-4254-bb68-64beff6e9d34
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Security
Owners of APPC transaction programs may want to allow only a limited set of users to start the program. APPC provides a mechanism, called APPC conversation security, by which the client transaction program identifies its user to the server system.  
  
 There are three levels of security for client programs: None, Same, and Program:  
  
- If the level of security is None, the client system sends no security information (user ID or password).  
  
- If the level of security is set to Same, APPC tries to determine a user ID for the client program. If the server system requires a password and the client system permits APPC to retrieve one for the user ID, APPC will also send the password to the server system. If no user ID is available, or if the server requires a password but the client system does not allow APPC to retrieve the password, no security information is sent to the server. This is sometimes referred to as downgraded to security NONE.  
  
- If the security level is set to Program, the client transaction program will override any security information that the local system may provide. The client program must supply both a user ID and a password. CPI-C programs may get the user ID and password by either prompting the user to enter the information or by checking the CPI-C side information. Not all systems allow this option.  
  
  If the client program uses SECURITY=SAME or SECURITY=PROGRAM, APPC on the server must check the user ID and password regardless of the server transaction's security requirements. This requirement can cause unexpected problems and is not recommended.  
  
### To configure session security for remote LUs  
  
1.  In the SNA Manager tree, expand an SNA subdomain, expand the server you want to work with, expand **SNA service**, and then expand **Remote APPC LUs**.  
  
2.  Right-click the LU that you want to configure, and click **Properties**.  
  
3.  Click the **Options** tab. Under **Session-Level Security**, select an option.  
  
4.  Click **OK**.  
  
5.  On the **Action** menu, click **Save configuration**.  
  
6.  To put the changes into effect, you must restart the server.  
  
> [!NOTE]
>  Setting the security for remote LU sessions is optional.  
  
## See Also  
 [Transaction Programs](../core/transaction-programs2.md)   
 [Understanding Connectivity](../core/understanding-connectivity1.md)