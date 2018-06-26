---
title: "Develop your SAP applications using the adapter in BizTalk | Microsoft Docs"
description: Create my SAP applications using WCF, BizTalk Server, or ADO.NET with the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

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

## Overview
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. Client applications can consume the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to invoke operations on SAP artifacts. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be consumed:  
  
- Through a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- By invoking methods on an instance of a client proxy.  
  
- As a hosted WCF service.  
  
- By sending SOAP messages over a channel instance in code that uses the WCF channel model.  
  
- Through an ADO.NET interface.  

## BizTalk vs WCF service vs WCF channel vs ADO.NET
  
 The following table:  
  
- Lists the different operations that can be performed on an SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- Indicates which of the approaches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, WCF channel model, or ADO.NET interface) can be used to perform the operations.  
  
- Provides links to more information about performing the task using the chosen approach.  
  
|Task|BizTalk Server|WCF Service Model|WCF Channel Model|ADO.NET Interface|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|Invoking RFCs in an SAP system|[Invoke RFCs in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)|[Invoke RFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)|[Invoke RFCs and BAPIs using the EXEC Command in SAP](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-and-bapis-using-the-exec-command-in-sap.md)|  
|Receiving inbound RFC calls from an SAP system|[Receive Inbound RFC Calls from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)|[Receive Inbound RFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)|[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|Invoking tRFCs in an SAP system|[Invoke tRFCs in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)|[Invoke tRFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Receiving inbound tRFC calls from an|[Receive Inbound tRFC Calls from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)|[Receive Inbound tRFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)|[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|Performing transactions on an SAP system|[Run BAPI Transactions in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)|[Invoke BAPIs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Sending an IDOC to an SAP system|[Send IDOCs to SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)|[Send IDOCs to SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)|[Invoke Operations on the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Receiving an IDOC from an SAP system|[Receive IDOCs from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)||[Receive Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  

## Next steps

 The next topics provide information on procedures, and examples to develop applications that consume the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programming solutions. 

- [Create a connection to the SAP system](create-a-connection-to-the-sap-system.md)
- [Get Metadata for SAP Operations in Visual Studio](get-metadata-for-sap-operations-in-visual-studio.md)
- [Working with the binding properties](read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)
- [Streaming and the SAP Adapter](streaming-and-the-sap-adapter.md)
- [Develop BizTalk applications using the SAP adapter](develop-biztalk-applications-using-the-sap-adapter.md)
- [Develop applications using the WCF Service Model](develop-sap-applications-using-the-wcf-service-model.md)
- [Develop applications using the WCF Channel Model](develop-sap-applications-using-the-wcf-channel-model.md)
- [Get metadata programmatically](get-metadata-programmatically-from-sap.md)
- [Use the .NET Framework Data Provider for mySAP](use-the-net-framework-data-provider-for-mysap-business-suite.md)
- [Use the SAP adapter with SharePoint](use-the-sap-adapter-with-sharepoint.md)
- [Samples](samples-for-the-sap-adapter.md)
- [Use svcutil.exe](use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md) 
 
  
## See Also  
 [Create the SAP system connection URI](create-the-sap-system-connection-uri.md)