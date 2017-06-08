---
title: "Develop your SAP applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, use adapters"
  - "adapters, working with"
  - "working with adapters"
ms.assetid: e8315c0d-923b-433e-9d11-4e8a53e0a1d9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop your SAP applications
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. Client applications can consume the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to invoke operations on SAP artifacts. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be consumed:  
  
-   Through a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   By invoking methods on an instance of a client proxy.  
  
-   As a hosted WCF service.  
  
-   By sending SOAP messages over a channel instance in code that uses the WCF channel model.  
  
-   Through an ADO.NET interface.  
  
 The following table:  
  
-   Lists the different operations that can be performed on an SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Indicates which of the approaches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, WCF channel model, or ADO.NET interface) can be used to perform the operations.  
  
-   Provides links to more information about performing the task using the chosen approach.  
  
|Task|BizTalk Server|WCF Service Model|WCF Channel Model|ADO.NET Interface|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|Invoking RFCs in an SAP system|[Invoke RFCs in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)|[Invoke RFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)|[Invoke RFCs and BAPIs using the EXEC Command in SAP](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-and-bapis-using-the-exec-command-in-sap.md)|  
|Receiving inbound RFC calls from an SAP system|[Receive Inbound RFC Calls from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)|[Receive Inbound RFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)|[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|Invoking tRFCs in an SAP system|[Invoke tRFCs in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)|[Invoke tRFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Receiving inbound tRFC calls from an|[Receive Inbound tRFC Calls from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)|[Receive Inbound tRFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)|[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|Performing transactions on an SAP system|[Run BAPI Transactions in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)|[Invoke BAPIs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Sending an IDOC to an SAP system|[Send IDOCs to SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)|[Send IDOCs to SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Receiving an IDOC from an SAP system|[Receive IDOCs from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)||[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
  
 The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programming solutions. The topics also provide information on other key aspects of using the adapters such as:  
  
-   Connecting to the SAP system.  
  
-   Retrieving metadata from the SAP system.  
  
-   Using binding properties to configure the adapter.  
  
 
  
## See Also  
 [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)