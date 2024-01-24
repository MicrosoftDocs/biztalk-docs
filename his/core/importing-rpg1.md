---
description: "Learn more about: Importing RPG"
title: "Importing RPG1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Importing RPG
The Report Program Generator (RPG) is oriented to programs written for use by distributed program call (DPC). The expectation is that the RPG source contains an `*ENTRY PLIST` operation statement. This statement leads the importer down the path of explicitly understanding the exact parameter names. This eliminates the picking and choosing of data areas found in the **Import COBOL Wizard**.  
  
 This implies that the RPG Importer is simple to use. It also implies that the RPG Importer is not designed to be used for raw TCP and raw SNA programming models. The assumptions are as follows:  
  
-   RPG DPC is the most likely programming model that will be used.  
  
-   For those situations where raw TCP or SNA is required, you can still create RPG definitions through basic HIS Designer functionality (not the Import Wizard)  
  
## See Also  
 [HIS Designer Menus](../core/his-designer-menus1.md)
