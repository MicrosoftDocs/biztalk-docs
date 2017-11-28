---
title: "Restrictions on the Destination URL Property | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [HTTP adapters], restrictions"
  - "HTTP adapters, restrictions"
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restrictions on the Destination URL Property
The destination URL is a string that specifies the address of the HTTP server where you want to send messages using the HTTP protocol.  
  
 The following rules and restrictions apply to the destination URL property:  
  
-   You must always specify the destination URL property in the following format:  
  
     http[s]://\<host\>[:\<port\>][/\<path\>[/\<file\>[?\<query-string\>]]]  
  
-   The whole string may or may not be URI encoded.  
  
-   The whole string, except the query string, cannot contain any of the following characters: \< \> : \ &#124; " ? *.  
  
-   The property is not case-sensitive.  
  
-   The length of the string must not exceed 256 characters.  
  
## See Also  
 [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md)