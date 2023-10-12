---
description: "Learn more about: How to Retrieve an Instance"
title: "How to Retrieve an Instance1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Retrieve an Instance
You can retrieve a local copy of the instance with a call to **GetObject** with the object path of the instance. The following example shows how to retrieve an IPDLC connection using WMI:  
  
```  
Set ObjClass = Namespace.Get("MsSna_ConnectionIpDlc")  
  
```  
  
 Besides retrieving a single instance, you can also retrieve collections of WMI instances by querying the WMI database with a **SELECT** statement.
