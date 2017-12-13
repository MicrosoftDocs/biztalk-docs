---
title: "SNAModemAddLink1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e999f91-c53b-4be0-a2fc-c1e9353a72c8
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNAModemAddLink
The **SNAModemAddLink** function should be called once per link initialization. For link services that support more than a single SNA link, this call can be made multiple times. For link services that support only a single link, this call can be made immediately after **SNAModemInitialize**; otherwise it is preferable to call **SNAModemAddLink** as each port is initialized.  
  
## Syntax  
  
```  
  
            void SNAModemAddLink(   
MODEM_STATUS **ppModemStatus);  
```  
  
#### Parameters  
 *ppModemStatus*  
 The address of a pointer to a **MODEM_STATUS** structure that will be used for storing modem status information. The returned **MODEM_STATUS** structure will contain a link service name.  
  
## Remarks  
  
> [!NOTE]
>  The IHV should declare a pointer to a **MODEM_STATUS** structure and pass its address to **SNAModemAddLink**.  
  
> [!NOTE]
>  The **LSName** is initially the name of the link service, but may need to be altered for multiport link services.The IHV can replace the link service name returned in the **MODEM_STATUS** structure to differentiate between possible multiple connections through a single link service.  
  
> [!NOTE]
>  The IHV should maintain the various input and output signal lines and the data flow frame counts in the returned **MODEM_STATUS** structure. The Microsoft [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Modem Monitor application will periodically read and display the data stored in this **MODEM_STATUS** structure.  
  
> [!NOTE]
>  Internally **SNAModemAddLink** increments the usage count of the shared memory, and signals the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Modem Monitor application that a new link has been added.  
  
## See Also  
 [MODEM_STATUS](../core/modem-status1.md)   
 [SNAModemInitialize](../core/snamodeminitialize2.md)