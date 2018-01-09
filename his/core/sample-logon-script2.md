---
title: "Sample Logon Script2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5dfe5f32-1459-4b8f-8ef0-f21b26f49249
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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