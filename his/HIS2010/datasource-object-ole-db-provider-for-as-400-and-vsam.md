---
title: "DataSource Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a0bcda4-cbf5-4384-b90f-88ddf239e262
caps.latest.revision: 3
---
# DataSource Object (OLE DB Provider for AS-400 and VSAM)
The **DataSource** object is created by an OLE DB consumer. The **DataSource** object contains the knowledge and ability to connect to an IBM mainframe or AS/400 computer over Advanced Program-to-Program Communications (APPC) and LU 6.2 (through Microsoft [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]) or over TCP/IP. The **DataSource** object is used to create one or more **Session** objects.  
  
 The following interfaces of the **DataSource** object are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM:  
  
-   **IDBCreateSession**  
  
-   **IDBInitialize**  
  
-   **IDBProperties**  
  
-   **IPersist**  
  
-   **IPersistFile**  
  
-   **ISupportErrorInfo**