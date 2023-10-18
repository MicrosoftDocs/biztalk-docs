---
description: "Learn more about: SNAModemDeleteLink"
title: "SNAModemDeleteLink2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [MODEM_STATUS](../core/modem-status1.md)   
 [SNAModemAddLink](../core/snamodemaddlink1.md)
