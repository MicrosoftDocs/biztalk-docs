---
title: "SNAModemTerminate2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fcad57e-faac-477c-9f3f-07142e1e1bed
caps.latest.revision: 3
---
# SNAModemTerminate
The **SNAModemTerminate** function should be called once per link service process, at termination. The ideal place is **SNALinkTerminate**. If the link service supports a single link, it is appropriate to call **SNAModemDeleteLink** immediately before **SNAModemTerminate**. Otherwise it is better to call **SNAModemDeleteLink** as each link instance is terminated.  
  
## Syntax  
  
```  
  
void SNAModemTerminate();  
  
```  
  
## See Also  
 [SNALinkTerminate](../HIS2010/snalinkterminate2.md)   
 [SNAModemDeleteLink](../HIS2010/snamodemdeletelink1.md)