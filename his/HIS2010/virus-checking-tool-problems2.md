---
title: "Virus-Checking Tool Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 089c1ce3-f1cb-4ea6-963b-f9bcf4848318
caps.latest.revision: 4
---
# Virus-Checking Tool Problems
When you are running [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] with some independent software vendor virus checking tools, SNA link services might fail to start due to the following error:  
  
 Event 128: "Can't load IHV DLL xxx.dll"  
  
 where xxx.dll is the specific DLL  
  
 It is recommended that any "real-time scanning" options be disabled on the virus checker before starting Host Integration Server to prevent local file access slowdowns.