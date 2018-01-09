---
title: "How to Create a 3270 Downstream LU2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a9da1c6-71b4-4688-b27c-84e1f8e2f250
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create a 3270 Downstream LU
The following procedure details how to create a downstream LU.  
  
### To create a 3270 downstream LU  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, **DM3270**, point to **New**, and then click **Downstream LU**.  
  
     You can define LUs in this **Properties** dialog box. Keep the default for the **LU Number** box as 5. Five is the next available number, because two, three, and four were used in the previous examples and one is reserved for the host.  
  
     The LU number is meaningful to the connection. You can add a user-friendly name in the **LU Name** box.  
  
3.  Type the LU Name, **LU 6**. Leave the other boxes as they are.  
  
4.  Type a comment (optional).  
  
5.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu1.md)   
 [How to Create a 3270 Printer LU](../core/how-to-create-a-3270-printer-lu1.md)   
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua-2.md)   
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu1.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu2.md)   
 [Creating LUs](../core/creating-lus2.md)