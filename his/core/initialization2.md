---
description: "Learn more about: Initialization"
title: "Initialization2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Initialization
The 3270 emulator should initialize the DL-BASE and then call the Dynamic Access Module (DMOD) to obtain the necessary configuration information. This also registers the user name with the DMOD. It can then obtain further system information such as the Host Integration Server version number, if required.  
  
 The following table lists the functions involved with this process.  
  
|Function|Description|  
|--------------|-----------------|  
|[sbpuinit](./sbpuinit1.md)|Initializes the DL-BASE.|  
|[sepdcrec](./sepdcrec1.md)|Gets configuration information.|  
|[sepdgetinfo](./sepdgetinfo2.md)|Gets system information.|  
  
 The **sbpuinit** entry point should always be called before any other DL-BASE/DMOD entry points except [SNAGetVersion](./snagetversion1.md). For new emulators, **sepdcrec** should be called after **sbpuinit**. (Because of the order of calls used in older emulators, a call to **sepdcrec** before **sbpuinit** is still supported, but this order is not recommended.)
