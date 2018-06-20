---
title: "SOAP Send Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d65218d-516b-4e45-a824-272ef6ef298c
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Send Adapter
You use the SOAP send adapter to call a Web service. The SOAP send adapter reads the message context on the BizTalk Message object to get the proxy name and calls the associated external Web service proxy.  
  
## Client Authentication for the SOAP Send Adapter  
 The SOAP send adapter authenticates with the destination server by using one of the following authentication types:  
  
- **Anonymous.** The default setting.  
  
- **Basic.** The SOAP connection sends the user name and password in plain text.  
  
- **Digest.** The SOAP connection sends the user name and password in an encrypted format.  
  
- **Kerberos or NTLM.** Neither the user name nor the password is sent over a SOAP connection. The SOAP adapter always uses the credentials of the process under which the SOAP send adapter runs for this authentication type.  
  
  Additionally, the SOAP send adapter can provide a client Secure Sockets Layer (SSL) certificate to the Web server if the server requires or accepts it.  
  
  If you enabled Enterprise Single Sign-On (SSO), when the SOAP send adapter receives a message with the request to the **SSOTicket** property, the adapter connects to an SSO server to validate and redeem the ticket. After the SOAP adapter validates the ticket, it is decrypted and the credentials for the affiliate system are retrieved from the credential store. The SOAP adapter then uses the credentials to connect to the affiliate system, and the SOAP request is processed.  
  
## Client Certificates for the SOAP Send Adapter  
 The SOAP send adapter can establish a secure connection with servers that accept or require client certificates. If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates. If you do not specify a client certificate and the destination server requires client certificates, the SOAP send adapter fails to send the message and follows the standard retry logic.  
  
 The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running. The SOAP adapter specifies the certificate by its thumbprint. If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.  
  
## Negative Acknowledgement (NACK) Messages Generated for Failed Transmissions by the HTTP or SOAP Adapters  
 When a message is successfully transmitted, the BizTalk Messaging Engine publishes an associated Acknowledgement (ACK) message to the MessageBox database if delivery notifications are enabled. Likewise, when a message is suspended by the BizTalk Messaging Engine or an orchestration is suspended by the orchestration engine, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publishes an associated Negative Acknowledgement (NACK) message to the MessageBox. The NACK message contains context properties and a message body part consisting of a SOAP fault. If the NACK message is generated due to a failed transmission from the HTTP or SOAP adapters, the SOAP fault contains the **Headers** element and the **Body** element of the response from the destination Web server. The following is an example of the SOAP fault in a NACK generated for a failed SOAP transmission:  
  
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
>  The **Headers** element and the **Body** element are limited to 48 KB. The **Headers** element is rounded to the nearest complete header value pair without exceeding the limit. The **Body** element is truncated to 48 KB.  
  
> [!NOTE]
>  NACK and ACK messages are discarded if there are no matching subscriptions for them. NACK and ACK messages are not suspended by the Messaging Engine.  
  
 To subscribe to a NACK message, you can do one of the following:  
  
1. Create a send port with a filter for the appropriate message context property. See **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for a listing of system message context properties including those related to message acknowledgment.  
  
2. Send from an orchestration port marked with **Delivery Notification = Transmitted**. If an orchestration port is marked with **Delivery Notification = Transmitted**, the orchestration will wait until it receives either an ACK or a NACK for the message that was transmitted. If a NACK is generated then it will be routed to the orchestration and the orchestration will throw a DeliveryFailureException. The DeliveryFailureException is deserialized from the SOAP fault that is contained within the NACK message body. To retrieve the exception message string from the SOAP fault that is returned to the orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml from the SOAP Detail section. The following code sample demonstrates how to do this:  
  
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
 [What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md)   
 [SOAP Adapter Security Recommendations](../core/soap-adapter-security-recommendations.md)