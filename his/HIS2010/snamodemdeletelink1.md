---
title: "SNAModemDeleteLink1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9655dcac-213f-4b87-a62a-655a28c3ef58
caps.latest.revision: 3
---
# SNAModemDeleteLink
The **SNAModemDeleteLink** function should be called when a link is terminating to delete the resources associated with the link. The parameters passed in must correspond to those returned by a call to **SNAModemAddLink**.  
  
## Syntax  
  
```  
  
            void SNAModemDeleteLink(   
MODEM_STATUS *pModemStatus);  
```  
  
#### Parameters  
 *pModemStatus*  
 A pointer to a **MODEM_STATUS** structure that was passed to the **SNAModemAddLink** function used for storing modem status interface.  
  
## Remarks  
 All resources in the link service associated with the modem status are deleted, and they must not be accessed by the IHV code after calling this function.  
  
## See Also  
 [MODEM_STATUS](../HIS2010/modem-status2.md)   
 [SNAModemAddLink](../HIS2010/snamodemaddlink2.md)