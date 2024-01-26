---
description: "Learn more about: Case Discrepancies in Assigned Names"
title: "Case Discrepancies in Assigned Names1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Case Discrepancies in Assigned Names
Use care when assigning names to any part of a type library in TI Designer. You can assign case-sensitive variants of the same name. For example, you can assign a name of `myparam` to a parameter of one method, and `MyParam` to a parameter of another method. However, when you save the type library, the name of the second parameter will be changed to match the case of the first. In the previous example, both parameters would be saved as `myparam`. Such unexpected changes in case are potentially confusing, although they will not affect the operation of your application.
