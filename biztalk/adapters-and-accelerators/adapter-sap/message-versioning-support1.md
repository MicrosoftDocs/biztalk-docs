---
description: "Learn about the support  for message versioning in the Microsoft BizTalk Adapter for mySAP Business Suite."
title: "Message Versioning Support1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Support for Message Versioning

The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations. The current version is `http://Microsoft.LobServices.Sap/2007/03`. This means that for an RFC named "RFC_SAMPLE", the RFC operation surfaced by the adapter has the following:  
  
- Node ID: `http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE`  
  
- Message action: `http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE`  
  
- Namespace: `http://Microsoft.LobServices.Sap/2007/03/Rfc`  
  
> [!NOTE]
> This feature does not provide backward compatibility with the earlier versions of the adapter.  
  
## See Also
  
[Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)
