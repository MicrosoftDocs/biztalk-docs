---
title: "SOAP Transport Properties Dialog Box, Web service Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.soap.transport.webservice"
helpviewer_keywords: 
  - "SOAP adapters, Web services"
  - "SOAP adapters, properties"
  - "properties, SOAP adapters"
  - "Web services, SOAP adapters"
ms.assetid: ea43d93b-5f97-479c-a9af-193f3218adb0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Transport Properties Dialog Box, Web service Tab
In the **SOAP Transport Properties** dialog box, use the **Web Service** tab to configure the send port for the SOAP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Orchestration Web Port**|Specify to use the Web service that is exposed at the Web Service URL listed on the General tab.<br /><br /> This is the default setting.|  
|**Assembly name**|Specify the name of the assembly containing the Web service proxy. This field can be populated by clicking the browse button to find an assembly. After selecting the assembly this box is populated with the fully qualified name of the assembly.|  
|**Type name**|Specify the name of the class that contains the Web method to be invoked. This can be selected from list of types contained within the assembly.|  
|**Method name**|Specify one of the methods in the list box or choose the option to "Specify later." If the option to "Specify later" is chosen, the Web method must be set by some other means, such as a pipeline component. This pipeline component would be placed in the preassemble stage of the pipeline.|  
|**SOAP 1.2**|Specify to generate proxy code that will support the SOAP 1.2 protocol. If this option is not selected, SOAP 1.1-compliant proxy code will be generated.<br /><br /> Default value: Not selected.|  
  
## See Also  
 [Publishing Web Services](../core/publishing-web-services.md)