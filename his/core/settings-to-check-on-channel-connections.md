---
title: "Settings to Check on Channel Connections2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be7e7258-cf1c-4ee7-8f56-6bd37749d7b2
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Settings to Check on Channel Connections
The number of parameters involved in channel connections is fewer than with other types of connections. The key parameters to note are those specifying addresses and, for channel connections, the Max BTU Length.  
  
 If one or more 3270 LUs never becomes active, even when users are attempting to start sessions, the LOCADDR settings in the LU definitions in VTAM or NCP may not match the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] LU numbers, or some or all of the LUs may be inactivated in VTAM or NCP. To correct this, consult with the administrator of the host system.