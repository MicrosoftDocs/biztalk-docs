---
description: "Learn more about: SNAModemInitialize"
title: "SNAModemInitialize2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNAModemInitialize
The **SNAModemInitialize** function should be called once per link service process at initialization. This function initializes the communication path to the SNA Modem application. The ideal place to call this function is in the **SNALinkInitialize** function.  
  
## Syntax  
  
```  
  
void SNAModemInitialize();  
  
```  
  
## See Also  
 [SNALinkInitialize](../core/snalinkinitialize2.md)
