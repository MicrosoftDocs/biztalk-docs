---
title: "How to Create a 3270 Connection Manually1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58aa07fc-b4b4-4dd4-bbaf-66ee5bc88fe3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create a 3270 Connection Manually
The following procedure details creating a 3270 connection manually.  
  
### To create a 3270 connection manually  
  
1. In SNA Manager, expand the server on which to create the connection, and then expand **SNA Service**.  
  
2. Right-click **Connections**, point to **New**, and then click the type of connection (802.2) to be created.  
  
3. Configure the **Connection Properties**. You are required to specify which link service to use for the connection, as well as the name of the connection and additional information. The choices you make depend on the purpose of the connection.  
  
    The following information must be configured correctly to make a connection:  
  
   -   General Tab  
  
   -   Address Tab  
  
   -   System Identification Tab  
  
   -   DLC 802.2 Tab  
  
4. Click **OK**.  
  
5. Right-click **SNA Service**, and then click **Save configuration**.  
  
6. Stop and then start SNA service.  
  
   To display this dialog box after the connection has been created, double-click the connection in the tree view, or select the connection, and click **Properties** in the **View** menu.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [Creating Connections](../core/creating-connections1.md)   
 [Creating a 3270 Connection with a Wizard](../core/creating-a-3270-connection-with-a-wizard1.md)   
 [Creating a 5250 Connection with a Wizard](../core/creating-a-5250-connection-with-a-wizard2.md)   
 [How to Create a 5250 Connection Manually](../core/how-to-create-a-5250-connection-manually2.md)   
 [How to Create a 5250 Local APPC LU](../core/how-to-create-a-5250-local-appc-lu1.md)   
 [How to Create a 5250 Remote APPC LU](../core/how-to-create-a-5250-remote-appc-lu1.md)