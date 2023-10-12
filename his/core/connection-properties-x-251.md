---
description: "Learn more about: Connection Properties: X.25"
title: "Connection Properties: X.251"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_PU_X25"
---
# Connection Properties: X.25
The following tabs are available on the X.25 Connection Properties sheet:  
  
## Connection Properties: Address  
 **Remote X.25 Address**  
 Select the type of virtual circuit used by the connection.  
  
 **Switched Virtual Circuit Address**  
 Enter the Switched Virtual Circuit Address of the host.  
  
 **Permanent Virtual Circuit Alias**  
 Enter the Permanent Virtual Circuit Alias of the host. This is a number that identifies the channel: 1 for the first channel, 2 for the second, and so on. The default is **1**.  
  
 **Affiliate Application**  
 If you selected Single Sign-On, choose an Affiliate Application from the list. The Enterprise Single Sign-On (SSO) Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using SSO. An affiliate application can represent a back-end system such as a mainframe or UNIX computer. It can also represent an application such as SAP, or a subdivision of the system, such as the "Benefits" or "Pay stub" sub-systems.  
  
## Connection Properties: X.25  
 **Max BTU Length**  
 Specify the Maximum Basic Transmission Unit (BTU) Length.  
  
 The range is from 265 through 16393; the default is **265**.  
  
 With an IBM SDLC adapter, set the Max BTU Length to 521 or less.  
  
 This is the maximum number of bytes that can be transmitted in a single data-link information frame. A BTU is sometimes called an I-frame.  
  
 For downstream connections, specify a Max BTU Length less than or equal to the maximum value supported by software on the downstream system.  
  
 For host connections, specify a Max BTU Length less than or equal to the VTAM PU definition for the MAXDATA= parameter.  
  
 **Facility Data**  
 For an SVC channel, specify the codes for any Facility Data required by your network provider or by the administrator of the remote system. You can specify as many as 126 Hexadecimal characters (63 Hexadecimal bytes).  
  
 **User Data**  
 For an SVC channel, specify the codes for any User Data required by your network provider. Type an even number of hexadecimal characters of 32 characters or fewer.  
  
 **Packet Size**  
 For a PVC channel, select the maximum number of data bytes (not header bytes) to be sent in a frame. Obtain this value from your network provider.  
  
 **Window Size**  
 For a PVC channel, select the maximum number of frames that the local system can send without receiving a response from the remote system. Obtain this value from the administrator of the remote host or peer system.  
  
 **Connection Retry Limits**  
 Supply activation limits for the connection:  
  
 **Maximum Retries**  
 Select the number of attempts for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to make when trying to establish the connection. After making this number of attempts, Host Integration Server makes an entry in the event log and stops trying. The range is from 1 through No Limit; the default is **No Limit**.  
  
 **Delay After Failure**  
 Select the length of time for Host Integration Server to wait between attempts to establish the connection. The range is from 5 seconds through 255 seconds; the default is **10** seconds.  
  
## See Also  
 [X.25 Connection Parameters](./x-25-connection-parameters2.md)   
 [SNA Manager Help](../core/sna-manager-help1.md)
