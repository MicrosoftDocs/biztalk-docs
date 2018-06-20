---
title: "CreateSNAService1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c30c1c24-6a3b-4be7-8680-d411bce924e4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CreateSNAService
The **CreateSNAService** function creates the necessary entries for an instance in the **Services** registry tree. This function adds particular values that are necessary for the service as well as all the subkeys under the service key, including **Parameters** and **ExtraParameters**.  
  
## Parameters  
 *Argument 0*  
 Name of the service to be created.  
  
 *Argument 1*  
 Type of SNA Service (*SNAServiceType* variable).  
  
 *Argument 2*  
 Image path of this component (*ImagePath* variable).  
  
 *Argument 3*  
 Dependency list (*ProductDepends* variable).  
  
 *Argument 4*  
 Parameter list (*ProductParams* variable).  
  
 *Argument 5*  
 Extra parameter list (*ProductExtraParams* variable).  
  
 *Argument 6*  
 Event Log message file.  
  
 *Argument 7*  
 Event types supported (usually 0x07).  
  
## Return Values  
 *Return 0*  
 Status of the operation:  
  
- STATUS_SUCCESSFUL: Operation succeeded.  
  
- STATUS_FAILED: Operation failed.  
  
  *Return 1*  
  Handle to the service key.  
  
  *Return 2*  
  Handle to the **Parameters** key under the service key.  
  
  *Return 3*  
  Handle to the **ExtraParameters** key under the **Parameters** key.