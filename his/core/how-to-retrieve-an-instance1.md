---
title: "How to Retrieve an Instance1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5c3329b-2801-4710-92af-03124c93e931
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Retrieve an Instance
You can retrieve a local copy of the instance with a call to **GetObject** with the object path of the instance. The following example shows how to retrieve an IPDLC connection using WMI:  
  
```  
Set ObjClass = Namespace.Get("MsSna_ConnectionIpDlc")  
  
```  
  
 Besides retrieving a single instance, you can also retrieve collections of WMI instances by querying the WMI database with a **SELECT** statement.