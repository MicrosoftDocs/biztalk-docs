---
title: "Client Cursor Engines | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 087d6cd3-c791-42ca-af53-347775207f39
caps.latest.revision: 4
---
# Client Cursor Engines
The Microsoft Data Access Components (MDAC) supports the option of a client cursor engine. This feature is implemented as part of OLE DB and ADO. When using ADO, a client cursor is enabled by setting the **CursorLocation** property on the recordset to **adUseClient**.  
  
 The OLE DB Provider for AS/400 and VSAM does not support any updating capabilities when used with a client cursor engine. If a client cursor engine is enabled using RDS or ADO, the OLE DB provider cannot be used to update data on the host. The ADO recordset is treated as if it were read-only.