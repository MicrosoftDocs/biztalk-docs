---
title: "Rowset Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc18055b-bc66-41ef-8235-1968941e5955
caps.latest.revision: 3
---
# Rowset Object (OLE DB Provider for AS-400 and VSAM)
**Rowset** objects are created by **Session** objects. The **Rowset** object exposes data in tabular format.  
  
 The following interfaces of the **Rowset** object are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM:  
  
-   **IAccessor**  
  
-   **IChapteredRowset**  
  
-   **IColumnsInfo**  
  
-   **IConvertType**  
  
-   **IRowset**  
  
-   **IRowsetChange**  
  
-   **IRowsetFind**  
  
-   **IRowsetIdentity**  
  
-   **IRowsetIndex**  
  
-   **IRowsetInfo**  
  
-   **IRowsetLocate**  
  
-   **IRowsetRefresh**  
  
-   **IRowsetUpdate**  
  
-   **IRowsetView**  
  
-   **ISupportErrorInfo**  
  
> [!NOTE]
>  The **IRowsetFind** interface is only supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM when applied to AS/400 keyed physical files, AS/400 logical files, VSAM KSDS files with unique keys, and VSAM RRDS files with unique keys.