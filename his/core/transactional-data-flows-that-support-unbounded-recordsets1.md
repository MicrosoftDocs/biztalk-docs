---
description: "Learn more about: Transactional Data Flows That Support Unbounded Recordsets"
title: "Transactional Data Flows That Support Unbounded Recordsets1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bb5fd7-e556-4b69-b40d-0224d03b2bc7
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Transactional Data Flows That Support Unbounded Recordsets
This model supports one or more consecutive sends followed by one or more consecutive receives. Therefore, the last input parameter and/or the return value of the method invocation can be an unbounded recordset (that is, a recordset with no set number of rows).  
  
 The CICS Link programming model cannot be used, so this data flow model supports only these two server models:  
  
-   CICS LU6.2 User Data  
  
-   IMS LU6.2  
  
## See Also  
 [Supported Data Flow Models](../core/supported-data-flow-models1.md)
