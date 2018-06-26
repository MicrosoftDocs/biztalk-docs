---
title: "How to Configure SSL for the MQSC Adapter: Transactional2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ee1d8d1-61b6-4480-b7a1-93f20f6f4891
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure SSL for the MQSC Adapter: Transactional
This topic lists the steps to configure the MQSeries Client (MQSC) adapter to execute transactional requests to the MQSeries server using SSL. These steps describe configuration for one-way (Server) authentication.  
  
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
  
3. Define a CLNTCONN channel TO.QM1. Use the same name used for the SRVCONN channel.  
  
4. Create a local queue on the MQSeries server Queue Manager named TESTQUEUE. This is used for testing the client connections from the MQSC adapter.  
  
5. Copy the AMQCLCHL.TAB file from the MQSeries server onto the client computer. On most UNIX installations, this file is in \var\mqm\qmgrs\\*QueueManagerName*\\@IPCC. On most Windows installations, this file is in \Program Files\\*Websphere MQ Server installation folder*\qmgrs\\*QueueManagerName*\\@IPCC.  
  
6. On the client computer, set the following environment variables:  
  
   -   `MQCHLLIB=C:\sslclient\ssl\` where MQCHLLIB is the path of the client channel table.  
  
   -   `MQCHLTAB=AMQCLCHL.TAB` where MQCHLTAB is the name of the client channel table.  
  
   > [!NOTE]
   >  The environment variables’ default values can also be used. Refer the WebSphere MQ Client manual for more information.  
  
7. Test the connection by running amqsputc.exe on your client computer: **amqsputc.exe TESTQUEUE.*QManagerName***.  
  
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
  
3.  Modify the CLNTCONN channel so the SSLCIPH is set to the same as the SVRCONN channel. For example, set it to NULL_MD5.  
  
4.  Copy the new AMQCLCHL.TAB file from the MQSeries server to the client computer. This step allows the SSL settings to be used.  
  
5.  **Optional**. On the Windows client computer, the CA certificates can be installed in the system key store, which can be done in Internet Explorer.  
  
6.  Set the following environment variable to specify the location and name of the client key store: **set MQSSLKEYR=C:\sslclient\ssl\key**.  
  
    > [!NOTE]
    >  The key store **must** have the .sto file name extension  and the environment variable **must not** specify it.  
  
7.  Set up a client key store:  
  
    1.  If you added the required CA certificates to the system store, return a list of the certificates: **amqmcert -l -k ca**. Note the number(s) of the required CA certificate(s).  
  
    2.  Add the certificates to the client store: **amqmcert -a (certificate_number)**, where *(certificate_number)* is the number of each required certificate.  
  
8.  Test the SSL Client connections using the amqsputc sample program with the test queue you created previously.  
  
    > [!IMPORTANT]
    >  Do not enter the Channel name, Connection name, SSL Cipher Specification, SSL Key Repository Location, or the SSL Peer Name. This information is from the AMQCLCHL.TAB file.  
  
## Configure the MQSC adapter  
 When the MQSeries Client - to - MQSeries Queue Manager SSL request succeeds, the adapter can be configured on both receive locations and send ports to use SSL and Transactions. Refer to the following links:  
  
 [How to Configure a Receive Port and a Receive Location for the MQSC Adapter](../core/how-to-configure-a-receive-port-and-a-receive-location-for-the-mqsc-adapter2.md)  
  
 [How to Configure a Send Port for the MQSC Adapter](../core/how-to-configure-a-send-port-for-the-mqsc-adapter2.md)  
  
## See Also  
 [How to Configure SSL for the MQSC Adapter: Non-Transactional](../core/how-to-configure-ssl-for-the-mqsc-adapter-non-transactional1.md)   
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)