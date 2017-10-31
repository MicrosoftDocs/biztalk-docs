---
title: "Building Connection Strings1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c28025fa-c79d-4d30-8829-23e6c52d6761
caps.latest.revision: 4
---
# Building Connection Strings
The Managed Provider for DB2 provides a strongly typed connection string builder class that inherits from `DbConnectionStringBuilder`. The connection string builders let developers programmatically create syntactically correct connection strings that are based on user input, and also parse and rebuild existing connection strings by using methods of the class. The <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2ConnectionStringBuilder> class provides strongly typed properties that correspond to the known key/values pairs allowed by the Managed Provider for DB2.  
  
 In earlier versions of ADO.NET, there was no compile-time checking of connection strings that consisted of concatenated string values. At run time, an incorrect keyword would generate an invalid ArgumentException. Because values received from a user were not checked or quoted appropriately, it was possible for an attacker to bypass expected settings.  
  
 The <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2ConnectionStringBuilder> class performs checks for valid key/value pairs. An invalid pair throws an exception and injected values are handled in a safe manner. Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.  
  
## Example  
  
## See Also  
 [Working with Connection Strings and the Managed Provider for DB2](../core/working-with-connection-strings-and-the-managed-provider-for-db2.md)