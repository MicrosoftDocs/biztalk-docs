---
description: "Learn more about: How to Create a 3270 Printer LU"
title: "How to Create a 3270 Printer LU1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a 3270 Printer LU
The following procedure details how to create a printer LU.  
  
### To create a 3270 printer LU  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, **DM3270**, point to **New**, and then click **Printer LU**.  
  
     You can define LUs in this **Properties** dialog box. Keep the default for the **LU Number** box as 3. Three is the first available number, because two was used in the previous example and one is reserved for the host.  
  
     The LU number is meaningful to the connection. You can add a user-friendly name in the **LU Name** box.  
  
3.  Type the LU Name, **LU 4**. (You might have expected LU 3, but LU 3 is reserved for the LU3 demo.) Leave the other boxes as they are.  
  
4.  Type a comment (optional).  
  
5.  If you are using compression, select the **Use Compression** box.  
  
6.  If the workstation is secured, select the **User Workstation Secured** box.  
  
7.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu1.md)   
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua-2.md)   
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu2.md)   
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu1.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu2.md)   
 [Creating LUs](../core/creating-lus2.md)
