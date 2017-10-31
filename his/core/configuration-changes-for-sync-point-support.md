---
title: "Configuration Changes for Sync Point Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 331421c6-3d48-42b3-851a-75fa356357a8
caps.latest.revision: 3
---
# Configuration Changes for Sync Point Support
A new check box is added to the Local LU Configuration dialog box. When selected, this indicates that the local LU is able to participate in **synclevel** Sync Point sessions. Host Integration Server uses this option to determine the **synclevel** BIND parameters it sends on BIND requests and responses.  
  
 This field is added to the Host Integration Server configuration file in a field that is no longer used by Host Integration Server. Existing configurations from earlier versions of Host Integration Server will therefore continue to work unmodified.