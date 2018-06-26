---
title: "Parameter Requirements1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd2e2c14-e570-484f-aa4d-da68a212fdea
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Parameter Requirements
Requirements for the In, In/Out, and Out parameters might affect how you define a Transaction Integrator (TI) component or mainframe transaction program (TP). The In and In/Out parameters are sent to the mainframe-based TP from the TI Automation server. The Out and In/Out parameters are sent from the mainframe-based TP to the TI Automation server.  
  
## Best Parameter Order  
 The way parameters are ordered with regard to inputs and outputs determines the amount of data that must be transmitted, as well as the structure of the mainframe program. If you are creating a Transaction Integrator (TI) component in TI Project without importing COBOL code from a mainframe transaction program, place the parameters in the following order to minimize the amount of data transmitted:  
  
- Input parameters  
  
- Input/output parameters  
  
- Output parameters  
  
  However, if you are using a CICS LINK LU 6.2, TCP TRM Link, or TCP ELM Link remote environment (RE) and importing COBOL data declarations into TI Project from an existing mainframe program, place the parameters in the order they appear in the COBOL data structure. In such a case, although the parameters are contained within the COMMAREA data structure, only the part of the COMMAREA containing the last input or input/output parameter is sent to the mainframe. The mainframe program is not affected by this ordering, but less data will be transmitted, especially in the case of small amounts of input data.  
  
## Maximum Amount of Parameter Data  
 The remote environment (RE) you use can affect the maximum possible message size. Programs associated with the CICS LINK LU 6.2, TCP TRM Link, or TCP ELM Link REs are limited by the maximum size of the COMMAREA (32,767 bytes). Therefore, the total byte size of all parameters cannot exceed 32 KB. Programs associated with distributed program call (DPC) are limited to a maximum of 65,500 bytes of user data. This maximum decreases as additional parameters are defined. DPC is limited to a maximum of 35 parameters.  
  
 The IMS Using LU 6.2 and CICS Using LU 6.2 REs have message size restrictions that, if exceeded, affect the programming logic in the mainframe program. Therefore, be careful not to exceed the limit if you use either of these REs.