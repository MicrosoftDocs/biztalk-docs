---
title: "How to Create a 5250 Remote APPC LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1af8278-b071-4fb8-87b3-135c9eed145c
caps.latest.revision: 3
---
# How to Create a 5250 Remote APPC LU
The following procedure details creating a 5250 remote APPC LU manually.  
  
### To create a 5250 remote APPC LU  
  
1.  In SNA Manager, expand the server on which to add the **Remote APPC LU**.  
  
2.  Expand **SNA Service**, and right-click **Remote APPC LU**.  
  
3.  Point to **New**, and then select **Remote LU**.  
  
4.  On the **General** tab:  
  
    -   Enter Connection.  
  
    -   Enter LU Alias.  
  
    -   Enter Network Name.  
  
    -   Enter LU Name.  
  
    -   Enter Uninterpreted Name.  
  
    -   Enter Comment (optional).  
  
5.  On the **Options** tab:  
  
    -   Select if this remote LU supports parallel sessions.  
  
    -   Select implicit incoming remote LU.  
  
    -   Select Session-Level security.  
  
    -   Select SyncPoint support.  
  
6.  Click **OK**.  
  
7.  Right-click **SNA Service**, and click **Save configuration**.  
  
8.  Stop and then start SNA service.  
  
## See Also  
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [Creating Connections](../core/creating-connections.md)   
 [Creating a 3270 Connection with a Wizard](../core/creating-a-3270-connection-with-a-wizard.md)   
 [How to Create a 3270 Connection Manually](../core/how-to-create-a-3270-connection-manually.md)   
 [Creating a 5250 Connection with a Wizard](../core/creating-a-5250-connection-with-a-wizard.md)   
 [How to Create a 5250 Connection Manually](../core/how-to-create-a-5250-connection-manually.md)   
 [How to Create a 5250 Local APPC LU](../core/how-to-create-a-5250-local-appc-lu.md)