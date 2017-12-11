---
title: "View Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3107d2d9-8cad-46ab-9422-eb358ac721d6
caps.latest.revision: 3
---
# View Object (OLE DB Provider for AS-400 and VSAM)
The **View** object is created on a **Rowset** object. The **View** object is used to expose simple operations, such as sorting and filtering a rowset by applying a view. Views can be applied when opening a **Rowset** object or applied to an existing **Rowset** object.  
  
 The following interfaces of the **View** object are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM when applied to AS/400 keyed physical files, AS/400 logical files, VSAM KSDS files with unique keys, and VSAM RRDS files with unique keys:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **ISupportErrorInfo**  
  
-   **IViewChapter**  
  
-   **IViewFilter**  
  
-   **IViewRowset**  
  
-   **IViewSort**