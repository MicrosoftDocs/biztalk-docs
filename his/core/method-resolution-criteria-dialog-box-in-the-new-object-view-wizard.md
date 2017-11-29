---
title: "Method Resolution Criteria Dialog Box (in the New Object View Wizard)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15309"
ms.assetid: fb6a3571-8ae5-4d59-a828-e2484810cbd1
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Method Resolution Criteria Dialog Box (in the New Object View Wizard)
Use the **Method Resolution Criteria** dialog to provide detailed information about a specific method on the object view.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Method**|View the name of the object's method for which the method resolution criteria are being set.|  
|**Endpoint**|Select the endpoints on the local environment that are available for the type of resolution specified in **Type**. All endpoints in the LE are listed and available for selection. If an endpoint selected for one resolution type is already used with another resolution type then an error message will pop up when you click **Apply**. The error message explains which object and view has this endpoint used with another resolution type.|  
|**Method resolution criteria**|View a description of the behavior for the IT runtime when it resolves a request to a method. The sequence of data flow events may require the TI to send and receive various amounts of data prior to obtaining the ability to make the connection between the incoming request and the target method.|  
|**Type**|Select the type of resolution to be conducted:<br /><br /> -   **Endpoint** The endpoint resolution type is simplest means of resolving a request to a method. A data stream directed to a port always executes a single method on a view. This model is considered "raw sockets," and it represents a single synchronous exchange of data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Endpoint** disables **Object Name**, **Input format** and **Output format** and clears their contents.<br />-   **Transaction Request Message (TRM)** The TRM resolution type is specific to the IBM CICS Concurrent Server model and the Microsoft variant MSLink model. It represents a double exchange sequence. The first exchange represents the transaction request, and the second exchange represents the request and reply data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Transaction Request Message (TRM)** enables **Object**, **Input format**, and **Output format**. This option is available only for TCP/IP local environment/host environment pairs.<br />-   **Enhanced Listener Message (ELM)**:<br />-   **Data** Similar to **Endpoint** in that it adds the flexibility to identify a string in the data stream directed to a port that is used to associate the request with a specific method in the view. This model is considered "raw sockets." It represents a single synchronous exchange of data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Data** disables **Object**, **Input format**, and **Output format** and clears their contents.<br />-   **Link to Program Name:** Resolves all the methods of a new object view using the data information specified when the object view was created. When a new view is created and associated with the HE, the method resolves to the Link Tran ID field in the default HE resolution. Selecting **Link to Program Name** disables **Object**, **Input format**, and **Output format** and clears their contents. This option is available only for SNA local environment/host environment pairs. **Note:**  Only **TRM-MSLink** and **Link to Program Name** are available for Link methods. Methods can be defined as Link in Visual Studio by setting the **Is Link** property to **True**.|  
|**Object Name**|Select the object. The list of objects is populated from the Help string in the interface definition of objects identified to the resolution handler. Microsoft provides three TRM resolution handlers:<br /><br /> -   **Microsoft HIS - TRM Handler MS Link** (default)<br />-   **Microsoft HIS - TRM Handler MSCCS**<br />-   **Microsoft HIS - TRM Handler IBMCCS**|  
|**Input format**|Select the format of the data stream that represents the TRM sent by the client host application program. The list of TRM input formats is determined by the UDT) definitions in the MicrosoftTRMDef.tim file in the installation TIMLibs directory. The **Input format** box is blank by default, but three input formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **MS Link Request Format**<br />-   **IBM Listener Type 1 Request Format**<br />-   **IBM Listener Type 2 Request Format**|  
|**Output format**|Select the format of the data stream that represents the reply to the TRM that was sent by the host application program. TI formats a data stream that is returned to the host client application program in the form defined by the output TRM. The list of TRM output formats is determined by the UDT definitions in the MicrosoftTRMDef.tim file. The **Output format** box is blank by default, but three output formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **MS Link Reply Format**<br />-   **IBM Listener Type 1 Reply Format**<br />-   **IBM Listener Type 2 Reply Format**|  
|**Link**|View the name of the program being linked to.|  
|**Program Name**|Name of the TP program.|  
|**Resolution Data**|View a definition of the data used by the IT runtime when it resolves a request to a method.|  
|**Data**|Type the method resolution criteria for a method on the object view. The criteria can be a maximum of 256 alpha-numeric characters. This control is enabled for resolution types **Transaction Request Message (TRM)** and **Data**. This control is disabled for resolution type **Endpoint**.|  
|**Position**|Type the resolution position. The position can be a maximum of nine numeric characters. This control is enabled for resolution type **Data** and disabled for resolution types **Transaction Request Message (TRM)** and **Endpoint**.|  
  
## See Also  
 [TI Manager Properties](../core/ti-manager-properties.md)