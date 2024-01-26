---
description: "Learn more about: How to Create a 5250 Local APPC LU"
title: "How to Create a 5250 Local APPC LU1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a 5250 Local APPC LU
The following procedure details creating a 5250 local APPC LU manually.  
  
### To create a 5250 local APPC LU  
  
1.  In SNA Manager, expand the server on which to add the **Local APPC LU**.  
  
2.  Expand **SNA Service**, and right-click **Local APPC LU**.  
  
3.  Point to **New**, and then select **Local LU**.  
  
4.  On the **General** tab:  
  
    -   Enter LU Alias.  
  
    -   Enter Network Name.  
  
    -   Enter LU Name.  
  
    -   Enter Comment (optional).  
  
5.  On the **Advanced** tab:  
  
    -   Select if this is a member of default local APPC LU pool.  
  
    -   Enter time-out in seconds for starting invokable TPs.  
  
    -   Select implicit incoming remote LU.  
  
    -   Select LU 6.2 type.  
  
    -   Select SyncPoint support.  
  
6.  Click **OK**.  
  
7.  Right-click **SNA Service**, and click **Save configuration**.  
  
8.  Stop and then start SNA service.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [Creating Connections](../core/creating-connections1.md)   
 [Creating a 3270 Connection with a Wizard](../core/creating-a-3270-connection-with-a-wizard1.md)   
 [How to Create a 3270 Connection Manually](../core/how-to-create-a-3270-connection-manually1.md)   
 [Creating a 5250 Connection with a Wizard](../core/creating-a-5250-connection-with-a-wizard2.md)   
 [How to Create a 5250 Connection Manually](../core/how-to-create-a-5250-connection-manually2.md)   
 [How to Create a 5250 Remote APPC LU](../core/how-to-create-a-5250-remote-appc-lu1.md)
