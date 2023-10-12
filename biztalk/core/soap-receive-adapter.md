---
description: "Learn more about: SOAP Receive Adapter"
title: "SOAP Receive Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SOAP Receive Adapter
You use the SOAP receive adapter to receive Web service requests. The SOAP receive adapter creates a BizTalk Message object, and promotes the associated properties to the message context.  
  
 A SOAP receive adapter URI must correlate to one or more BizTalk orchestrations or schemas that have been published as a web service with the **BizTalk Web Services Publishing Wizard**. The published web service exposes one or more web methods which correlate to one or more BizTalk Server orchestrations or schemas in a BizTalk assembly. In effect, the published web service acts as a server proxy for the BizTalk orchestration(s) or schema(s) and forwards requests and responses between the client and the BizTalk orchestration(s) or schema(s). For more information about publishing BizTalk orchestrations or schemas as web services see [Publishing Web Services](../core/publishing-web-services.md).  
  
 A receive location that uses the SOAP adapter can be configured as one-way or request response (two way). When a one-way receive location is configured to use the SOAP adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns the status of the request to the client. When a request response (two way) receive location is configured to use the SOAP Adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns a response document to the client. For more information about request response messaging see [Request-Response Messaging](../core/request-response-messaging.md).  
  
## See Also  
 [What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md)   
 [SOAP Adapter Security Recommendations](../core/soap-adapter-security-recommendations.md)
