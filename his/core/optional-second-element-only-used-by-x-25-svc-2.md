---
description: "Learn more about: Optional Second Element (Only Used by X.25 SVC)"
title: "Optional Second Element (Only Used by X.25 SVC)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Optional Second Element (Only Used by X.25 SVC)
**Element 2**  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr–>elteptr|PTRBFELT|Pointer to next buffer element: NULL|  
|hdreptr–>elteptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>elteptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>elteptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s]|Not applicable|Length of facilities data field (= c) inclusive of this length byte 0x01 no facilities data|  
|dataru[s+1..s+c–1]|Not applicable|CHAR[c–1]Facilities data|  
|dataru[s+c]|Not applicable|CHARLength of user data field (= d) inclusive of this length byte 0x01 no user data|  
|dataru[s+c+1..s+c+d]|Not applicable|User data|
