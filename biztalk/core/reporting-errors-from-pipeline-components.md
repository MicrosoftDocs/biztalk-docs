---
title: "Reporting Errors from Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IErrorInfo object"
  - "pipeline components [custom], errors"
  - "SetErrorInfo method"
  - "Exception object"
ms.assetid: ad7c519e-829a-4a92-a42f-3e367d5dbaa8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reporting Errors from Pipeline Components
Pipeline components report errors in two ways:  
  
-   For .NET-based components, by throwing an exception.  
  
-   For COM-based components, by setting the **ErrorInfo** object and returning a failure HRESULT.  
  
## Reporting errors from .NET pipeline components  
 To report an error, a .NET-based pipeline component needs to throw an exception where it reports the error description. To report the name of the component that throws an error, set the **Source** property of the **Exception** object.  
  
 The Messaging Engine uses the **Message** and **Source** properties of the **Exception** object to report an error. The following message is written to the event log:  
  
 "There was a failure executing the [receive&#124;send] pipeline: \<pipeline name\> Source: \<Source\> [Receive Location&#124;Send Port:] \<location&#124;port name\> Reason: \<Message\>."  
  
## Reporting errors from COM pipeline components  
 To report an error, COM-based pipeline components perform the following actions:  
  
1. The pipeline component sets the **IErrorInfo** object by calling the **SetErrorInfo** method.  
  
2. The pipeline component returns a failed HRESULT to the Messaging Engine.  
  
   The Messaging Engine uses the **GetSource** and **GetDescription** properties of the **IErrorInfo** object to report an error. If the source is not set, the name of the component is used. If the description is not set or the whole **ErrorInfo** object is not set, the returned HRESULT is reported instead of the description. The following message is written to the event log:  
  
   "There was a failure executing the [receive&#124;send] pipeline: \<pipeline name\> Source: \<GetSource\> [Receive Location&#124;Send Port:] \<location&#124;port name\> Reason: \<GetDescription or HRESULT\>."  
  
## See Also  
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)