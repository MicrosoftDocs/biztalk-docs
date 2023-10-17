---
title: "Develop your Siebel applications in BizTalk Server | Microsoft Docs"
description: Create Siebel applications using WCF, or in BizTalk Server with the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bc04906-6d64-433c-b357-797ec5883279
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop your Siebel applications

## Overview
The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. Client applications can consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to invoke operations on Siebel artifacts. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can be consumed:  
  
-   Through a physical port binding in a BizTalk Server solution.  
  
-   By invoking methods on an instance of a client proxy.  
  
-   As a hosted WCF service.  
  
-   By sending SOAP messages over a channel instance in code that uses the WCF channel model.  
  
-   Through an ADO.NET interface.  
  
## BizTalk vs WCF service vs WCF channel vs ADO.NET
 The following table:  
  
- Lists the different operations that can be performed on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
- Indicates which of the approaches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, WCF channel model, or ADO.NET interface) can be used to perform the operations.  
  
- Provides links to more information about performing the task using the chosen approach.  
  
|                                   Task                                    |                                                                                       BizTalk Server                                                                                        |                                                                                    WCF Service Model                                                                                    |                                                                              WCF Channel Model                                                                               |                                                                                                                        ADO.NET Interface                                                                                                                        |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Basic Insert, Update, Delete, and Query operations on business components |              [Run Operations on Business Components Using BizTalk Server and the Siebel adapter](run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)              |     [Run Operations on Business Components with the Siebel adapter using the WCF Service Model](run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)     | [Run Operations on Business Components with the Siebel adapter using the WCF Channel Model](run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md) | [Run a SELECT Query on Business Components with Siebel](run-a-select-query-on-business-components-with-siebel.md) **Note:**  You can only perform a SELECT operation using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]. |
|             Operations on business components with MVG fields             |   [Run Operations on Business Components with MVG Fields Using BizTalk Server and the Siebel adapter](run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)    | [Run Operations on Business Components with MVG Fields with the Siebel adapter using the WCF Service Model](work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md) |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |
|          Operations on business components with picklist fields           | [Run Operations on Business Components with Picklist Fields Using BizTalk Server and the Siebel adapter](run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md) |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |
|                        Invoking business services                         |                [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)                |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                    [Run an EXECUTE Operation on Business Services with Siebel](run-an-execute-operation-on-business-services-with-siebel.md)                                                                    |
|            Invoking business services with integration objects            |           [Invoke Business Service Methods with Integration Objects using the Siebel adapter](run-business-service-methods-with-integration-objects-using-the-siebel-adapter.md)            |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |

## Next steps  
 The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programming solutions. 

- [Create a connection to the Siebel system](create-a-connection-to-the-siebel-system.md)
- [Get Metadata for Siebel Operations in Visual Studio](get-metadata-for-siebel-operations-in-visual-studio.md)
- [Metadata Node IDs](metadata-node-ids1.md)
- [Working with the binding properties](read-about-biztalk-adapter-for-siebel-binding-properties.md)
- [Develop BizTalk applications using the Siebel adapter](develop-biztalk-applications-using-the-siebel-adapter.md)
- [Develop applications using the WCF Service Model](develop-siebel-applications-using-the-wcf-service-model.md)
- [Develop applications using the WCF Channel Model](develop-siebel-applications-using-the-wcf-channel-model3.md)
- [Use the .NET Framework Data Provider for Siebel eBusiness Applications](use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
- [Use the Siebel Adapter with SharePoint](use-the-siebel-adapter-with-sharepoint.md)
- [Samples](samples-for-the-siebel-adapter.md)
- [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications](use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)