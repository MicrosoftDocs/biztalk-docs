---
title: "How to Configure SSL for the MQSC Adapter: Non-Transactional1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b29cee4c-445f-4196-8681-eacf308fc833
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure SSL for the MQSC Adapter: Non-Transactional
This topic lists the steps to configure the MQSeries Client (MQSC) adapter to execute non-transactional requests to the MQSeries server using SSL. These steps describe configuration for one-way (Server) authentication.  
  
 Configuration is performed in the following steps:  
  
- Configure the Queue Manager and the client computer.  
  
- Add SSL to the configuration.  
  
- Configure the MQSC adapter.  
  
  The IBM WebSphere MQ documentation provides more information.  
  
## Configure the Queue Manager and the Client  
 The following steps create a new Queue Manager. These steps can also be applied to existing Queue Managers.  
  
#### To set up the Queue Manager and the Client  
  
1. Create a Queue Manager named **QM1**. Define a listener on the required port.  
  
2. Define a SVRCONN channel TO.QM1.  
  
3. Create a local queue on the MQSeries server Queue Manager named TESTQUEUE. This is used for testing the client connections from the MQSC adapter.  
  
4. Test the connection by running amqsputc.exe on your client computer: **amqsputc.exe TESTQUEUE.*QManagerName***.  
  
   > [!IMPORTANT]
   >  This syntax is case-sensitive. Be sure to enter the correct case.  
  
## Add SSL to the configuration  
 The following steps add an SSL certificate to your MQ configuration.  
  
#### To add SSL to the configuration  
  
1.  Add the certificate to the Queue Manager’s store. On Windows, use Internet Explorer/the MQSeries user interface or amqmcert. On UNIX, use gsk6ikm or gsk6cmd.  
  
     The format of the label for CA Signer certificates is not important. However, personal certificates for WebSphere MQ queue manager must adhere to the following lowercase format: **ibmwebspheremqqueuemanagername**.  
  
2.  Modify the SVRCONN channel so the SSLCIPH is set. For example, set it to NULL_MD5. Set SSLCAUTH to OPTIONAL.  
  
    > [!NOTE]
    >  SSLCAUTH is required for two-way authentication (client/server).  
  
3.  **Optional**. On the Windows client computer, the CA certificates can be installed in the system key store, which can be done in Internet Explorer.  
  
4.  Set the following environment variable to specify the location and name of the client key store: **set MQSSLKEYR=C:\sslclient\ssl\key**.  
  
    > [!NOTE]
    >  The key store **must** have the .sto file name extension and the environment variable **must not** specify it.  
  
5.  Set up a client key store:  
  
    1.  If you added the required CA certificates to the system store, return a list of the certificates: **amqmcert -l -k ca**. Note the number(s) of the required CA certificate(s)  
  
    2.  Add the certificates to the client store: **amqmcert -a (certificate_number)**, where *(certificate_number)* is the number of each required certificate.  
  
6.  Test the SSL Client connections using the amqsputc sample program with the test queue you created previously.  
  
## Configure the MQSC adapter  
 When the MQSeries Client – to – MQSeries Queue Manager SSL request succeeds, the adapter can be configured on both receive locations and send ports to use SSL over non-transactional requests. Refer to the following links:  
  
 [How to Configure a Receive Port and a Receive Location for the MQSC Adapter](../core/how-to-configure-a-receive-port-and-a-receive-location-for-the-mqsc-adapter2.md)  
  
 [How to Configure a Send Port for the MQSC Adapter](../core/how-to-configure-a-send-port-for-the-mqsc-adapter2.md)  
  
 The property values that are used in the test must also be specified in the adapter configuration. The adapter properties are relevant to send ports **and** receive locations:  
  
|Property|Description|  
|--------------|-----------------|  
|**SSL Cipher Specification**|Defines a single CipherSpec for an SSL connection that is used by the endpoint configured in the adapter. Both ends of a WebSphere MQ SSL channel definition must include the attribute. The value specified should match the name that is specified on the server-end of the channel. The value is a string with a maximum length of 32 characters.  For example, enter  NULL_MD5.|  
|**SSL Key Repository location**|The location and name of the client key store. For example, enter C:\sslclient\ssl\key.|  
|**SSL Peer Name**|**Normally left blank** is used to check the distinguished name (also known as DN) of the certificate from the peer queue manager or client at the other end of a WebSphere MQ channel. If the distinguished name received from the peer does not match this value, the channel does not start.  The SSL Peer Name is only required if **Authentication of parties initiating connections** is enabled on the MQ server channel **and** if the **Accept only certificates with Distinguished Names** option is enabled. Verify through the MQ explorer or check with your MQSeries Administrator.|  
  
## See Also  
 [How to Configure SSL for the MQSC Adapter: Transactional](../core/how-to-configure-ssl-for-the-mqsc-adapter-transactional2.md)   
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)