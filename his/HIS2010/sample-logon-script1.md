---
title: "Sample Logon Script1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6ac4cde-fd2d-4f8c-aae3-0e9e2956e6a1
caps.latest.revision: 3
---
# Sample Logon Script
```  
SETTIMEOUT 30,EXIT  
WAITSESSION SSCP  
WAIT 3  
SEND vm1@E  
WAITSESSION LULU  
WAIT 3  
SEND myuser@Tmypass@E  
WAIT 3  
SEND run myapp@E  
WAIT 3  
EXIT:  
```  
  
## See Also  
 [How to Record and Play Logon Scripts](../HIS2010/how-to-record-and-play-logon-scripts1.md)