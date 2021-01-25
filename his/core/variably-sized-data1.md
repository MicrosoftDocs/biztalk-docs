---
description: "Learn more about: Variably Sized Data"
title: "Variably Sized Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48d9719e-de94-4faf-9af1-55d9b75c6cc7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Variably Sized Data
A string or array parameter that is the last parameter in its direction (last of the inputs and in/outs or last of the outputs and in/outs) can be smaller than the maximum size specified, even without an associated actual size. The variable string or array must be a parameter or return value and cannot be contained in a recordset.  
  
 If the final field is an array, it can be an array of any type, including a recordset. If there is an unbounded output recordset, it is the only variably-sized data allowed because Transaction Integrator (TI) cannot handle two pieces of the data stream that are variable in size. If COBOL FILLER exists after the last parameter, that parameter cannot be variable in size.  
  
 Identify the possibility of variably sized data at design time in TI Project. In the Designer select the method whose parameter list contains the final field of string to be of variable size, and set the method property "Variable Sized Final Field" to true.  
  
## See Also  
 [Host and Automation Data](../core/host-and-automation-data1.md)   
 [Sending Binary Data to the Host](../core/sending-binary-data-to-the-host2.md)
