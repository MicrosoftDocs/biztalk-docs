---
description: "Learn more about: Writing Code that Specifies a Remote Environment"
title: "Writing Code that Specifies a Remote Environment1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28e4b1e3-4ce4-4621-a54a-621a6f5e8e29
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Writing Code that Specifies a Remote Environment
Applications can set the `SelectionHint` property to specify a remote environment (RE) programmatically. By specifying the RE, the application identifies the CICS or IMS region where transaction programs are carried out when the Transaction Integrator (TI) run-time environment handles calls to the TI component's methods.  
  
 The following Visual Basic code demonstrates how to set the `SelectionHint` property:  
  
```  
Dim objExample As Object  
Dim Store As String  
Set objExample = CreateObject("MyComponent.MyInterface")  
Open "My REList.txt" for Input as #1  
Line Input #1, strRE  
Close #1  
  
objExample.SelectionHint = strRE  
RtrnVal = objExample.method1(parm1,  , parmN) 'Use RE named "MyRemEnvName"  
  
```  
  
 This example shows how the application can explicitly instruct the TI run-time environment to use the RE named `MyRemEnvName` when handling the call to `method1`. In this example, `MyRemEnvName` is the first string in the file MyREList.txt. Any method calls made after `method1` that follow the `SelectionHint` assignment are handled using the original RE that was assigned to the component, not the new one. In other words, the programmatic override of the default RE does not continue past a single method call.  
  
 If an application attempts to set the `SelectionHint` property to a string that does not correspond to the name of an RE, an error is reported, and the original RE is used.  
  
 The `SelectionHint` property can be set to a deactivated RE. However, the next method call to the object will fail because a deactivated RE was selected.  
  
 The `SelectionHint` property is optional. If the `SelectionHint` property does not specify an RE, the TI run-time environment uses the original RE.  
  
## See Also  
 [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property2.md)
