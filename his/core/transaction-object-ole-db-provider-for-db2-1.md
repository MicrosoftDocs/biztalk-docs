---
title: "Transaction Object (OLE DB Provider for DB2)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54cbd428-4acd-4c0a-b751-6602cc4c5bb1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Object (OLE DB Provider for DB2)
The **Transaction** object is created by a **Session** object. The **Transaction** object is used to manage transactions on one or more **Rowset** objects.  
  
 The following interfaces of the **Transaction** object are supported by the current version of Microsoft OLE DB Provider for DB2:  
  
- **ISupportErrorInfo**  
  
- **ITransaction**  
  
  The current implementation of OLE DB Provider for DB2 services all OLE DB **Session**, **Command**, and **Rowset** objects present in a given instance of the **DataSource** object through a single Advanced Program-to-Program Communications (APPC) conversation or TCP/IP connection. One implication of this design is that if two **Rowset** objects, each created from a different OLE DB **Session** object, use explicit commitment control through the **ITransaction** interface, they will interfere with each other. When a **Commit** or **Abort** for one instance is invoked, all work for the **DataSource** object will be either committed or aborted. This may yield undesirable results. The work around to this problem is to instantiate two instances of the **DataSource** object.