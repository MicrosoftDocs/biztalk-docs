---
description: "Learn more about: Modem API Summary"
title: "Modem API Summary2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13f42b3b-9ced-42b8-be10-b52b8d949b06
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Modem API Summary
To simplify the task for independent hardware vendors (IHVs) who want to use this feature, four new entry points have been added to SNALINK.DLL. An IHV who uses these must be linking with IHVLINK.LIB, a stub library that contains the exports library for SNALINK.DLL. This API enables the IHV to simply maintain the contents of a [MODEM_STATUS](./modem-status1.md) structure. The underlying SNALINK library code handles the communication of this information to the modem lights application.  
  
 The modem status functions are as follows.  
  
|Function|Description|  
|--------------|-----------------|  
|[SNAModemInitialize](./snamodeminitialize2.md)|Initializes the communication path to the SNA Modem application.|  
|[SNAModemAddLink](./snamodemaddlink1.md)|Adds an SNA link.|  
|[SNAModemDeleteLink](./snamodemdeletelink2.md)|Deletes the resources associated with a link.|  
|[SNAModemTerminate](./snamodemterminate1.md)|Terminates an SNA link.|
