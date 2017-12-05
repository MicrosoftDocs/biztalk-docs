---
title: "Creating a 3270 Connection with a Wizard2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b41aa1b0-fd1e-4ab6-8f2e-9ec75f3a12b0
caps.latest.revision: 3
---
# Creating a 3270 Connection with a Wizard
The following procedure details using a wizard to create a 3270 connection. The 3270 Continuous link service will be used as an example.  
  
### To create a 3270 connection using a wizard  
  
1.  In SNA Manager, right-click the server on which to add a connection.  
  
2.  Point to **All Tasks**, and then select the **3270 Wizard** option.  
  
3.  Click **Next** on the **Welcome** screen.  
  
4.  Select the computer where SNA service resides, and click **Next**.  
  
5.  Enter a **Name** for the connection, **DM3270**, and click **Next**.  
  
6.  Select the appropriate link service, **SNADEMO1**, and click **Next**.  
  
7.  Accept the default Local Node ID information, and click **Next**.  
  
8.  Accept the default PU address information, and click **Next**.  
  
9. Accept the default LU information, and click **Next**.  
  
10. Click **Add** to add a member (user).  
  
11. Select a member, click **Add**, and then click **OK**.  
  
12. Click **Next**.  
  
13. Click **Finish** to complete the wizard.  
  
14. Click **OK** on the final wizard information page.  
  
15. When the wizard completes, right-click **SNA Service**, and click **Save configuration**.  
  
16. Stop and then start SNA service.  
  
## See Also  
 [IP-DLC Link Service](../core/ip-dlc-link-service1.md)   
 [Creating Connections](../core/creating-connections2.md)   
 [How to Create a 3270 Connection Manually](../core/how-to-create-a-3270-connection-manually2.md)   
 [Creating a 5250 Connection with a Wizard](../core/creating-a-5250-connection-with-a-wizard1.md)   
 [How to Create a 5250 Connection Manually](../core/how-to-create-a-5250-connection-manually1.md)   
 [How to Create a 5250 Local APPC LU](../core/how-to-create-a-5250-local-appc-lu2.md)   
 [How to Create a 5250 Remote APPC LU](../core/how-to-create-a-5250-remote-appc-lu2.md)