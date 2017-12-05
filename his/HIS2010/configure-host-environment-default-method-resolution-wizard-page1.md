---
title: "Configure Host Environment Default Method Resolution Wizard Page1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15316"
ms.assetid: e496bd67-63c0-4993-a40e-0e78652e0004
caps.latest.revision: 4
---
# Configure Host Environment Default Method Resolution Wizard Page
Use the **Configure Host Environment Default Method Resolution** wizard page to identify the default characteristics of the typical interaction of the applications programs on the host with the application programs on the server. Select the default method resolution criteria for the host.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host environment**|View the name of the host environment. The name was entered on a previous page of the wizard. To change the name, click **Back**.|  
|**Default method resolution criteria**|View the definition of the default behavior for setting up the method resolution criteria for a new object view.|  
|**Type**|Select the type of resolution to be conducted:<br /><br /> **Endpoint:** The endpoint resolution type is the simplest means of resolving a request to a method. A data stream directed to a port always executes a single method on a view. This model is considered "raw sockets," and represents a single synchronous exchange of data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Endpoint** disables the **Object**, **Input format** and **Output format** boxes and clears their contents.<br /><br /> -   **Transaction Request Message (TRM):** The TRM resolution type is specific to the IBM CICS Concurrent Server model and the Microsoft variant, MSLink model. It represents a double exchange sequence. The first exchange represents the transaction request; the second exchange represents the request and reply data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Transaction Request Message (TRM)** enables the **Object**, **Input format**, and **Output format** boxes.<br />-   **Enhanced Listener Message (ELM)**:<br />-   **Data:** Similar to **Endpoint** in that it adds the ability to identify a string in the data stream directed to a port that is used to associate the request with a specific method in the view. This model is considered "raw sockets." It represents a single synchronous exchange of data. When a new view is created and associated with the HE, the method resolves to the first endpoint defined in the associated local environment. Selecting **Data** disables the **Object**, **Input format**, and **Output format** boxes and clears their contents.<br />-   **Link to Program Name:** Select **Link to Program Name** to resolve all the methods of a new object view using the data information specified when the object view was created. When a new view is created and associated with the HE, the method resolves to the Link Tran ID field in the default HE resolution. Selecting **Link to Program Name** disables the **Object**, **Input format**, and **Output format** boxes and clears their contents.|  
|**Object**|Select the object. The list of objects is populated from the Help string in the interface definition of objects defined as TRM resolution handlers. Microsoft provides three TRM resolution handlers:<br /><br /> -   **Microsoft HIS - TRM Handler MS Link** (default)<br />-   **Microsoft HIS - TRM Handler MSCCS**<br />-   **Microsoft HIS - TRM Handler IBMCCS**|  
|**Input format**|Select the format of the data stream that represents the TRM sent by the client host application program. The list of TRM input formats is determined by the user-defined type definitions in the MicrosoftTRMDef.tim file. The **Input format** box is blank by default, but three input formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **TRMINMSLink**<br />-   **TRMINMSCCS**<br />-   **TRMINIBMCCS**|  
|**Output format**|Select the format of the data stream that represents the reply to the TRM that was sent by the host application program. TI formats a data stream that is returned to the host client application program in the form defined by the output TRM. The list of TRM output formats is determined by the UDT definitions in the MicrosoftTRMDef.tim file. The **Output format** box is blank by default, but three output formats are defined that match the names of the resolution handler **Object**:<br /><br /> -   **MS Link Reply Format**<br />-   **IBM Listener Type 1 Reply Format**<br />-   **IBM Listener Type 2 Reply Format**|  
|**Link Tran ID**|View or select an existing TP name or the link mirror transaction ID for the local environment.|  
  
## See Also  
 [Configure a New Security Policy Wizard Page (in the New Application Deployment Wizard) (1)](../HIS2010/4a43b40e-411e-4b88-b2f0-6527269c65e8.md)   
 [New Application Deployment Wizard](../HIS2010/new-application-deployment-wizard2.md)