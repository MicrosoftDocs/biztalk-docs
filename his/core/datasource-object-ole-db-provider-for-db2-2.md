---
title: "DataSource Object (OLE DB Provider for DB2)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 433d22ee-6632-438f-bd11-aac8240c9740
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DataSource Object (OLE DB Provider for DB2)
The **DataSource** object is created by an OLE DB consumer. The **DataSource** object contains the knowledge and ability to connect to DB2 over Advanced Program-to-Program Communications (APPC) and LU 6.2 (through [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]) or over TCP/IP. The **DataSource** object is used to create one or more **Session** objects.  
  
 The following interfaces of the **DataSource** object are supported by the current version of Microsoft OLE DB Provider for DB2:  
  
-   **IDBCreateSession**  
  
-   **IDBInfo**  
  
-   **IDBInitialize**  
  
-   **IDBProperties**  
  
-   **IPersist**  
  
-   **IPersistFile**  
  
-   **ISupportErrorInfo**