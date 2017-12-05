---
title: "SetupMessage2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34e1e333-e0fe-4388-8f14-9e4e00c8fb97
caps.latest.revision: 3
---
# SetupMessage
The **SetupMessage** function displays a dialog box with user-defined text plus **OK** and **Cancel** buttons. It is useful for debugging.  
  
## Parameters  
 *Argument 0*  
 Language to use (*STF_LANGUAGE*).  
  
 *Argument 1*  
 Which icon to display in the dialog box: STATUS, WARNING, NONFATAL, and so on.  
  
 *Argument 2*  
 The text to be displayed. Can contain line feeds using the LF symbol.  
  
## Return Values  
 *Return 0*  
 Status of the operation.