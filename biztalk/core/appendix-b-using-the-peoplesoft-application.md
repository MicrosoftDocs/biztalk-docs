---
title: "Appendix B: Using the PeopleSoft Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PeopleSoft, using"
  - "using PeopleSoft application"
ms.assetid: 36475836-1d23-4bb4-a3c1-cdd3fff28476
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix B: Using the PeopleSoft Application
This section describes using different areas of PeopleSoft that could be useful in your orchestration testing.  
  
 When you use PeopleSoft for receive ports, you use PeopleTools to create an XML document. Nothing special is required to interact with PeopleSoft. For an event, you must be able to access to an **http\\\\:\<host>:\<port>** to listen for events from PeopleSoft. If a host and port is not available to you, you can set up a specific HTTP host and port by configuring the PeopleSoft Integration Broker.  
  
 To complete the testing of a PeopleSoft receive port, [Generating XML or Schema in PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md) discusses how to trigger a PeopleSoft event by changing something in a PeopleSoft environment. The change activates an XML file that is sent to the folder you set in the orchestration to be monitored.  
  
## In This Section  
  
-   [Generating XML or Schema in PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md)  
  
-   [Creating a PeopleSoft HTTP Host and Port](../core/creating-a-peoplesoft-http-host-and-port.md)