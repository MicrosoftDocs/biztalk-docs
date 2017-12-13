---
title: "WMI and the Host Integration Server Architecture1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0cc0be3-9f29-4734-abff-23825b4ba0fc
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WMI and the Host Integration Server Architecture
The architecture of the Windows Management Instrumentation (WMI) technology includes management applications, managed objects, providers, and the management infrastructure.  
  
## Management Applications  
 A management application is a Microsoft Windows-based application or service that processes or displays data from a managed object. A management application can perform a variety of tasks in a Host Integration Server  environment, such as configuring servers that are running Host Integration Server, measuring performance, reporting outages, and correlating data. The management application is what you will probably be creating using this programmer's guide.  
  
## Managed Objects  
 A managed object represents a logical or physical enterprise component. A managed object is modeled in WMI using the Common Information Model (CIM), and is accessed by a management application through the WMI programming interface. A managed object in the Host Integration Server environment can be any component of the system, from a link service device driver communicating with hardware to software configuration information about users and connected logical units (LU).  
  
## WMI Providers  
 A WMI provider is a COM object that exposes an interface to a managed object. The WMI providers supplied with Host Integration Server  use the WMI COM API to supply the WMI repository with data from Host Integration Server managed objects, to handle requests on behalf of Host Integration Server management applications, and to generate notifications of events.  
  
## Management Infrastructure  
 The management infrastructure is made up of WMI and the CIM repository. WMI lets users handle communications between management applications and providers. Users store their static data in the CIM repository. Applications and providers communicate through WMI using a common application programming interface (COM API). The COM API, which supplies event notification and query processing services, is available in the C and C++ programming languages.  
  
 The CIM repository holds static management data. Static data is data that does not regularly change. WMI also supports dynamic data, which is data that must be generated on demand because it changes frequently. Data can be placed in the CIM repository by WMI or network administrators. Information can be placed in the CIM repository using either the managed object format (MOF) language and the MOF Compiler or the WMI COM APIs. The WMI providers supplied with Host Integration Server  use both mechanisms.  
  
 Management applications can access the COM API directly to interact with WMI and the CIM repository to make management requests of Host Integration Server. Applications can also use other access methods, such as HTML to make these requests. The protocol used for communication between local and remote components is Distributed Component Object Model (DCOM).  
  
## See Also  
 [WMI and Host Integration Server](../core/wmi-and-host-integration-server1.md)