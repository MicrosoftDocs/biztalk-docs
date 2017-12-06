---
title: "Total Number of Sessions | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0273cf83-6118-4f04-8971-7addaab9c614
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
ms.author: "paulettm"
---
# Total Number of Sessions
In general the independent and dependent sessions to an IBM Host must be hard coded.   With dependent sessions (3270 Display, Printer, or LUA) this is especially true, as each LU defined can only support one session.  In addition most customers still require a large number of dependent sessions.  The total number of sessions will need to taken into account when doing the capacity planning, as they will need to be explicitly configured on each server.  
  
 Each Host Integration Server can support a maximum of 60,000 dependent sessions.  Although one server can support this number, typically the sessions will be divided across multiple servers to provide fault tolerance.   Most customers will support a maximum of 7,000-10,000 Display or LUA sessions and 2000 Printer sessions per server.  
  
 Another factor is the number of unique users connecting to the server.  Each server can support 8,000 unique users.  Typically customers will run multiple sessions per desktop.  If the customer scenario is a 1:1 ratio, then the total number of sessions per server should be keep below 8,000.  
  
 An alternate strategy is to use LU Pools.  This allows the Display and LUA sessions to be grouped together under one name, referred to as a “Pool”.  From the user’s perspective the pool name is used instead of the LU name.  The server will provide them with the next available LU in the pool.   In scenarios where there is intermittent use of sessions, pooling can allow a smaller number of sessions to service a larger group of users.  For example there may be 10,000 users, but never more than 5,000 sessions in use at one time.  In this case a pool can be created with 5,000 sessions to accommodate the peak load.  This strategy works best when users and application are not tied to specific LUs.  
  
 Dependent LUs used for emulation of Printer session follow the same limits as Display & LUA sessions, but have additional constraints.  The operating system may limit the number of concurrently printing sessions.  On Windows 2008R2 & Windows 2012, Host Integration Server defaults to a limit of 500 concurrent sessions.  In addition, Printer sessions incur more overhead than Display or LUA session due to the interaction with the Windows Printing System.  Using multi-processor systems will increase concurrent printing performance.  Typically customers will support a maximum of 2000 configured sessions per server.  
  
 The following table provides some of the limitation for the components.  
  
|**Component**|**Maximum Values**|  
|-------------------|------------------------|  
|**HIS Connections**|-   1:1 mapping to a Host PU<br /><br /> -   255 Dependent LUs<br /><br /> -   250 Connections per SNA Service|  
|**SNA Service (Node)**|-   15,000 Dependent LUs<br /><br /> -   Four per Server|  
|**HIS Server**|-   60,000 Dependent LUs<br /><br /> -   1000 Connections<br /><br /> -   15 per Sub Domain|