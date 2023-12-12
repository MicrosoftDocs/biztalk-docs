---
description: "Learn more about: X.25 Connection Pointers"
title: "X.25 Connection Pointers2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# X.25 Connection Pointers
An X.25 connection uses a packet-switching network, and communicates through the Qualified Logical Link Control (QLLC) protocol. Connections are configured through SNA Manager. See [Make a connection](making-a-connection2.md) for guidance on configuring an X.25 connection. The following pointers indicate items that require special attention:  
  
-   As with all connections, the identifiers must be configured correctly. For details, see [Settings to Check for All Connection Types](../core/settings-to-check-for-all-connection-types2.md).  
  
-   Pay close attention to the **Remote X.25 Address** on the **Address** tab of the **Connection Properties** dialog box; it should match the address of the remote host, peer, or downstream system. The address consists of from 1 through 15 hexadecimal digits. If a 15-digit address is used, the final 3 digits are used for routing between stations with the same 12-digit address. For connections to a host using VTAM, the address should match the DIALNO parameter in the PORT definition. For connections to an IBM System i, the address should match the local address of the IBM System i (assigned by the X.25 carrier).  
  
-   Check the Max BTU Length setting, found in the **Connection Properties** dialog box. A BTU is a data-link information frame.  
  
-   Set the Max BTU Length so that it matches the capacity of the adapter and the host or downstream system. Otherwise, when the mainframe or IBM System i sends a logon screen, the BTU length (frame size) that is used will be unworkable, causing the connection to be dropped. The following table provides guidelines:  
  
    |For...|Set the Max BTU Length to...|  
    |------------|----------------------------------|  
    |IBM SDLC adapter|521 or less.|  
    |Connection to a mainframe|Equal to MAXDATA in the PU definition on the mainframe (recommended).|  
    |Connection to an IBM System i|Equal to MAXFRAME on the IBM System i (recommended).|  
    |Connection to a downstream system|Less than or equal to the maximum value supported by the downstream system.|  
  
-   Setting the Max BTU Length correctly is especially important for downstream connections.  
  
-   For SVC connections, check that the codes in **User Data** include C3, which specifies the QLLC protocol (the X.25 protocol used by SNA Manager). To view **User Data** codes, right-click the connection in the left pane, then click **Properties**, then click the **X.25** tab in the **Connection Properties** dialog box. For information about other user data codes, contact your X.25 network administrator.  
  
-   If each attempt at connection activation incurs cost as you access the X.25 network, you may want to limit the number of these attempts. To do this, double-click the connection, and then click the **X.25** tab. In the **Maximum Retries** list, select an appropriate maximum number of attempts. (The default is No Limit.)
