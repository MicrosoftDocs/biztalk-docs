---
title: "Session Integrator Programming Interfaces1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e5f1bf5-c78e-445c-a544-9b7633961689
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Session Integrator Programming Interfaces
Session Integrator provides a COM and a .NET Framework interface to grant programmatic access to an SNA network using LU0 and LU2 protocols. The following tables describe the relationships between the COM and the .NET Framework interfaces.  
  
## LU0 Interfaces  
  
|COM|.NET|Description|  
|---------|----------|-----------------|  
|[IcomLU0](../HIS2010/icomlu0-interface1.md)|<xref:Microsoft.HostIntegration.SNA.Session.SessionLU0>|The primary interface for connecting, sending, and receiving information over an LU0 session.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0>|Represents the LU0 connection.<br /><br /> `SessionLU0` uses `SessionConnectionLU0` to contain the relevant connection and initialization information.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionLU0Data>|Encapsulates the information you want to send and receive over LU0.<br /><br /> `SessionLU0` uses `SessionLU0Data` in the `Send` and `Receive` methods to send and receive data.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionLU0InitType>|Contains initialization information.<br /><br /> `SessionLU0` uses this class during the initialization process to pass initialization information to the host.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionLU0ReceiveIndication>|Represents the current state of a session associated with a receive call.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionLU0SendIndication>|Contains values used by the `Send` method of `SessionLU0`.|  
  
## LU2 Interfaces  
  
|COM|.NET|Description|  
|---------|----------|-----------------|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay>|Provides the connection interface for the `SessionDisplay` class.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenPosition>|Provides access to a position on the LU2 screen.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenCursor>|Provides access to the cursor on the screen.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenPartialField>|Provides access to a part of a screen field.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenField>|Provides access to a particular area of the LU2 screen including the data and attributes.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenFieldCollection>|Contains a collection of `ScreenField` classes.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenPartialFieldCollection>|Contains a collection of `ScreenPartialFields` classes.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenFieldAttributeData>|Provides all of the attributes about the `ScreenField` data.|  
|[Icom3270](../HIS2010/icom3270-interface2.md)|<xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay>|Primary interface for accessing the network over a 3270 connection.|  
||<xref:Microsoft.HostIntegration.SNA.Session.ScreenData>|Provides access to a particular area of the raw 3270 data representations.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionDisplayScript>|Enables users to take a script created in the Host Integration Server 3270 client and play it programmatically.|  
||<xref:Microsoft.HostIntegration.SNA.Session.SessionDisplayVariableCollection>|Used with the `SessionDisplayScript` class to provide variables that can be replaced in the script.|  
  
## See Also  
 [Session Integrator](../core/session-integrator2.md)   
 [Working with Session Integrator](../core/working-with-session-integrator1.md)