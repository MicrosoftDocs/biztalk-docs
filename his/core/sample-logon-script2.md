---
description: "Learn more about: Sample Logon Script"
title: "Sample Logon Script2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [How to Record and Play Logon Scripts](../core/how-to-record-and-play-logon-scripts2.md)
