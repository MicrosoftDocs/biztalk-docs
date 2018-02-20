---
title: "How to Modify Objects2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4fa02781-dc4a-4ec2-aa0b-0686d0e3ff18
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Modify Objects
After an object has been created and assigned to an application within the host-initiated processing environment, you must be careful when making changes to the object or its Transaction Integrator metadata (TIM) file.  
  
### To safely modify a TIM file for an existing object  
  
1.  In the TI Manager console tree, right click the object to be changed, and then click **Delete**.  
  
2.  Exit TI Manager.  
  
3.  Modify the TIM file and save it.  
  
4.  Start TI Manager.  
  
5.  In the TI Manager console tree, right-click **Objects**, point to **New**, and then click **Object**.  
  
6.  Follow the instructions in the **Object Wizard** to re-create the object.  
  
7.  In the TI Manager console tree, right-click the re-created object, point to **New**, and then click **View**.  
  
8.  Follow the instructions in the **New Object View Wizard** to re-create the object views.