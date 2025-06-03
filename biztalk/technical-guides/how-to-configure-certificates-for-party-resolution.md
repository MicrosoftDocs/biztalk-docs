---
description: "Learn more about: How to Configure Certificates for Party Resolution"
title: "How to Configure Certificates for Party Resolution"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure Certificates for Party Resolution
When you use BizTalk Explorer to configure a party, you can configure the party so that the party is resolved by using its digital signature. If you configure the party this way, when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it will use the public key certificate to determine who sent the message, and to resolve the sender to a known party in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure party resolution to use a certificate  
  
1.  Open the **Party Properties** dialog box.  
  
2.  Click the **Certificate** tab, and then click **Browse**.  
  
3.  Select a certificate.  
  
4.  Click **OK**.
