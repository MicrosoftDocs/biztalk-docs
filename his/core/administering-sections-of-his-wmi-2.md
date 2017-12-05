---
title: "Administering Sections of HIS (WMI)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c42b6e5-6e0f-47db-a3e5-921e18729a85
caps.latest.revision: 4
---
# Administering Sections of HIS (WMI)
[!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] is included with Windows Management Instrumentation (WMI) providers that grant administrative access to the following areas:  
  
-   Rolling out, configuring, and restoring services  
  
     The [SNA Provider WMI Programmer's Reference](../core/sna-provider-wmi-programmer-s-reference1.md) and [SNA Trace Provider WMI Programmer's Reference](../core/sna-trace-provider-wmi-programmer’s-reference2.md) providers expose information regarding the Setup and rollout procedures for [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. You can use instances of classes such as **MsSna_LinkService** to set up and administer link services, and the classes derived from **MsSna_Config** to configure your system. For more information, see [Configuring Host Integration Server with WMI](../core/configuring-host-integration-server-with-wmi1.md).  
  
-   Starting and stopping services and connections  
  
     The **WmiSna** provider exposes the **MsSna_Server**, **MsSna_Service**, and **MsSna_Connection** classes. These classes and their derived classes let you add an SNA service, start and stop services, pause services, and start and stop connections. For more information, see [Controlling Services and Connections with WMI](../core/controlling-services-and-connections-with-wmi2.md).  
  
-   Health monitoring  
  
     The **WmiSnaStatus** provider exposes information regarding the SNA service status. **WmiSnaStatus** uses a variety of classes derived from **MsSnaStatus_Event** to describe changes in different parts of your system. For more information, see [How to Monitor the Health of Host Integration Server with WMI](../core/how-to-monitor-the-health-of-host-integration-server-with-wmi2.md).  
  
-   Trace capturing  
  
     The **WmiSnaTrace** provider supports classes and instances derived from the **MsHisTrace_Config** class, which displays information regarding different configuration files. **WmiSnaTrace** also supports the **MsHisTrace_Event**, which describes an event that occurs whenever a trace is triggered. For more information, see [How to Capture a Trace with WMI](../core/how-to-capture-a-trace-with-wmi2.md).  
  
 Additionally, Microsoft Windows includes several standard WMI providers, such as a registry provider, for accessing information from the system registry. Windows also supplies a Windows Event Log provider that enables applications to receive notifications of Windows and [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] events and to access the information stored in the Windows event log. Third-party vendors can create custom providers to interact with managed objects specific to their environment.