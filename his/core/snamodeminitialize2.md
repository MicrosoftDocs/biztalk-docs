---
description: "Learn more about: SNAModemInitialize"
title: "SNAModemInitialize2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03127fd0-8be4-4051-a8a3-eab84c7c3257
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SNAModemInitialize
The **SNAModemInitialize** function should be called once per link service process at initialization. This function initializes the communication path to the SNA Modem application. The ideal place to call this function is in the **SNALinkInitialize** function.  
  
## Syntax  
  
```  
  
void SNAModemInitialize();  
  
```  
  
## See Also  
 [SNALinkInitialize](../core/snalinkinitialize2.md)
