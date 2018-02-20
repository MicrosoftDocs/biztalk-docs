---
title: "How to Assign an Application to an Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2ca8850-6789-455b-be53-56f126605c06
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Assign an Application to an Adapter
To process information between a local application and a remote server, an adapter must have one or more applications assigned to it.  
  
### To assign an application to an adapter  
  
1.  Add the application to the adapter by using `ISSOPSAdmin.AssignApplicationToAdapter`.  
  
2.  You can retrieve the current list of applications assigned to an adapter by using `ISSOAdmin.GetApplicationsForAdapter`.  
  
3.  Once you are finished, you can remove an application from an adapter by using `ISSOPSAdmin.RemoveApplicationFromAdapter`.