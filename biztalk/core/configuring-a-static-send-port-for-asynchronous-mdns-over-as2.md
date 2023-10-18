---
description: "Learn more about: Configuring a Static Send Port for Asynchronous MDNs over AS2"
title: "Configuring a Static Send Port for Asynchronous MDNs over AS2"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring a Static Send Port for Asynchronous MDNs over AS2
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send an asynchronous EDIINT/AS2-encoded MDN message over a static send port. This configuration includes creating the static send port and if required, setting up an encryption certificate to be used by the send port.  
  
> [!NOTE]
>  You can configure a dynamic send port to send MDN messages, instead of a static send port. For more information, see [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).  
  
 To send an MDN message, create a one-way HTTP send port with the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port Type|Static One-way Send Port|  
|**Send Port Properties: General**|Transport Type|HTTP **Note:**  Only the HTTP adapter can be used for transporting EDIINT/AS2-encoded messages. This transport will not work with an adapter other than the HTTP adapter.|  
|**Send Port Properties: General**|Send handler|BizTalkServerApplication|  
|**Send Port Properties: General**|Send pipeline|AS2Send|  
|**HTTP Transport Properties**|Destination URL|\<Destination URL string\>|  
|**HTTP Transport Properties**|Enable chunked encoding|Cleared|  
|**Send Port Properties: Filters**|Property|EdiIntAS.IsAS2AsynchronousMdn **Note:**  You should also specify additional filter expressions to ensure that only MDN messages destined to the address specified in this send port are picked up by this subscription filter.|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|True|  
|**Send Port Properties: Certificates**|Common Name  and thumbprint|Enter the certificate name and thumbprint if using an encryption certificate for the outbound MDN message.|  
  
 An asynchronous MDN should be sent to the address specified in the **Receipt-Delivery-Option** header of the received AS2 message. A dynamic send port will do so automatically, whereas a static send port will send the message to the **Destination URL** in the send port properties. When sending an asynchronous MDN with a static send port, ensure that the URL you are sending to is correct.  
  
## Functionality  
 The send port and pipeline must do the following to send an MDN:  
  
-   Pick up the MDN by filtering on the `EdiIntAS.IsAS2AsynchronousMdn==True` property.  
  
-   Build an AS2 message. For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
-   Route the MDN to the address defined in the send port.  
  
## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)
