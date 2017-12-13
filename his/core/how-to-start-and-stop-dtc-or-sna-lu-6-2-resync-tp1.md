---
title: "How to Start and Stop DTC or SNA LU 6.2 Resync TP1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c35f1acd-d987-4fd6-b6e5-bc34f568c29e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start and Stop DTC or SNA LU 6.2 Resync TP
If necessary, you can manually stop and start the Microsoft Distributed Transaction Coordinator (DTC) and/or the SNA LU 6.2 Resync TP services by clicking **Services** in the **Administrative Tools** menu in Windows.  
  
 Use the following procedures to start or stop services in Windows. It is important to start and stop the services in the precise order given.  
  
### To stop DTC or SNA LU 6.2 Resync TP in Windows  
  
1.  Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Services**.  
  
2.  Right-click **SNA LU 6.2 Resync TP**, and then click **Stop**. If prompted, click **Yes**.  
  
3.  Right-click **SnaBase**, and then click **Stop**. If prompted, click **Yes**.  
  
4.  Right-click **DTC**, and then click **Stop**. If prompted, click **Yes**.  
  
### To start DTC or SNA LU 6.2 Resync TP in Windows  
  
1.  Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Services**.  
  
2.  Right-click **DTC**, and then click **Start**.  
  
3.  Right-click **SnaBase**, and then click **Start**.  
  
4.  Right-click **SNA LU 6.2 Resync TP**, and then click **Start**.