---
title: "Client Application Does Not Start but No Error Given1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0d07010-d56f-4fa5-a849-b66c210ea6c4
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Client Application Does Not Start but No Error Given
If you double-click the .exe file for your Visual Basic client application and nothing happens but no error message appears, the problem may be that you did not deploy the TI component that your client application is attempting to use.  
  
 Normally, if a TI component type library is not registered (that is, it has not been deployed in a COM+ application), you will receive error message number 429 that says, "ActiveX component cannot create object." However, no error appears at all if the unregistered TI component contains a user-defined type (UDT) and that UDT is referenced in the Visual Basic client application.  
  
 To resolve this problem, deploy the TI component in a COM+ application to automatically register it. Then your Visual Basic client application will work.