---
title: "Error - Failure writing XML Type Blob file (&lt;file:---{0}&gt;). Error: {1} | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb787db4-0919-4e1b-bfe1-ba0e19a08881
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Failure writing XML Type Blob file (&lt;file:---{0}&gt;). Error: {1}
**Error Code**  
  
 btm1062  
  
 **Explanation**  
  
 This occurs when mapper compiler is not able to create the xml blob file in the location specified by the build task.  
  
 **User Action**  
  
 Check the error message included in the message (Error {1})i. If it is an UnAuthorised exception, then you may not have write permission for the project output folder.