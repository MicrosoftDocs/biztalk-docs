---
title: "HTTP Receive Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9008833c-5a02-4fb4-a43e-09ca28a21eff
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Receive Adapter
The receive location for the HTTP receive adapter is a distinct URL configured through the BizTalk Server Administration console.  
  
 You can configure the HTTP receive adapter for either asynchronous submission or synchronous submission from the client. Asynchronous submissions are one-way submissions and synchronous submissions are two way or request-response submissions.  
  
 You use IIS security for authentication and authorization of incoming requests.  
  
## HTTP GET and HTTP POST Requests  
 The HTTP receive adapter can receive messages in two different ways—by an HTTP POST request or an HTTP GET request.  
  
 When an HTTP receive adapter gets messages on an HTTP POST request, the following sequence of events occurs:  
  
1. The URL configured in BizTalk Server receives a new message on the receive location.  
  
2. The receive adapter creates a BizTalk Message object so that the message can be submitted to the server.  
  
3. The receive adapter creates the BizTalk Message object with only one part—the body part.  
  
4. After the message has been read and successfully submitted to the server, the HTTP receive adapter sends an HTTP code 202 back to the client indicating that the request was accepted.  
  
    Optionally, the HTTP receive adapter can send a message correlation token on the HTTP response. This correlation token represents the message within BizTalk Server. If the HTTP receive location is in a request-response port, the adapter returns success code 200 along with the response message.  
  
   When an HTTP receive adapter processes messages from an HTTP GET request, the receive adapter creates a BizTalk Message object and puts the decoded query string of the HTTP GET request into the BizTalk message body part. The HTTP adapter selects the query string that is placed into the BizTalk message body part using the following algorithm:  
  
-   If the HTTP receive adapter receives an HTTP GET request, it splits the incoming URI string into two parts, using the question mark (?) symbol as a delimiter.  
  
-   The first part of the URI string, the part before the question mark delimiter, is copied into the **InboundTransportLocation** property on the message context. The **InboundTransportLocation** property uniquely identifies the location where BizTalk Server received the message. The engine uses this property to determine which receive location to run for the message.  
  
-   The HTTP adapter takes the rest of the URI string, the part after the question mark delimiter, and decodes and copies it into the BizTalk message body part.  
  
-   If an empty HTTP GET or HTTP POST operation is received by the HTTP receive adapter, it is rejected.  
  
## HTTP Receive Adapter Processing of a GET Request  
 The following are examples of how the HTTP receive adapter processes messages received by HTTP GET requests. These examples assume that the HTTP receive adapter is configured with the following two receive locations:  
  
```  
/vroot/BTSHTTPReceive.dll  
/vroot/BTSHTTPReceive.dll?LocationID=1  
```  
  
1.  Given the following HTTP GET request for the client:  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1  
    ```  
  
     The action taken by the HTTP receive adapter is as follows:  
  
     Set the **InboundTransportLocation** property on the message context equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1.  
  
2.  Given the following HTTP GET request for the client:  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1&MyParam=My%20Value  
    ```  
  
     The action taken by the HTTP receive adapter is as follows:  
  
     Set the **InboundTransportLocation** property equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1&MyParam=My Value.  
  
3.  Given the following HTTP GET request for the client:  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll  
    ```  
  
     The action taken by the HTTP receive adapter is+ as follows:  
  
     Reject the request due to incorrect formatting of the HTTP GET request.  
  
## Batching Support for the HTTP Receive Adapter  
 The HTTP receive adapter submits messages to the server in batches. The size of the batch used to submit messages to the server can be configured on the HTTP adapter receive handler.  
  
## HTTP Receive Adapter Support for Suspending Failed Requests  
 The BizTalk Server HTTP receive adapter has a configuration setting, **Suspend Failed Requests**, to control what happens with an HTTP request if it fails inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure. The setting has two possible values:  
  
-   **False.** This is the default setting. The HTTP receive adapter discards messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure. Additionally, an error status code 401 or 500 is sent to the client. 
  
-   **True.** The HTTP receive adapter suspends messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure. For one-way receive ports an **Accepted** status code 202 is sent to the client. For two-way receive ports an **Error** status code 500 is sent to the client.  
  
## Chunked Encoding Support for the HTTP Receive Adapter  
 The HTTP receive adapter accepts HTTP requests with chunked encoded body messages. The receive adapter uses chunked encoding to send response messages when the body size is larger than 4 KB. Chunked encoding can be turned off by setting the DWORD registry entry described in [HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md)  
  
## Client Certificates for the HTTP Receive Adapter  
 Whenever a secure connection with a client certificate is used for the HTTP receive location, the HTTP receive adapter obtains the client certificate thumbprint from Microsoft Internet Information Services (IIS) and adds it to the message context of all messages that were received over HTTPS on that location. The HTTP receive adapter sets the following system properties:  
  
```  
SourcePartyEvidenceQualifier = "Certificate"  
SourcePartyEvidence = <certificate thumbprint>  
```  
  
## Status Codes Returned by the HTTP Receive Adapter  
 The following list contains status codes returned by the HTTP receive adapter.  
  
-   **200 OK.** The adapter successfully processed the request message and generated a response. The adapter returns this status code on the HTTP response from the HTTP request-response port.  
  
-   **202 Message Accepted.** The adapter successfully submitted the message into the server or a one-way request is suspended. The adapter returns this status code on the HTTP response from a one way HTTP receive port.  
  
-   **401 Access Denied.** The HTTP request is received on an authentication-required receive port and the security check for that message failed. For example, the party was not resolved or the message was not decrypted.  
  
-   **500 Internal Server Error.** A general failure to process the HTTP request. The message is not suspended by BizTalk Server unless the configuration setting **Suspend Failed Requests** is set to **True** for a two-way receive port.  
  
## See Also  
 [HTTP Adapter](../core/http-adapter.md)