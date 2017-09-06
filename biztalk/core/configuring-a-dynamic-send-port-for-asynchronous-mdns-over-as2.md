---
title: "Configuring a Dynamic Send Port for Asynchronous MDNs over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72646c90-89db-4884-824b-6921bb824f8d
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Dynamic Send Port for Asynchronous MDNs over AS2
To send an asynchronous EDIINT/AS2-encoded MDN message over HTTP/HTTPS, create a dynamic HTTP send port with the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port Type|Dynamic One-Way|  
|**Send Port Properties: General**|Send pipeline|AS2Send|  
|**Send Port Properties: Filters**|Property|EdiIntAS.IsAS2AsynchronousMdn|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|True|  
  
 An asynchronous MDN should be sent to the address contained in the **Receipt-Delivery-Option** header of the received AS2 message. A dynamic send port will do so, whereas a static send port will send the message to the **Destination URL** in the send port definition. The exception to this is if the **Use agreement settings for validation and MDN instead of message header** property is set in **Validation** page of the one-way agreement tab of the **Agreement Properties** dialog box. In that case, the send port will send the MDN message to the URL entered into the **Receipt-Delivery-Option** agreement property. However, the send port used to do so must still be a dynamic send port, not a static send port.  
  
 You can configure this send port to return both MDNs and EDI acknowledgments. In the instance, if an EDIINT/AS2-encoded message is transported over HTTP/HTTPS successfully, but processing of the EDI-encoded payload fails, the sender of the original message would receive both an MDN indicating successful AS2 processing and an EDI acknowledgment indicating a failure in EDI processing. The EDI-encoded payload would be suspended and an error posted.  
  
## Functionality  
 The send port and pipeline must do the following to send an MDN:  
  
-   Pick up the MDN by filtering on the `EdiIntAS.IsAS2AsynchronousMdn==True` property.  
  
-   Build an AS2 message. For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
-   Route the MDN to the address in the **Receipt-Delivery-Option** line in the header of the message.  
  
    > [!NOTE]
    >  If the **Use agreement settings for validation and MDN instead of message header** property is set in **Validation** page of the one-way agreement tab of the **Agreement Properties** dialog box, the send port will send the MDN message to the URL entered into the **Receipt-Delivery-Option** agreement property, not to the address mentioned in **Receipt-Delivery-Option** header of the received AS2 message.  
  
## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)