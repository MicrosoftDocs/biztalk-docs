---
title: "Default Tab (Host Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15334"
ms.assetid: 306c305e-a55e-45d3-8380-abb2c054da39
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Default Tab (Host Environment Properties)
The **Default** tab of the properties page of a specific host environment defines the manner in which the host typically communicates with Transaction Integrator. These defaults are applied during the configuration for an object view.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Default method resolution criteria**|View the definition of the default behavior for setting up the method resolution criteria for a new object view.|  
|**Type**|Select the type of resolution to be conducted:<br /><br /> **Endpoint**: The endpoint resolution type is the simplest means of resolving a request to a method. A data stream directed to a port always executes a single method on a view. This model is considered "raw sockets," and represents a single synchronous exchange of data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Endpoint** disables the **Object**, **Input format** and **Output format** boxes and clears their contents.<br /><br /> -   **Transaction Request Message (TRM)**: The TRM resolution type is specific to the IBM CICS Concurrent Server model and the Microsoft variant, MSLink model. It represents a double exchange sequence. The first exchange represents the transaction request; the second exchange represents the request and reply data.<br />     When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Transaction Request Message (TRM)** enables the **Object**, **Input format**, and **Output format** boxes. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting one of the predefined **Transaction Request Objects** disablesthe **Input format** and **Output format** boxes; it also disables the **Link Tran ID** box and clears its contents. Selecting a custom object enables the **Input format** and **Output format** boxes and sets their initial values to the Microsoft-supplied TRM handler items.<br />-   **Data**: Similar to **Endpoint** in that it adds the ability to identify a string in the data stream directed to a port, that is used to associate the request with a specific method in the view. This model is considered "raw sockets." It represents a single synchronous exchange of data. Selecting **Data** disables the **Object**, **Input format**, **Output format,** and **Link Tran ID** boxes and clears their contents.<br />-   **Link:** The Link resolution type is specific to the IBM CICS DPL model. The endpoint name is representative of the TP name that is the CICS mirror transaction ID.<br />     Select **Link** to resolve all the methods of a new object view using the data information specified when the object view was created. When a new view is created and associated with the HE, the method resolves to the Link Tran ID field in the default HE resolution. Selecting **Link** disables the **Object**, **Input format**, and **Output format** boxes and clears their contents.|  
|**Object**|Select the object. The list of objects is populated from the Help string in the interface definition of objects identified to the resolution handler. Microsoft provides three TRM resolution handlers:<br /><br /> -   **Microsoft HIS - TRM Handler MS Link** (default)<br />-   **Microsoft HIS - TRM Handler MSCCS**<br />-   **Microsoft HIS - TRM Handler IBMCCS**<br />-   **Microsoft HIS - Link Handler**|  
|**Input format**|Select the format for the data stream that represents the TRM sent by the client host application program. The list of TRM input formats is populated from the user-defined type definitions in the MicrosoftTRMDef.tim file. The **Input format** box is disabled for standard TRM handlers and enabled for custom TRM handlers, but three input formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **TRMINMSLink**<br />-   **TRMINMSCCS**<br />-   **TRMINIBMCCS**|  
|**Output format**|Select the format for the data stream that represents the reply to the TRM that was sent by the host application program. TI formats a data stream to be returned to the host client application program in the form defined by the output TRM. The list of TRM output formats is populated from the UDT definitions in the MicrosoftTRMDef.tim file. The **Output format** box is disabled for standard TRM handlers and enabled for custom TRM handlers, but three output formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **TRMOUTMSLink**<br />-   **IBM Listener Reply Format (TRMOUTCCS)**<br />-   **Link Tran ID:** Select the TP name or Link Mirror Tran ID for the SNA local environment. This control is enabled only when the **Network Type** is set to SNA and the **Resolution Type** is set to Link.|  
  
> [!CAUTION]
>  The properties of a host environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the host environment to function incorrectly.  
  
## See Also  
 [Host Environments Node](../core/host-environments-node.md)   
 [Host Environment Node](../core/host-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)