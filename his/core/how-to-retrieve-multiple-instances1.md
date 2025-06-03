---
description: "Learn more about: How to Retrieve Multiple Instances"
title: "How to Retrieve Multiple Instances1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Retrieve Multiple Instances
You can retrieve a local copy of the collection with a call to **ExecQuery**. After you have retrieved an instance, you can modify and update the instance. The following example shows how to retrieve a collection:  
  
```  
Set colItems = objWMIService.ExecQuery("Select * from MSSnaStatus_Connection")  
  
```
