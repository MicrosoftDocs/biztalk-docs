---
title: "Deleting Link Services1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e531b3b-ba52-4123-9141-474379e3a0bb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Deleting Link Services
As with other link services, you can delete an IP-DLC link service in the MMC snap-in.  
  
> [!NOTE]
>  When you delete a link service, all related connections will no longer be associated with any link service. A user might associate such a connection with any other IP-DLC link service that is associated with the node. Deleting a node associated with a link service will break association between these items.  
  
### To delete a link service  
  
1. In the scope pane of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] MMC snap-in, locate the computer with the link services that you want to delete.  
  
2. Expand the list for that computer.  
  
3. Right-click the appropriate link service, and then click **Delete**.  
  
## See Also  
 [Managing IP-DLC Link Services](../core/managing-ip-dlc-link-services2.md)