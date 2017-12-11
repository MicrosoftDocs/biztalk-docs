---
title: "How to Start and Stop DTC or SNA LU 6.2 Resync TP2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14da7d32-bddc-4a3c-b124-b5cd7a8d8163
caps.latest.revision: 5
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