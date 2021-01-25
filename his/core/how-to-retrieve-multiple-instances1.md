---
description: "Learn more about: How to Retrieve Multiple Instances"
title: "How to Retrieve Multiple Instances1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2026178-2cab-497d-94de-098ed1be9428
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Retrieve Multiple Instances
You can retrieve a local copy of the collection with a call to **ExecQuery**. After you have retrieved an instance, you can modify and update the instance. The following example shows how to retrieve a collection:  
  
```  
Set colItems = objWMIService.ExecQuery("Select * from MSSnaStatus_Connection")  
  
```
