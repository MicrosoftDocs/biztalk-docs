---
description: "Learn more about: Configuring Dependent LUs"
title: "Configuring Dependent LUs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Dependent LUs
When you configure a dependent LU, make sure you do the following:  
  
- Set up a single session for each dependent LU. (Only one session is allowed for each dependent LU.)  
  
- Specify the remote end, using **Host**.  
  
- Use VTAM 3.2 or later for host-to-APPC LU communication.  
  
  Set the host VTAM to a value of 1 or greater in the *LOCADDR*= parameter of the LU definition.  
  
## SeeAlso  
 [Dependent APPC LUs](../core/dependent-appc-lus1.md)
