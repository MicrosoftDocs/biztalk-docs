---
title: "Connection String Keywords1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5635790b-10b7-4a31-aa53-405778b5b9e4
caps.latest.revision: 4
---
# Connection String Keywords
The format of a connection string is a semicolon-delimited list of key/value parameter pairs:  
  
 **keyword1=value; keyword2=value**  
  
 When the connection string is validated by the data source, spaces are ignored and keywords are not case sensitive. However, values may be case sensitive, depending on the case sensitivity of the data source. To include values that contain a semicolon, single-quote character, or double-quote character, the value must be enclosed in double quotation marks.  
  
 To avoid misspellings, the Managed Provider for DB2 exposes the keywords and values of the connection string as properties.  
  
## Example  
  
## See Also  
 [Working with Connection Strings and the Managed Provider for DB2](../HIS2010/working-with-connection-strings-and-the-managed-provider-for-db21.md)