---
description: "Learn more about: Variant Data Type"
title: "Variant Data Type1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Variant Data Type
The type of each element in a message is fixed and defined by the information in the component library. Because mainframe programs do not support the Variant data type, you must fix the type of each parameter at design time in Transaction Integrator (TI) Project. Microsoft Visual Basic Scripting Edition (VBScript), which is often used to create Active Server Pages (ASP) in Web-based applications, supports only the Variant data type. It does not accept declared variables. As a result, if your COM+ client application calls a TI Automation server and passes parameters with Variant data types, the TI run-time environment forces each Variant data type into the type for each parameter as defined in the TI component library.  
  
 The Variant data type is not supported in Visual Basic .NET. Visual Basic .NET supports defining data types as objects, and then casting the objects as data types. TI does not support variables defined as objects cast to data types. All method parameters must be defined initially as data types, not objects.  
  
## See Also  
 [Data Types](../core/data-types2.md)
