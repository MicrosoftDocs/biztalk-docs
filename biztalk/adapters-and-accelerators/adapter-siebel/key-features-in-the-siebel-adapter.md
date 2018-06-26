---
title: "Key features in the Siebel Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "features, performance-related"
  - "adapter features, new"
  - "features, technology-related"
  - "features, metadata-related"
  - "adapter features, operations-related"
  - "adapter features, performance-related"
  - "features, new"
  - "features, operations-related"
  - "adapter features, metadata-related"
ms.assetid: 4612c9ab-810e-4c69-9168-a25c58682e71
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Key features in the Siebel Adapter
This section lists the new features in [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
> [!NOTE]
>  This topic has been used from the previous version of [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] Help.  
  
## New Features in the Siebel Adapter  
 The following are the new features introduced in this release of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
### Technology-Related Features  
  
|                                                                    Feature                                                                     |                                                                                                               Comment                                                                                                               |
|------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Support for using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server (MOSS) | You can use the adapters to present data from the Siebel system onto a MOSS portal. For more information, see [Using the Siebel Adapter with Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx). |
  
### Operations-Related Features  
  
|Feature|Comment|  
|-------------|-------------|  
|Support for ASSOCIATE operation on business components|Adapter clients can associate records by specifying search expressions for parent and child records. This is applicable only for business components with multivalued group (MVG) fields. Note that the search expressions should filter exactly one record for both the parent and child business components.|  
|Support for DISASSOCIATE operation on business components|Adapter clients can dissociate records by specifying search expressions for parent and child records. This is applicable only for business components with multivalued group (MVG) fields. Note that the search expressions must filter exactly one record for both the parent and child business components.|  
|Support for multivalue link queries|Adapter clients can query the child records associated with a parent record by specifying the parent record and the multivalued field name. This is applicable only for business components with multivalued group (MVG) fields.|  
  
### Other Features  
  
|                                                        Feature                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| New way of using the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] | The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-Siebel port. If you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default. However, if you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Siebel port, you must first add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For more information, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md). |
  
## See Also  
 [Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)