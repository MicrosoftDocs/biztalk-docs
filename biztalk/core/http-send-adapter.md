---
title: "HTTP Send Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e69308b4-421f-4d7c-b9bb-ee086df03272
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Send Adapter
The HTTP send adapter gets messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and sends them to a destination URL on an HTTP POST request. The HTTP send adapter gets the message content from the body part of the BizTalk Message object. The HTTP send adapter ignores all other parts of the BizTalk Message object.  
  
 After the adapter sends the message to a destination URL and the BizTalk Messaging Engine receives the HTTP success status code, the HTTP send adapter deletes the message from the MessageBox database.  
  
 Redirection of HTTP messages is supported and can be configured on the send port.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts the HTTP send adapter as a native BizTalk application. It supports one-way sending of messages as well a solicit-response transmission. The send location for the HTTP send adapter is a distinct URL that you configure through the send port. This unique URL can include query strings appended to the base URL.  
  
## Batching Support for the HTTP Send Adapter  
 The HTTP send adapter does not support batching operations.  
  
## Chunked Encoding Support for the HTTP Send Adapter  
 If the **Enable chunked encoding** configuration option is enabled, then the HTTP send adapter sends request messages using chunked encoding if the request size exceeds 8 KB. If the HTTP proxy server is used, the HTTP send adapter does not use chunked encoding and always stages the data before sending. The **Enable chunked encoding** configuration option is enabled by default.  
  
 When the send adapter receives a response message, it can accept response messages with a chunked encoded body part.  
  
## Client Authentication for the HTTP Send Adapter  
 The HTTP send adapter authenticates with the destination server by using one of the following authentication types:  
  
- **Anonymous.** The HTTP adapter does not send any credentials when connecting to the destination server. If the destination server permits anonymous authentication then the credentials of the configured anonymous account on the destination server are used.  
  
- **Basic.** The HTTP adapter sends the user name and password over an HTTP connection in plain text.  
  
- **Digest.** The HTTP adapter sends passwords in an encrypted format over the HTTP connection.  
  
- **Kerberos.** Neither the user name nor the password is sent over an HTTP connection. The HTTP adapter uses the credentials of the process under which the HTTP send adapter runs for this authentication type.  
  
  Additionally, the HTTP send adapter can provide a client Secure Sockets Layer (SSL) certificate to the Web server if the server requires or accepts it.  
  
## Client Certificates for the HTTP Send Adapter  
 The HTTP send adapter can establish a secure connection with servers that accept or require client certificates. If a client certificate is specified, the HTTP send adapter uses the certificate when connecting with servers that require or accept client certificates. If the client certificate is not specified and the destination server requires client certificates, the HTTP send adapter fails to send the message and follows the standard retry logic.  
  
 The HTTP send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running. The certificate is specified by its thumbprint. If the HTTP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.  
  
## Single Sign-On Support for the HTTP Adapter  
 You can configure Enterprise Single Sign-On (SSO) for use with the HTTP receive location or send port by using BizTalk Administration console. This topic describes how SSO works with the HTTP adapter.  
  
 **Single Sign-On Support for the HTTP Receive Location**  
  
 When an HTTP request is received by Microsoft Internet Information Services (IIS) from a Web client, IIS authenticates the user. The Internet Server Application Programming Interface (ISAPI) extension impersonates the Microsoft Windows user and then calls the SSO credential store to obtain an encrypted ticket. This ticket is stored as the **SSOTicket** property in the context of the message.  
  
 In the pass-through scenario, the BizTalk Messaging Engine directs the message to the MessageBox database. When the adapter receives the message from the MessageBox database, the HTTP adapter calls the **ISSOTicket.RedeemTicket Method** with the encrypted ticket along with the application name to retrieve the back-end credentials from the SSO store. The HTTP adapter then uses the external credentials to connect to the back-end system and process the request. For more information about the affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).  
  
 In the scenario where an orchestration invokes the adapter, the BizTalk Messaging Engine sends this message to the MessageBox database. The orchestration should ensure that both the **SSOTicket** context property and the **Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID** context property of the message that contains the ticket are maintained. When the adapter receives this message from the MessageBox database, the adapter calls **RedeemTicket** with the encrypted ticket to retrieve the back-end credentials from the SSO store. The user designing the schedule should specifically copy this property to the message.  
  
 **Single Sign-On Support for the HTTP Send Adapters**  
  
 If SSO is enabled, when an HTTP send port receives a message with the **Secure** property, it calls the SSO server to validate and redeem the ticket for an affiliate application. The administration application, affiliate administrators, or SSO administrators for the affiliate application can call SSO to redeem a ticket. SSO then decrypts the ticket and obtains the back-end credentials. The pass-through and orchestration scenario are the same as for the HTTP send port.  
  
 By default, SSO is disabled for the HTTP send port. For more information about enabling SSO for the HTTP send port, see [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md).  
  
> [!NOTE]
>  You can only use Single Sign-On with basic and digest authentication.  
  
 To correctly implement Single Sign On support for the HTTP receive and send adapter the following conditions must be met:  
  
-   The same user account must be specified in the following places:  
  
    -   The application pool identity (IIS 7.0) or hosting COM+ application identity for the IIS virtual directory that is monitored by the HTTP receive adapter. For more information about configuring IIS for HTTP receive locations, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
    -   The logon credentials used for the isolated host instance that the HTTP adapter is running in. For information about how to configure the logon credentials for a host instance, see [How to Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md).  
  
-   The isolated host that the HTTP adapter is using must be configured as Authentication Trusted. For information about how to configure a host as Authentication Trusted, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).  
  
## Negative Acknowledgment (NACK) Messages Generated for Failed Transmissions by the HTTP or SOAP Adapter  
 When a message is successfully transmitted, the BizTalk Messaging Engine publishes an associated acknowledgment (ACK) message to the MessageBox if delivery notifications are enabled. Likewise, when a message is suspended by the BizTalk Messaging Engine or an orchestration is suspended by the orchestration engine, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publishes an associated negative acknowledgment (NACK) message to the MessageBox. The NACK message contains context properties and a message body part that consists of a SOAP fault. If the NACK message is generated due to a failed transmission from the HTTP or SOAP adapter, the SOAP fault contains the Headers element and the Body element of the response from the destination Web server. The following is an example of the SOAP fault in a NACK generated for a failed HTTP transmission:  
  
```  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
   <SOAP:Body>  
      <SOAP:Fault>  
         <faultcode>Microsoft BizTalk Server Negative Acknowledgment</faultcode>   
         <faultstring>An error occurred while processing the message, refer to the details section for more information</faultstring>   
         <faultactor>http://localhost/receivestandard.asp</faultactor>   
         <detail>  
            <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
            <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
            <ErrorCode>0x80131600</ErrorCode>  
            <ErrorCategory>0</ErrorCategory>  
            <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
            <ErrorDetail>  
            <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
               <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
               <Body>We could not locate the page you requested. Please check the URL.</Body>  
            </HttpErrorDetail>  
            </ErrorDetail>  
            </ns0:NACK>  
         </detail>  
      </SOAP:Fault>  
   </SOAP:Body>  
</SOAP:Envelope>  
```  
  
> [!NOTE]
>  The Headers element and the Body element are limited to 48 KB. The Headers element is rounded to the nearest complete header value pair without exceeding the limit. The Body element is truncated to 48 KB.  
  
> [!NOTE]
>  NACK and ACK messages are discarded if there are no matching subscriptions for them. NACK and ACK messages are not suspended by the BizTalk Messaging Engine.  
  
 To subscribe to a NACK message, you can do one of the following:  
  
- Create a send port with a filter for the appropriate message context property. See **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for a listing of system message context properties including those related to message acknowledgment.  
  
- Send from an orchestration port marked with **Delivery Notification = Transmitted**. If an orchestration port is marked with **Delivery Notification = Transmitted**, the orchestration will wait until it receives either an ACK or a NACK for the message that was transmitted. If a NACK is generated then it will be routed to the orchestration and the orchestration will throw a DeliveryFailureException. The DeliveryFailureException is deserialized from the SOAP fault that is contained within the NACK message body. To retrieve the exception message string from the SOAP fault that is returned to the orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml from the SOAP Detail section. The following code sample demonstrates how to do this:  
  
  ```  
  // Cast the DeliveryFailureException to a SoapException…  
  System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
  System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
  //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
  //object type created in an Exception handler  
  
  ```  
  
   The code sample above will return an XML fragment similar to the following:  
  
  ```  
  <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
  <ErrorCode>0x80131600</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
  <ErrorDetail>  
  <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
     <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
     <Body>We could not locate the page you requested. Please check the URL.</Body>  
  </HttpErrorDetail>  
  </ErrorDetail>  
  </ns0:NACK>  
  ```  
  
## See Also  
 [HTTP Adapter](../core/http-adapter.md)  
**SSO COM objects** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]