---
description: "Learn more about: Restrictions on the Destination URL Property"
title: "Restrictions on the Destination URL Property"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
