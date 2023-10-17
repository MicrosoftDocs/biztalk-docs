---
description: "Learn more about: SNAModemTerminate"
title: "SNAModemTerminate1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa4659ae-9379-4427-a53b-c32f00b68db9
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
