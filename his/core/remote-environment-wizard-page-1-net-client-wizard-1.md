---
title: "Remote Environment Wizard Page 1 (.NET Client Wizard)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ebiz.his.2006.tidesigner.wizard.netclient.reforTCPandCICS"
ms.assetid: 97d634ea-d078-4f28-86e9-6295d7838033
caps.latest.revision: 5
---
# Remote Environment Wizard Page 1 (.NET Client Wizard)
Use the **Remote Environment** wizard page to define the remote environment (RE). An RE identifies an application execution environment running on a remote host system. The RE can have a data communication protocol and a programming model associated with it.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Vendor**|Select the name of the vendor supplying the remote environment.|  
|**Protocol**|Select the data communication protocol to be used to connect to the remote environment. The available communication protocols are:<br /><br /> -   **TCP/IP** (default)<br />-   **LU 6.2**|  
|**Target environment**|Select the application environment running on the remote host system. The available environments are:<br /><br /> -   **CICS** (default)<br />-   **IMS**<br />-   **OS400** (TCP/IP only)|  
|**Programming model**|Select the programming model associated with the remote environment. The available models for the TCP/IP CICS target environment are:<br /><br /> -   **TRM User Data** (default)<br />-   **TRM Link**<br />-   **ELM User Data**<br />-   **ELM Link**<br /><br /> The available models for the LU 6.2 CICS target environment are:<br /><br /> -   **CICS User Data**<br />-   **CICS Link**<br />-   The available models for the TCP/IP IMS target environment are:<br />-   **IMS Connect**<br />-   The only available model for the LU 6.2 IMS target environment is **IMS User Data**.<br /><br /> The only available model for the OS400 target environment is **Distributed Program Call**.|  
|**Allow 32K in/out**|Select this option if you want TI to treat the input DFHCOMMAREA independently from the output DFHCOMMAREA. TI typically combines the input DFHCOMMAREA and the output DFHCOMMAREA area. The combined areas cannot exceed 32 KB of data. When this option is selected, TI treats the input DFHCOMMAREA independently from the output DFHCOMMAREA. Each input and output area uses up to 32 KB of data.|  
  
## See Also  
 [Library Properties](../core/library-properties1.md)   
 [TCP Transaction Request Message Link](../core/tcp-transaction-request-message-link1.md)   
 [TCP Enhanced Listener Message Link](../core/tcp-enhanced-listener-message-link2.md)   
 [TCP Transaction Request Message User Data](../core/tcp-transaction-request-message-user-data1.md)   
 [TCP Enhanced Listener Message User Data](../core/tcp-enhanced-listener-message-user-data1.md)   
 [Remote Environment Wizard Page 2 (for OS400) (.NET Client Wizard)](../core/remote-environment-wizard-page-2-for-os400-net-client-wizard-1.md)   
 [Remote Environment Wizard Page 2 (for LU 6.2 Link) (.NET Client Wizard)](../core/remote-environment-wizard-page-2-for-lu-6-2-link-net-client-wizard-1.md)   
 [Completing the New .NET Client Library Wizard Page](../core/completing-the-new-net-client-library-wizard-page1.md)   
 [New .NET Client Library Wizard](../core/new-net-client-library-wizard2.md)