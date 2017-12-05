---
title: "How to Retrieve an Instance2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27254104-e11e-4089-9f39-18fad450e799
caps.latest.revision: 3
---
# How to Retrieve an Instance
You can retrieve a local copy of the instance with a call to **GetObject** with the object path of the instance. The following example shows how to retrieve an IPDLC connection using WMI:  
  
```  
Set ObjClass = Namespace.Get("MsSna_ConnectionIpDlc")  
  
```  
  
 Besides retrieving a single instance, you can also retrieve collections of WMI instances by querying the WMI database with a **SELECT** statement.