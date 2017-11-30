---
title: "Initialization2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00f05d84-c6da-4945-9e04-4d5c26bb7cc1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Initialization
The 3270 emulator should initialize the DL-BASE and then call the Dynamic Access Module (DMOD) to obtain the necessary configuration information. This also registers the user name with the DMOD. It can then obtain further system information such as the Host Integration Server version number, if required.  
  
 The following table lists the functions involved with this process.  
  
|Function|Description|  
|--------------|-----------------|  
|[sbpuinit](../HIS2010/sbpuinit2.md)|Initializes the DL-BASE.|  
|[sepdcrec](../HIS2010/sepdcrec2.md)|Gets configuration information.|  
|[sepdgetinfo](../HIS2010/sepdgetinfo1.md)|Gets system information.|  
  
 The **sbpuinit** entry point should always be called before any other DL-BASE/DMOD entry points except [SNAGetVersion](../HIS2010/snagetversion2.md). For new emulators, **sepdcrec** should be called after **sbpuinit**. (Because of the order of calls used in older emulators, a call to **sepdcrec** before **sbpuinit** is still supported, but this order is not recommended.)