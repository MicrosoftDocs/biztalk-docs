---
title: "ErrorObject Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6123efe1-a60c-43e3-9c9a-b4c541a59ebc
caps.latest.revision: 3
---
# ErrorObject Object (OLE DB Provider for AS-400 and VSAM)
The **ErrorObject** object is created by any interface on any SNA OLE DB object. The **ErrorObject** object is used to retrieve additional information when an error occurs.  
  
 The following interface of the **ErrorObject** object is supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM:  
  
-   **IErrorRecords**  
  
 The **IErrorRecords** interface returns **ErrorRecord** objects with detailed information about the error that occurred.