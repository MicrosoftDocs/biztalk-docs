---
title: "How to Retrieve Multiple Instances2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54fc854d-b4c0-43dc-928f-7414f965997d
caps.latest.revision: 3
---
# How to Retrieve Multiple Instances
You can retrieve a local copy of the collection with a call to **ExecQuery**. After you have retrieved an instance, you can modify and update the instance. The following example shows how to retrieve a collection:  
  
```  
Set colItems = objWMIService.ExecQuery("Select * from MSSnaStatus_Connection")  
  
```