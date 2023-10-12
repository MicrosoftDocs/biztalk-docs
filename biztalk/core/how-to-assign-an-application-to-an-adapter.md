---
description: "Learn more about: How to Assign an Application to an Adapter"
title: "How to Assign an Application to an Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Assign an Application to an Adapter
To process information between a local application and a remote server, an adapter must have one or more applications assigned to it.  
  
### To assign an application to an adapter  
  
1.  Add the application to the adapter by using `ISSOPSAdmin.AssignApplicationToAdapter`.  
  
2.  You can retrieve the current list of applications assigned to an adapter by using `ISSOAdmin.GetApplicationsForAdapter`.  
  
3.  Once you are finished, you can remove an application from an adapter by using `ISSOPSAdmin.RemoveApplicationFromAdapter`.
