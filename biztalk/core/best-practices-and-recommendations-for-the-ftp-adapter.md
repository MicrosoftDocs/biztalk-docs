---
title: "Best practices and recommendations for the FTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, FTP adapters"
  - "FTP adapters, best practices"
ms.assetid: f73b2016-d48c-48d8-9ba0-96e26b694d1e
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best practices and recommendations for the FTP Adapter
Read about the best practices, security recommendations, and enhancements for the FTP adapter.

## Best practices  
  
-   Delete partially received files from the temporary folder on a regular basis to keep files from using computer resources and potentially disrupting service.  
  
-   When working with a streaming server, deny read access to the new file until the MessageBox database receives the entire file. If a partial file is submitted to the MessageBox database by the FTP adapter, the MessageBox database will successfully store the message, but the FTP adapter will not be able to delete the partial message from the receive location.  
  
-   To ensure high availability for the FTP adapter receive handler, the FTP adapter receive handler should be configured to run in a clustered BizTalk Host instance. For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  

## Security recommendations and tips

BizTalk Server can receive files from a File Transfer Protocol (FTP) server and send files to an FTP server for other applications. BizTalk Server does not act as an FTP server.  
  
 FTP is, by nature, not secure: The user name, password, and other credentials traverse the network in clear text. Likewise, files uploaded or downloaded move across in clear text and can be easily viewed or tampered with along the way. Moreover, an attacker could spoof the FTP server itself, known as a rogue server attack. In this case you cannot tell if a particular FTP server is indeed the computer that you intended to communicate with.  
  
 To overcome these problems, the FTP adapter supports the SSL/TLS protocol that ensures data confidentiality through encryption.  
  
 For general security considerations when you use the FTP protocol, see the [Internet FAQ Archives](http://go.microsoft.com/fwlink/p/?LinkId=24779) (http://go.microsoft.com/fwlink/p/?LinkId=24779).   
  
 We recommend that you use the following guidelines for securing and deploying the FTP adapter in your environment:  

- Secure your server and limit access to the data. Since the FTP protocol is not a secure protocol, it will always be vulnerable. You can ensure that the FTP server is secure by using a dedicated connection, and limiting the server and the connection between BizTalk Server and the FTP host. You can also set the security policies of the FTP server to allow for secure connections with the FTP client.  

- Configure the FTP adapter to use Secure Sockets Layer (SSL) protocol for the communication between the adapter and the FTP server. SSL protocol ensures data confidentiality through encryption. This means that user IDs and passwords are encrypted and not sent as plain text. With the FTP adapter, you also have a choice to encrypt the data channel of the FTP connection. See **Enhancements** (in this topic).
  
-   To achieve secure file transfer, configure the SSL-specific properties provided by the FTP adapter. See **Enhancements** (in this topic). 
  
-   The FTP adapter supports FTP Request for Comments (RFC) 959. See the [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?LinkId=24781) (http://go.microsoft.com/fwlink/p/?LinkId=24781). The FTP adapter does not support the Secure FTP (SFTP) protocol. See the [SFTP adapter](../core/sftp-adapter.md).
  
-   You can use the FTP adapter across firewalls. Depending on the type of firewall you use, you may have to configure one or more of the following firewall properties: username, password, computer, port, firewall type (none, socks 4, socks 5), and mode.  
  
-   We recommend you place the remote FTP server in a secure location. You must ensure the physical and network security of this server to minimize rogue server attacks.  
  
-   The FTP adapter supports the use of Enterprise Single Sign-On (SSO). See [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md).  
  
-   By default, the FTP receive adapter must have write permissions in the FTP server because the adapter deletes the file from the server after download. However, the FTP adapter supports downloading of files from read-only locations. See **Enhancements** (in this topic).
  
- When using an FTP send port, you must specify and store a user ID and password combination when configuring the send port. The adapter uses this information to connect to the FTP server. The user credentials are stored in a SQL Server database in plain text. In a dynamic send port, credentials are sent to the FTP server. If production environment requirements warrant stronger security, use anonymous credentials to the server.  
  
-   When the system prompts you for an account, we recommend that you enter an existing user account, and not the local system account. This enables you to implement better security, and allows the adapter to run in unattended mode, without logging on.  

## Enhancements

### Transferring data to and from a secure FTP server  
 The FTP adapter supports file transfers from an FTPS server over Secure Sockets Layer (SSL)/Transport Level Security (TLS). SSL/TLS ensures data confidentiality through encryption. You must enable the secure mode by configuring SSL-specific properties provided by the adapter. Because the adapter allows for both reading and writing data from a secure FTP server, the SSL-specific properties are available when configuring send handlers/ports and also with receive handlers/locations.  

Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], the FTP adapter no longer requires the SYST command: 

- **FTP Server Type** property – Set this property to use a server that doesn't require the SYST command.
   
  The following options are available for configuring the SSL-specific properties:  

- **Use SSL** property – Set this property so that FTP adapter must use SSL for each transfer session.  
  
- **Enable Data Protection** property – Set this property to turn on data encryption. The security policies of the FTPS server must allow for secure SSL connections with the adapter in order for this setting to work.  
  
- **FTPS Connection Mode** property – Set this property to determine when security is activated:  
  
  -   In **Implicit** mode, security is automatically turned on as soon as the adapter connects to the server.  
  
  -   In **Explicit** mode, the adapter sends a command to initiate a secure control channel.  
  
> [!NOTE]
>  The FTP adapter does not support revocation checks on the server certificates.  
  
### Support for downloading files from locations marked as read-only  
The FTP adapter supports download of files from read-only file locations. The adapter now maintains a list of downloaded files in a database. For the next download, the list of files on the FTP server is compared to the list of files maintained by the adapter, and only new files on the server are downloaded. To support scenarios where an existing file is updated between two downloads, you can configure the adapter to also check file timestamps by setting the **Enable Timestamp Comparison** property for the FTP receive location. In such cases, even if the file name is same but the timestamp is updated, the adapter downloads the file.  
  
 Sometimes the FTP server does not support associating a modified timestamp with a file. In such cases, the adapter enables you to specify an interval after which the file will be downloaded again. You configure this interval by setting the **Redownload Interval** property for the FTP receive location.  
  
 The following table lists the expected behavior of the FTP adapter for different values set for the **Delete After Download**, **Enable Timestamp Comparison** and **Redownload Interval** properties.  
  
|Delete After Download|Enable Timestamp Comparison|Redownload Interval|Adapter Behavior|  
|---|---|---|---|  
|Yes|Not applicable|Not applicable|The adapter deletes a file from the FTP server after downloading it. This is the default behavior of the adapter.|  
|No|Yes|Not applicable|The adapter does not delete a file from the FTP server after downloading it. Instead the adapter compares the file’s last modified timestamp using the MDTM command. Depending on the timestamp, the adapter downloads the file again.|  
|No|No|Applicable|The FTP adapter downloads a file from the FTP server after the interval you specify, irrespective of whether the file has been modified or not.|  
  
### Support for atomic file transfer in ASCII mode  
 The FTP adapter supports atomic file transfer for ASCII mode. To enable atomic file transfer for ASCII mode, the adapter uses the **Temporary Folder** property. This property defines a temporary location on the FTP server where the file is first moved to. After the file is completely transferred to the temporary location, the file is then moved to the relevant location on the FTP server. Here, the assumption is that the file transfer is atomic between the temporary location and the relevant location on the FTP server.  
  
> [!NOTE]
>  The extension of using temporary folder to ASCII file is applicable only for the **Send**, and does not apply to **Receive**. The primary reason for implementing this feature is that, a third party application will not read a file until it is fully written. In the case of BizTalk receiving the file, the adapter will submit the file to BizTalk only after it is completely read.  
  
> [!NOTE]
>  In binary mode, the **Temporary Folder** property can also be used to resume file transfer if there is a failure in between. This is not applicable for ASCII mode. For ASCII mode, the **Temporary Folder** property is only used for atomic file transfer.  
  
 
## Next 
[Configuring the FTP Adapter](../core/configuring-the-ftp-adapter.md)  

## See Also  
 [Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)
