---
title: "Item Options Wizard Page2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15407"
ms.assetid: 1533ad6a-2de6-430f-8752-3094a751fb4c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Item Options Wizard Page
Use the **Item Options** wizard page to specify the type of component to create. Select and identify the type of component to be created.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Type of item**|View the group of component types:<br /><br /> -   **Method**<br />-   **Recordset**<br />-   **User-defined type**|  
|**Select or type the name of the item to import**|View the identifying information for the new component.|  
|**Name**|Select or type the name of the component. The name can be a maximum of 250 Unicode characters.|  
|**Use Link programming model**|Type the name of an executable program that, running under the host environment (HE), will be linked to by this method and passed a COMMAREA. This option is available only for Link models. The name can be a maximum of 8 Unicode characters. This option is displayed only for host-initiated processing (HIP).|  
|**Exclude LL, ZZ, and TRANCODE fields**|Select to exclude the LL, ZZ, and TRANCODE fields from the transaction if the host environment is IMS. This option is available only for HIP server components.|  
|**Link-to-Program**|The name of an executable running under the host environment that will be linked to by this method and passed a COMMAREA. The name can be a maximum of 8 Unicode characters. This option is available only for Windows-initiated processing (WIP) Link server components.|  
|**Source TP Name**|The name of the mirror transaction identifier, which parses the distributed program link (DPL) header and identifies the link-to-program name. The name can be a maximum of 4 Unicode characters. This option is available only for WIP Link server components.|  
  
## See Also  
 [DFHCOMMAREA Wizard Page](../core/dfhcommarea-wizard-page1.md)   
 [Import COBOL Wizard](../core/import-cobol-wizard2.md)