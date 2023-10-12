---
description: "Learn more about: Transaction Object (OLE DB Provider for Informix)"
title: "Transaction Object (OLE DB Provider for Informix)"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transaction Object (OLE DB Provider for Informix)
The **Transaction** object is created by a **Session** object. The **Transaction** object is used to manage transactions on one or more **Rowset** objects.  
  
 The following interfaces of the **Transaction** object are supported by the current version of Microsoft OLE DB Provider for Informix:  
  
- **ISupportErrorInfo**  
  
- **ITransaction**  
  
  The current implementation of OLE DB Provider for Informix services all OLE DB **Session**, **Command**, and **Rowset** objects present in a given instance of the **DataSource** object through a single TCP/IP connection. One implication of this design is that if two **Rowset** objects, each created from a different OLE DB **Session** object, use explicit commitment control through the **ITransaction** interface, they will interfere with each other. When a **Commit** or **Abort** for one instance is invoked, all work for the **DataSource** object will be either committed or aborted. This may yield undesirable results. The work around to this problem is to instantiate two instances of the **DataSource** object.
