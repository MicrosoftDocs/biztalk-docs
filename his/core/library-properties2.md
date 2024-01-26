---
description: "Learn more about: Library Properties"
title: "Library Properties2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Library Properties
Use the **Library** properties page to set design and remote environment (RE) properties on the component library or .NET assembly.  
  
## Design Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Component Type**|View the type of library component. Possible values are:<br /><br /> -   **.NET Assembly**|  
|**Description**|Type a description of the component. The description can be a maximum of 250 Unicode characters.|  
|**Help Context ID**|Type the Help context ID associated with this method. It is used to connect to the Help topic for this method, and returned when an exception occurs during invocation of this method.|  
|**Initiation Type**|View the location of the transaction program (TP) making the request. Possible values are:<br /><br /> -   **Windows-initiated** (default)<br />-   **Host-initiated**|  
|**Name**|Type the name of the object. The name can be a maximum of 250 Unicode characters. The name must be different from any other component name in the same project. The default is **Assembly(n)**.|  
|**Version**|Type the version information for the type library or the .NET assembly, expressed in the form of *major.minor*.|  
  
## Remote Environment Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow 32K In/Out**|Select this option if you want TI to treat the input DFHCOMMAREA independently from the output DFHCOMMAREA. TI typically combines the input DFHCOMMAREA and the output DFHCOMMAREA area. The combined areas cannot exceed 32 KB of data. When this option is selected, TI treats the input DFHCOMMAREA independently from the output DFHCOMMAREA. Each input and output area uses up to 32 KB of data. Changing this option affects the currently selected method. Possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**Remote Environment Class**|Select the programming model associated with the remote environment. The available models for the TCP/IP CICS target environment are:<br /><br /> -   **TRM User Data**<br />-   **TRM Link**<br />-   **ELM User Data**<br />-   **ELM Link** (default)<br /><br /> The available models for the LU 6.2 CICS target environment are:<br /><br /> -   **CICS User Data**<br />-   **CICS Link**<br />-   The available models for the TCP/IP IMS target environment are:<br />-   **IMS Connect**<br />-   The only available model for the LU 6.2 IMS target environment is **IMS User Data**.<br /><br /> The only available model for the OS400 target environment is **Distributed Program Call**.|  
  
> [!WARNING]
>  The properties of an object are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Properties (TI Project)](../core/properties-ti-project-2.md)
