---
title: "OLE DB Data Source Property Support in the OLE DB Provider for DB22 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14422717-3031-4ddf-8e8c-34df0ce80a83
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# OLE DB Data Source Property Support in the OLE DB Provider for DB2
The following table summarizes the standard OLE DB version 2.0 data source properties from the DBPROP_DATASOURCE property set that are supported by the version of Microsoft OLE DB Provider for DB2 included with [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
|OLE DB Property ID|Comments|  
|------------------------|--------------|  
|DBPROP_CURRENTCATALOG|The name of the current catalog. This property is derived from the *Initial Catalog* parameter when configuring data sources. An application can use the CATALOGS schema rowset to enumerate catalogs.<br /><br /> This VT_BSTR type property defaults to the value configured in the data source for *Initial Catalog*.|