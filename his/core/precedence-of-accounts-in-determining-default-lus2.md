---
title: "Precedence of Accounts in Determining Default LUs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61361beb-5d80-4cb4-be55-f2708422b2c9
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Precedence of Accounts in Determining Default LUs
When user and group account memberships overlap, the highest-priority account that contains a default local APPC LU determines that LU for the user, and the highest-priority account that contains a default remote APPC LU determines that LU for the user. Accounts are prioritized as follows:  
  
1. User accounts (highest priority)  
  
2. Subdomain groups  
  
3. Local groups  
  
4. Well-known groups such as Everyone (lowest priority)  
  
   For example, suppose a user account (a high-priority account) called JOHND contains LOCLU1 as the default local APPC LU, but no default remote APPC LU. At the same time, suppose a local group (a low-priority account) of which JOHND is a member contains LOCLU2 as the default local APPC LU, and REMLU2 as the default remote APPC LU. For JOHND, the high-priority assignment, a default local APPC LU of LOCLU1, will be combined with the only other available assignment, a default remote APPC LU of REMLU2.  
  
### To assign or edit CPI-C information  
  
1.  In the Host Integration Server console tree, click **CPI-C Symbolic Names**.  
  
2.  On the **Action** menu, point to **New**, and click **CPI-C Symbolic Name**.  
  
3.  Fill in the **Properties** dialog box, and click **OK**.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  If you are using applications based on Common Programming Interface for Communications (CPI-C), use this procedure to configure the CPI-C symbolic destination name.  
  
#### To configure the default display verb  
  
1.  In SNA Manager, select the subdomain that you want to configure.  
  
2.  On the **Action** menu, click **Properties**.  
  
3.  Click the **Display Verb** tab.  
  
4.  Select the default connection for the display verb, and click **OK**.  
  
5.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  When the display verb does not specify a connection, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses the connection that you specify in this procedure. If you do not specify a default display verbconnection, Host Integration Server randomly selects a connection for the verb to use.  
  
 Configuring hot backup involves setting up a system environment in which one resource can automatically fill in if another fails. In such a configuration, resources are interchangeable.  
  
#### To configure hot backup for 5250 LUs  
  
1.  Configure one connection to the AS/400 computer for each computer that runs Host Integration Server and supports the 5250 protocol.  
  
2.  Create a local LU on each server, specifying the following:  
  
    -   For **LU 6.2 Type**, select **Independent**.  
  
    -   For **LU Alias**, specify the same string on each server.  
  
    -   For **LU Name**, specify a unique string on each server. This is required to avoid device name conflicts across servers.  
  
3.  Create a remote LU on each server and give all the remote LUs the same LU name and alias, (which must match the Control Point Name of the AS/400 computer).  
  
     Be sure that the **Supports Parallel Sessions** box is selected for these LUs.  
  
4.  Make the local and remote LUs available to users and groups, by doing one of the following:  
  
    -   For each group or user that uses 5250, select the appropriate default local APPC LU and the appropriate default remote APPC LU.  
  
    -   To keep this process simple, use or create a group that includes all 5250 users, and assign the appropriate default LUs to that group.  
  
    -   For the 5250 emulator, have users specify the local and remote LUs when configuring a session on the emulator.  
  
> [!NOTE]
>  To achieve hot backup, Host Integration Server chooses a server to connect with the AS/400 computer based on availability. This distributes the load more evenly.  
  
> [!NOTE]
>  To configure hot backup for 5250 users, you must configure multiple servers and pairs of LUs that can all handle sessions to the intended AS/400 computer.  
  
> [!NOTE]
>  For better protection against failure, use multiple servers, and not multiple connections on the same server.  
  
#### To configure a server with multiple connections to the same AS/400 computer  
  
1.  In the Host Integration Server console tree, double-click **Connections**.  
  
2.  Click the first connection that you want to configure.  
  
3.  On the **Action** menu, click **Properties**.  
  
4.  Click the **System Identification** tab, and fill in the properties for the local and remote node.  
  
5.  Click **OK** to exit the dialog box.  
  
6.  Repeat steps 2 through 5 for each connection to the same AS/400 computer.  
  
7.  On the **Action** menu, click **Save Configuration**.  
  
8.  After you configure a connection, you must stop and restart the server.  
  
> [!IMPORTANT]
>  Each connection to the same AS/400 computer must use a separate link service.  
  
> [!NOTE]
>  This procedure makes the fully qualified network name unique for each connection.  
  
> [!NOTE]
>  The settings that you specify in this procedure override the fully qualified network name configured in the properties for the server.  
  
#### To configure a connection for dynamic definition of remote APPC LUs  
  
1.  Select the connection that you want to configure.  
  
2.  On the **Action** menu, click **Properties**.  
  
3.  On the **General** tab in the **Properties** dialog box, select **Supports Dynamic Remote APPC LU Definition**, and click **OK**.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
## See Also  
 [How to Configure APPC LUs for TPs or 5250 Emulation](../core/how-to-configure-appc-lus-for-tps-or-5250-emulation2.md)   
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)