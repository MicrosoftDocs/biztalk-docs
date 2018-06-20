---
title: "Manage adapter versioning with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb596fdd-251c-4978-9f33-cf2883d281d8
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage adapter versioning with the WCF LOB Adapter SDK
After initial deployment of adapters and potentially several times during their lifetime, adapters (and the endpoints they expose) may need to be changed for a variety of reasons. These reasons include changing business needs, information technology requirements, or issues with the line of business system or the adapter itself. This topic discusses different strategies for handling versioning for adapters that are written using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].  
  
## Versioning and Windows Communication Foundation  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is built upon  [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] and relies on its infrastructure for exchanging messages between systems. Using mechanisms that  [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] exposes, you can version both services and data contracts. For more information, including best practices for service versioning, see [Service Versioning](http://go.microsoft.com/fwlink/?LinkId=85497) in the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] online reference. For more information, including best practices for data contract versioning, see [Data Contract Versioning](http://go.microsoft.com/fwlink/?LinkId=120177) in the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] online reference.  
  
## Versioning Scenarios  
 There are two primary versioning scenarios:  
  
- One adapter version supports multiple versions of the target system.  
  
- Two or more adapter versions support the same system or two or more different systems.  
  
  You may also need to release a new version of your adapter if updates to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] affect existing functionality.  
  
  Each of these scenarios requires a different versioning strategy.  
  
> [!NOTE]
>  The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not enforce any specific versioning scenarios. It is left to the developer to determine versioning requirements for an adapter.  
  
### One adapter supports multiple versions of target system  
 When the adapter supports multiple versions of the target system, you should expose one or more binding properties that can be used to identify the desired version. For example, an adapter might support multiple communication libraries supplied by the target system's vendor. Using a custom binding property named "LibraryVersion," the adapter consumer could choose which library to use based on the deployment environment or other requirements.  
  
### Two or more adapters support one version of target system  
 In this case, each adapter should use a unique scheme (ContosoV1:// and ContosoV2://) and a unique binding name (ContosoV1Binding and ContosoV2Binding). Vendors should consider using their name in the scheme and binding name as well (for example, Microsoft.ContosoV1:// and Microsoft.ContosoV1Binding).  
  
### New versions of the WCF LOB Adapter SDK  
 When new versions of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are released, you will be able to install the new version without having to recompile your adapter, since [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] releases are be backward-compatible. However, you should evaluate new releases to determine if there is a change in functionality that your adapter depends on, or if there is new functionality that your adapter would benefit from implementing.  
  
## See Also  
 [Development best practices using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)