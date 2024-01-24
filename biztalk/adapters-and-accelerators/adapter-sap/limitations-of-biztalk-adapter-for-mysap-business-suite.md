---
description: "Learn more about: Limitations of BizTalk Adapter for mySAP Business Suite"
title: "Limitations of BizTalk Adapter for mySAP Business Suite"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Limitations of BizTalk Adapter for mySAP Business Suite

## Limitations list
The following are known limitations of the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:  
  
- The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is not compatible with Microsoft BizTalk Adapter for mySAP Business Suite, the previous release of the adapter. This release of the adapter does not support sending and receiving messages having schemas generated using the earlier version of the adapter.  
  
- The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs with complex parameter types, including ITAB II (hierarchical) table types.  
  
- The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs having custom ABAP types.  
  
- Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support command and connection timeout.  
  
- If you change the system time of the computer running the BizTalk Server host, the time is not updated automatically in the BizTalk Server host. This could lead to incorrect behavior of the inbound operations that use the receive port of BizTalk Server. As a workaround, you must restart the host instance that has a receive port, after you have changed the system time of the computer running it.  
  
## See Also  
 [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)
