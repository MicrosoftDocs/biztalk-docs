---
description: "Learn more about: Security with the MQSeries adapter"
title: "MQSeries Adapter Security"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security with the MQSeries adapter

MQSeries adapter security begins with securing your BizTalk and MQSeries servers. For information about securing BizTalk Server, see [Secure and protect your data](secure-and-protect-your-biztalk-messages.md). For information about MQSeries Server security, see the IBM MQSeries Server documentation.  
  
> [!NOTE]
>  The adapter automatically uses packet privacy for sending and receiving messages between BizTalk Server and MQSeries Server.  

## Adapter security  
 Using the adapter itself securely requires attention to four areas:  
  
- Choosing the application identity and members for MQSAgent  
  
- Controlling the BizTalk Server accounts using the adapter  
  
- Securing the queue creation scripts  
  
- Making appropriate use of the **SSO Affiliate Application** property  
  
  The account assigned to the application identity during configuration should not be an administrator account. Rather, the account should have the minimum required privileges—read and write access to the MQSeries queues.  
  
  Make sure that you assign only BizTalk Server accounts using the adapter to the MQSAgent role.  
  
  When using exported scripts created during the queue definition process, keep the scripts in a secure area. Only administrators using the scripts should have access.  
  
  If your application uses MQCIH and MQIIH header properties to put user credentials in outbound messages, use the **SSO Affiliate Application** property on the **Transport Properties** page. For more information about this property, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).  
  
## See Also  
 [Structure of the MQSeries Adapter](../core/structure-of-the-mqseries-adapter.md)   
 [What Is the MQSeries Adapter?](../core/what-is-the-mqseries-adapter.md)
