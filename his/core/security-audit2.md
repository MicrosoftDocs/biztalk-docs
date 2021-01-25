---
description: "Learn more about: Security Audit"
title: "Security Audit2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98db21b1-8ec8-4b11-97cd-c2dfd1deba23
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Security Audit
When you set up security auditing, you specify events for which the system will create event log entries.  
  
 You can monitor system events using the Host Integration Server SNA Manager. When you configure the properties, you can view a detailed problem analysis, significant system events or general information messages, or you can disable audit logging.  
  
 You can cause the system to create an entry every time a member of the Administrators group changes the configuration file. The entry would include the time, the user and process IDs, and other information.  
  
 When you set up auditing with Host Integration Server, you are able to record not only access to the configuration file, but the running of Host Integration Server processes. However, using a file system other than NTFS limits the possibilities for auditing, just as it limits the possibilities for setting permissions. When Host Integration Server is not installed on NTFS, the only event that will actually result in log entries is the starting of the Host Integration Server SNA Manager. However, auditing information for this event is useful, if limited.  
  
 Auditing is an important way of collecting security-related information. However, there is a small performance overhead for each audit check the system performs. In addition, if you record a wide variety of events, the event log can grow very quickly. For these reasons, you may want to be selective when specifying events to be audited. You may want to focus on such events as Read Domain (Success), Write Domain (Success), and Manage Domain (Success). This list of events is a suggestion only. All the events offered for auditing through Host Integration Server can be useful, depending on the situation.  
  
 Among the events recorded when you enable auditing are the actions of Host Integration Server itself. For more information about event logs, the Event Viewer, and strategies for auditing, see your Windows documentation.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)
