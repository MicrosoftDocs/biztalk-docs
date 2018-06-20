---
title: "How to Configure Downstream Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a9dd2ab-6205-46e9-950b-8eaf6bc135b7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure Downstream Connections
You can configure [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to enable downstream LUs to communicate with the host. Following are the general procedures:  
  
1. Gather needed information about the host and downstream systems, including information about identifiers, such as addresses and exchange identification (XID), and information about Max BTU Length.  
  
2. Configure the host connection as you would configure any other host connection. When specifying the remote end for the connection, select **Host System**.  
  
3. Select the host connection and assign and configure one or more new downstream LUs.  
  
4. Optionally, you can put downstream LUs into a pool to maximize their availability.  
  
5. Configure the downstream connection. When specifying the remote end for the connection, select **Downstream**.  
  
    The downstream connection can be an 802.2, SDLC, or X.25 connection. It cannot be a channel connection.  
  
6. Select the downstream connection and associate the downstream LUs (from step 3) and LU pools (from step 4) with that connection.  
  
7. If necessary, reorder the downstream LU numbers; that is, the LU numbers used by the downstream system.  
  
    A downstream LU has two LU numbers: one recognized by the downstream system and one recognized by the host. These numbers need not match.  
  
   To put configuration changes into effect, save the configuration file and restart the server (if you have added a link service or connection).  
  
> [!NOTE]
>  It is recommended that you manually separate the sessions of your downstream pools if you are upgrading from SNA Server 4.0 or later. If this is not done, you may experience incorrect behavior from Host Integration Server when attempting to connect downstream client computers.  
  
 After creating the downstream LUs, you must associate them with the downstream connection they will use. Downstream LUs do not stand alone and need to be mapped to the upstream LU. Associating the LUs with the upstream connection maps the correct downstream LUs to the correct upstream LUs.  
  
 Downstream LUs have two parameters:  
  
- The LU number, which identifies the LU to the host.  
  
- The downstream LU number, which identifies an LU or LU pool to the downstream system.  
  
  The LU number and the downstream LU number need not match, and probably will not match. The downstream LU number should match the LU number on the downstream system.  
  
  Check with the host administrator for the correct value of the LU number. It should match the LOCADDR= parameter of the LU definition in VTAM or in the NCP Gen. If the number you specify has already been assigned to an LU or an APPC LU-LU pair on the current connection, you must change the number. The range for LU numbers is 1 through 254.  
  
  Host Integration Server assigns a downstream LU number to each LU or LU pool assigned to the downstream connection. Host Integration Server assigns downstream LU numbers starting with 2 and ascending sequentially. Therefore, one way to change downstream LU numbers is to reorder the list of LUs for the downstream connection. Another way to change downstream LU numbers is to use empty LU pools to take up unwanted numbers, leaving the correct (larger) numbers for other LU pools or LUs.  
  
> [!NOTE]
>  The LU numbers generated for an LU range are sequential. If the numbers assigned by your host administrator are not sequential, you can modify the numbers of individual LUs after they have been created.  
  
 You can move one or more downstream LUs to a different host connection, regardless of whether the LUs were created as part of a range. Although downstream LUs can be associated with multiple downstream connections, they can be assigned to only one host connection.  
  
 You can configure multiple LUs simultaneously by configuring them as a consecutively numbered range. After configuring the range of LUs, you can modify the numbering of individual LUs in the range.  
  
### To configure a downstream connection  
  
1.  In the Host Integration Server console tree, expand **Servers**, expand the server you are working with.  
  
2.  Right-click **Connections**, point to **New**, and click either **802.2**, **SDLC**, or **X.25**.  
  
3.  Fill in the **Connection Properties** dialog box, type a name for the new downstream connection, select a link service, and type a comment.  
  
4.  Under **Remote End**, select **Downstream**.  
  
5.  Under **Allowed Directions**, select an option. For SDLC downstream connections, select **Outgoing Calls**.  
  
6.  If you selected **Outgoing Calls**, under **Activation**, select either **On Server Startup** or **By Administrator**.  
  
7.  Click the other tabs to specify other connection parameters between the downstream system and Host Integration Server. Click **OK** to exit.  
  
8.  On the **Action** menu, click **Save Configuration**.  
  
9. To put the configuration changes into effect, you must restart the server.  
  
> [!NOTE]
>  Restarting the server disconnects all users. Try to schedule configuration changes when they least affect users.  
  
> [!NOTE]
>  Two connections are needed for a downstream system: a downstream connection (from the downstream system to the computer running Host Integration Server) and an ordinary host connection (from the computer running SNA Server to the host).  
  
> [!NOTE]
>  Activation does not affect incoming calls. A connection that accepts incoming calls begins to listen for these calls when the server node is started.  
  
#### To assign a downstream LU to a host  
  
1.  Before you begin, verify that you have configured the host connection that the downstream LU will use.  
  
2.  Ensure that the server is inactive. If necessary, right-click the appropriate server node, and click **Stop**.  
  
3.  Double-click **SNA service**, and then double-click **Connections**.  
  
4.  Right-click the host connection to which you want to assign a downstream LU, point to **New**, and then click **Downstream LU**.  
  
5.  Enter the LU name. Click **OK** to exit.  
  
6.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  After you assign a new downstream LU to a host, you must also associate that LU with a downstream connection.  
  
> [!NOTE]
>  A downstream LU pool must contain LUs from a single server. Downstream LUs cannot access pooled downstream LUs from multiple servers.  
  
#### To view or modify a downstream LU  
  
1.  Right-click the LU whose properties you want to view, and click **Properties**.  
  
2.  In the **Properties** dialog box, do one of the following:  
  
    -   View the properties and click **Cancel**.  
  
    -   Modify the properties and click **OK**.  
  
3.  If you made changes, on the **Action** menu, click **Save Configuration**.  
  
4.  Stop and restart **SNA service**.  
  
#### To assign a downstream LU  
  
1.  In the Host Integration Server console tree, expand **Servers**, expand the server you are working with, and then click **Connections**.  
  
2.  Right-click the host connection to which you want to assign the downstream LU, point to **New**, and click **Downstream LU**.  
  
3.  Fill in the **Connection Properties** dialog box, and click **OK**.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
#### To associate a downstream LU with a downstream connection  
  
1.  Verify that the server is inactive. If necessary, right-click the service node and click **Stop**.  
  
2.  In the Host Integration Server console tree, select the downstream LUs from the host connection.  
  
     To select several adjacent items, click the first item you want, hold down SHIFT, and click the last item.  
  
     To select several nonadjacent items, hold down CTRL as you click the items that you want.  
  
3.  Drag the LUs from the host connection to the downstream connection.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
> [!IMPORTANT]
>  If a downstream system needs access to multiple LU sessions, assign one LU or LU pool for each session needed. You can assign a pool multiple times to the same downstream connection.  
  
> [!NOTE]
>  Before you can associate downstream LUs with a downstream connection, you must define the host connection, downstream connection, and the LUs.  
  
> [!NOTE]
>  Downstream LU pools must contain LUs from a single server. Downstream LUs cannot access pooled downstream LUs from multiple servers.  
  
## See Also  
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)