---
title: "Case Discrepancies in Assigned Names2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 143a61e6-8c1c-4741-89e8-d89a74fa8de4
caps.latest.revision: 4
---
# Case Discrepancies in Assigned Names
Use care when assigning names to any part of a type library in TI Designer. You can assign case-sensitive variants of the same name. For example, you can assign a name of `myparam` to a parameter of one method, and `MyParam` to a parameter of another method. However, when you save the type library, the name of the second parameter will be changed to match the case of the first. In the previous example, both parameters would be saved as `myparam`. Such unexpected changes in case are potentially confusing, although they will not affect the operation of your application.