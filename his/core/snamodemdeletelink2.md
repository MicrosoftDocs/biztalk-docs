---
description: "Learn more about: SNAModemDeleteLink"
title: "SNAModemDeleteLink2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 225b2398-93ff-4893-b391-227f75804174
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
