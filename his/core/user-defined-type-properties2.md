---
title: "User-Defined Type Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15434"
ms.assetid: 75b7ffe0-1c86-4ae8-9f35-9a0544d3ec46
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# User-Defined Type Properties
Use the **User-Defined Type** properties page to set design and host definition properties on user-defined types (UDTs).  
  
## Design properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Name of the user-defined type (UDT). The name can be a maximum of 250 Unicode characters.|  
  
## Host Definition properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Independent UDT**|Independent user-defined type. An independent user-defined type (UDT) is a UDT that is not referenced by a method (directly or indirectly). When you use TCP/IP, the client sends the host a transaction request message (TRM) or enhanced listener message (ELM) containing the Transaction Program ID, User ID, Password, and other administrative data to be used by the host. The client sends a TRM or ELM reply containing additional administrative data. The data in the TRM or ELM is independent from the actual program data to be exchanged with the Transaction Program on the host.<br /><br /> You can use the independent UDT options and the naming convention of TRMIN, TRMOUT, ELMIN, or ELMOUT to control the data content and format in the TRM or ELM request and TRM or ELM reply. For TRMs or ELMs destined for the host, the name of the UDT must begin with the characters TRMIN or ELMIN. For TRM or ELM replies from the host, the name of the UDT must begin with the characters TRMOUT or ELMOUT. Examples of valid TRM names are: TRMINMyVeryOwn, ELMINStandard, TRMOUTMyVeryOwn, and ELMOUTStandard.<br /><br /> When you begin the UDT with the character TRMIN, TRMOUT, ELMIN, or ELMOUT, Visual Studio automatically formats the first member as an Int or Long and the last members as a String or Array.<br /><br /> After an independent UDT has been defined, it can be referenced by the client application and passed to and from the TI runtime (by using the COMTIContext object) as an optional parameter. The possible values are:<br /><br /> -   **(none)** (default)<br />-   **Length Inclusive**<br />-   **Length Exclusive**|  
|**Member Filler**|User-defined type member filler. Type the number of bytes of FILLER that precedes each row of data sent or received. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side. This option is not available if the length specifier option to include or exclude itself is selected.|  
  
> [!CAUTION]
>  The properties of a component are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Properties (TI Project)](../core/properties-ti-project-2.md)