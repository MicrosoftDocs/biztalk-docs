---
title: "Develop SAP applications using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, developing applications"
ms.assetid: 5387d063-31d3-49b3-9771-354802542f8f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop SAP applications using the WCF Service Model
At the lowest level, the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] presents a programming model in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints. This model, known as the WCF channel model, exposes data types and methods that enable you to operate directly on the WCF channel architecture. The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consume them; however, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.  
  
 For this reason, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides another programming model called the WCF service model. The WCF service model involves the use of proxy classes to invoke operations on a target service or to receive operations from a client.  
  
- The proxy class used to invoke operations on a target service is called a WCF client class. This class models the operations exposed by a service as .NET methods with strongly-typed parameters. By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as .NET methods on the WCF client. For more information about WCF clients, see [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx).
  
- The proxy class used to receive an operation from a client is called a WCF service contract class. This class models an operation exposed by your code as a callback method with strongly-typed parameters. You can then host an instance of this class in a **System.ServiceModel.ServiceHost** to enable a client to invoke the operation on your code. By using the WCF service model and a WCF service contract class targeted to the POLLINGSTMT operation, you can receive the results of a polling query from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
  You use tools to generate a WCF client class or a WCF service contract and associated helper code from the service metadata that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes. You can use either of the following tools:  
  
- The ServiceModel Metadata Utility Tool (svcutil.exe), which ships with WCF  
  
- The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], which ships with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]  
  
  The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience and presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations exposed by the adapter. For more information about how to generate a WCF client or a WCF service contract class, see [Generating a WCF Client or a WCF Service Contract for SAP solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
  Because it presents a model that is familiar to .NET programmers and that hides the underlying complexities of SOAP message exchange over a channel, the WCF service model is often the best choice to develop programming solutions for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. However, there are scenarios in which the WCF channel model might be a better choice; particularly in scenarios in which streaming is important. This is because serializing and de-serializing between the XML representation of objects in a SOAP message and the .NET types used to represent them in the service model involves reading the entire message into memory. For more information about using the WCF channel model, see [Develop SAP applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).
  
  The topics in this section contain information, procedures, and examples to help you create and use the WCF service model to develop applications by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## In This Section  
  
-   [Overview of the WCF Service Model with the SAP Adapter](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)  
  
-   [Metadata and the WCF Service Model with SAP](../../adapters-and-accelerators/adapter-sap/metadata-and-the-wcf-service-model-with-sap.md)  
  
-   [Generating a WCF Client or a WCF Service Contract for SAP solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)  
  
-   [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)  
  
-   [Invoke RFCs in SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [Receive Inbound RFC Calls in SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [Invoke tRFCs by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [Receive Inbound tRFC Calls in SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [Invoke BAPIs in SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)  
  
-   [Send IDOCs to SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)