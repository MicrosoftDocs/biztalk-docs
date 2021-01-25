---
description: "Learn more about: Using LoadGen 2007 with MSMQ"
title: "Using LoadGen 2007 with MSMQ | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8f23a86-0e6d-478a-87a3-5b02338c9afb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using LoadGen 2007 with MSMQ
The Load Generation tool, Loadgen, enables you to simulate heavy loads on a BizTalk Server system.

> [!NOTE]
>  The LoadGen 2007 tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](https://go.microsoft.com/fwlink/?LinkId=59841).

 Using LoadGen with MSMQ is supported, but we do not auto-register the MSMQ COM components during installation since the MSMQ runtime service may not be installed on your computer.

 To use MSMQ and LoadGen, manually register the MSMQTransmitter.dll and ComMsmqMonitor.dll files located in the bins directory:

```
regsvr32 MSMQTransmitter.dll
```

 If you do not register the MSMQ COM components, you will receive the following runtime errors:

```
Cannot Load Transport DLL C:\Program Files\LoadGen\Bins\MSMQTransport.dll for Section MSMQRxQTxn
Exception has been thrown by the target of an invocation.
```

## See Also
 [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md)
