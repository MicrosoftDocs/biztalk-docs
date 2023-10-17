---
description: "Learn more about: DLC Information Transfer"
title: "DLC Information Transfer2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DLC Information Transfer
When the local node has opened the LINK and STATION LPI connections and received a [Station-Contacted](./station-contacted1.md) message from the SNALink for a remote station, it can exchange data using the data link control (DLC) interface with the physical unit (PU) and associated logical units (LUs) at the remote station.  
  
 Data messages are contained within buffers. The transmission header (TH) of the SNA path information unit is contained within the buffer header. The request/response header (RH), if present, and request/response unit (RU) are contained within one or more buffer elements. The TH is contained in the buffer header for historical reasons. Typically, this will be copied by the SNALink into the element before **startd**, to keep the entire frame in contiguous memory locations. For a description of the DLC-Data message format, see [DLC-Data](./dlc-data1.md).  
  
 Note that all data messages to a specified remote station flow on the associated DLC STATION LPI connection, and not on the controlling DLC LINK LPI connection.  
  
## In This Section  
  
-   [DLC Flow Control](../core/dlc-flow-control1.md)
