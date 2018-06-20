---
title: "ErrorObject Object (OLE DB Provider for DB2)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc0f12e5-cccb-417a-880e-59e167158559
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ErrorObject Object (OLE DB Provider for DB2)
The **ErrorObject** object is created by any interface on any DB2 OLE DB object. The **ErrorObject** object is used to retrieve additional information when an error occurs.  
  
 The following interface of the **ErrorObject** object is supported by the current version of Microsoft OLE DB Provider for DB2:  
  
- **IErrorRecords**  
  
  The **IErrorRecords** interface returns **ErrorRecord** objects with detailed information on the error that occurred.