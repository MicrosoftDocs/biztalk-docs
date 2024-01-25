---
description: "Learn more about: XML Validation Stage (Recoverable Interchange Processing)"
title: "XML Validation Stage (Recoverable Interchange Processing)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# XML Validation Stage (Recoverable Interchange Processing)
The **XML validator** pipeline component processes an interchange in two modes:  
  
-   **Standard mode**. When the **XML validator** component is configured to perform standard validation, the messages contained in an interchange are validated in a transactional unit of work. Specifically, if validation of a message in the interchange fails, the entire interchange (containing all the messages) is placed in the suspended queue.  
  
-   **Recoverable mode**. When the **XML validator** component is configured to perform recoverable interchange processing, if validation of a message fails, the message is placed in the suspended queue and the **XML validator** component continues to validate remaining messages in the interchange.  
  
## Configure recoverable interchange processing  
  
1. Open a receive pipeline by using pipeline designer in Visual Studio.  
  
2. Drag **XML validator** component from the **Toolbox** to the **Validate** stage of the receive pipeline.  
  
3. In the Properties window, set the value of the **Recoverable Interchange Processing** property to **True** if you want the **XML validator** component to process interchanges in the recoverable mode, or set the property to **False** if you want the component to process interchanges in the standard mode. The default value of this property is `False`.  
  
   The **XMLValidator** class in the object model, which corresponds to the **XML validator** pipeline component, has a public property named **RecoverableInterchangeProcessing** that you can use to get/set the mode programmatically. See documentation for [Microsoft.BizTalk.Component.XmlValidator](/dotnet/api/microsoft.biztalk.component.xmlvalidator) class for more information.  
  
   Messages that are successfully validated have their sending party identified according to the party configured for the receive port on which the parent interchange arrived. If party resolution for any message extracted from the interchange fails, then the party resolution is considered to have failed for the entire interchange.  
  
## See Also  
 [How to Configure the XML Validator Pipeline Component](../core/how-to-configure-the-xml-validator-pipeline-component.md)
