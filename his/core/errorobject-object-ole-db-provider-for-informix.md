---
title: "ErrorObject Object (OLE DB Provider for Informix) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e372167-698b-4340-b475-c282e41d1f37
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ErrorObject Object (OLE DB Provider for Informix)
The **ErrorObject** object is created by any interface on any Informix OLE DB object. The **ErrorObject** object is used to retrieve additional information when an error occurs.  
  
 The following interface of the **ErrorObject** object is supported by the current version of Microsoft OLE DB Provider for Informix:  
  
- **IErrorRecords**  
  
  The **IErrorRecords** interface returns **ErrorRecord** objects with detailed information on the error that occurred.