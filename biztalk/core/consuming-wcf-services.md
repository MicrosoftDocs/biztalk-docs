---
description: "Learn more about: Consuming WCF Services"
title: "Consuming WCF Services"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Consuming WCF Services
Consuming WCF services enables you to add existing WCF services to your business process. You can aggregate several WCF services into a single orchestration.  
  
 You can consume (call) a WCF service from your orchestration by using the BizTalk WCF Service Consuming Wizard. The BizTalk WCF Service Consuming Wizard creates port types and message types necessary for consuming WCF services. The BizTalk WCF Service Consuming Wizard also creates two binding files that can be imported by the development command-line tool or wizard to configure the send ports with the system-provided binding WCF adapters and the WCF-Custom adapter. The wizard allows you to use SOAP headers with a consumed WCF service, change the URI of a consumed WCF service, and dynamically set the WCF for a consumed Web service. WCF send adapters consume WCF services and WCF receive locations publish WCF services.  
  
 The BizTalk WCF send adapters include five physical send adapters that represent the WCF predefined bindings **BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**. The BizTalk WCF adapters also include the custom adapters that enable you to freely configure WCF binding and behavior information for a send port. For more information about how to configure a WCF send handler and send port, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).  
  
## In This Section  
  
-   [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)  
  
-   [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)  
  
-   [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)  
  
-   [How to Handle Typed Fault Contracts in Orchestrations](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)  
  
-   [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)
