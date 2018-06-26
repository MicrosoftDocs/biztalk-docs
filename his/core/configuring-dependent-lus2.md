---
title: "Configuring Dependent LUs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 812067c9-137c-4819-9148-5592e6ba76ac
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Dependent LUs
When you configure a dependent LU, make sure you do the following:  
  
- Set up a single session for each dependent LU. (Only one session is allowed for each dependent LU.)  
  
- Specify the remote end, using **Host**.  
  
- Use VTAM 3.2 or later for host-to-APPC LU communication.  
  
  Set the host VTAM to a value of 1 or greater in the *LOCADDR*= parameter of the LU definition.  
  
## SeeAlso  
 [Dependent APPC LUs](../core/dependent-appc-lus1.md)