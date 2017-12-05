---
title: "Invoking TPs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f884dbc-a1e5-48ae-9be3-f395cea31a9d
caps.latest.revision: 3
---
# Invoking TPs
An invoking TP can be located on any system on the SNA network. An invoking TP identifies itself by issuing [TP_STARTED](../core/tp-started1.md), which specifies the name of the invoking TP and can specify the LU alias that the TP uses. If the LU alias is not specified in **TP_STARTED**, Host Integration Server must be configured to supply it through one of two types of default local LU; otherwise, **TP_STARTED** will fail. For more information, see [Configuring Invoking TPs on Host Integration Server](../core/configuring-invoking-tps-on-host-integration-server1.md).  
  
 Next, the invoking TP initiates the invoking process by issuing [ALLOCATE](../core/allocate1.md) or [MC_ALLOCATE](../core/mc-allocate1.md), in which it specifies the name of the invokable TP, and can also specify the partner LU alias (the LU alias to be used by the invokable TP). If the partner LU is not specified in **ALLOCATE** or **MC_ALLOCATE**, [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] must be configured to supply one through the default remote APPC LU assigned to the user who started the invoking TP; otherwise, **ALLOCATE** or **MC_ALLOCATE** will fail. For more information, see [Configuring Invoking TPs on Host Integration Server](../core/configuring-invoking-tps-on-host-integration-server1.md).  
  
 After a TP successfully issues an **ALLOCATE** or **MC_ALLOCATE** verb, an allocation request flows. For more information about what happens after an invoking TP requests an invokable TP, see [Matching Invoking and Invokable TPs](../core/matching-invoking-and-invokable-tps2.md).