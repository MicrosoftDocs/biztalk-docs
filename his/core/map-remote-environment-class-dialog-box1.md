---
title: "Map Remote Environment Class Dialog Box1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15449"
ms.assetid: 963516b2-c79f-4524-9eb6-e86105449bc2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Map Remote Environment Class Dialog Box
Use the **Map Remote Environment Class** dialog box to update the definition of a remote environment (RE) class that is no longer supported or does not conform to Transaction Integrator (TI) requirements.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remote environment class**|Type or select the COM type library or .NET assembly class of the remote environment.|  
|**Vendor**|Select the name of the vendor supplying the remote environment.|  
|**Protocol**|Select the data communication protocol to be used to connect to the remote environment. The available communication protocols are:<br /><br /> -   **TCP/IP** (default)<br />-   **LU 6.2**|  
|**Target environment**|Select the application environment running on the remote host system. The available environments are:<br /><br /> -   **CICS** (default)<br />-   **IMS**<br />-   **OS400** (TCP only)|  
|**Programming model**|Select the programming model associated with the remote environment. The available models for the TCP/IP CICS target environment are:<br /><br /> -   **TRM User Data** (default)<br />-   **TRM Link**<br />-   **ELM User Data**<br />-   **ELM Link**<br /><br /> The available models for the LU 6.2 CICS target environment are:<br /><br /> -   **CICS User Data**<br />-   **CICS Link**<br />-   The available models for the TCP/IP IMS target environment are:<br />-   **IMS Connect**<br />-   The only available model for the LU 6.2 IMS target environment is **IMS User Data**.<br /><br /> The only available model for the OS400 target environment is **Distributed Program Call**.|  
  
## See Also  
 [Wizards and Dialog Boxes (TI Project)](../core/wizards-and-dialog-boxes-ti-project-1.md)