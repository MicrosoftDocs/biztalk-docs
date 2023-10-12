---
description: "Learn more about: SNAModemTerminate"
title: "SNAModemTerminate1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNAModemTerminate
The **SNAModemTerminate** function should be called once per link service process, at termination. The ideal place is **SNALinkTerminate**. If the link service supports a single link, it is appropriate to call **SNAModemDeleteLink** immediately before **SNAModemTerminate**. Otherwise it is better to call **SNAModemDeleteLink** as each link instance is terminated.  
  
## Syntax  
  
```  
  
void SNAModemTerminate();  
  
```  
  
## See Also  
 [SNALinkTerminate](../core/snalinkterminate1.md)   
 [SNAModemDeleteLink](../core/snamodemdeletelink2.md)
