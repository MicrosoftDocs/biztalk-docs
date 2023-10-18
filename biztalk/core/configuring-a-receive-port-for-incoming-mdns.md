---
description: "Learn more about: Configuring a Receive Port for Incoming MDNs"
title: "Configuring a Receive Port for Incoming MDNs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring a Receive Port for Incoming MDNs
To receive an AS2 MDN, create a one-way HTTP receive port to receive the message and return a response back to the party.  
  
 A two-way request-response receive port that is used to receive AS2 messages should not be used to receive MDN messages. Using a request-response receive port for an MDN would prevent a 200OK message from being returned in response to the incoming MDN, thereby causing unnecessary retries of the MDN transmission.  
  
 You can use either the AS2Receive or the AS2EdiReceive pipeline to process a received MDN. However, if you use AS2EdiReceive, you cannot route the MDN into the MessageBox by setting the **Process inbound MDN into MessageBox for routing/delivery options** property on the **Acknowledgements** page of the one-way agreement tab. Trying to do so will result in an EDI error because the MSN will be passed to the EDI Decoder, which cannot process an MDN. If the MDN is not sent to the MessageBox, the AS2Decoder will consume the MDN, so it will not be passed to the EDI Decoder.  
  
 Create the receive port with the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Receive Port Properties: General**|Port type|One-Way|  
|**Receive Location Properties: General**|Transport Type|HTTP<br /><br /> **Note** Only the HTTP adapter can be used for transporting MDNs, which are EDIINT/AS2-encoded messages. This transport will not work with an adapter other than the HTTP adapter.|  
|**Receive Location Properties: General**|Receive handler|BizTalkServerIsolatedHost|  
|**Receive Location Properties: General**|Receive pipeline|AS2Receive or AS2EdiReceive|  
|**HTTP Transport Properties**|Virtual directory plus ISAPI extension|/\<name of virtual directory\>/BTSHTTPReceive.dll|  
  
## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)
