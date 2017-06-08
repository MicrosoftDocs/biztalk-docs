---
title: "Host Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.host.properties"
ms.assetid: 2241f922-3a90-429e-91cb-72f972dee70b
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Host Properties Dialog Box
Use the **Host Properties** window to view the common properties of the selected send handler.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the name of the host. You name the host when you create it.|  
|**Type**|Displays the host type. You can enlist an orchestration to an In-process host, and an In-process host can host a send handler. An Isolated host operates outside the BizTalk Server installation.|  
|**Options - Allow Host Tracking**|Select this check box to indicate that the host loads the BizTalk Tracking component to process health monitoring and business data. If you select this check box, the current host will have read/write privileges to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access privileges to these databases. If you clear the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database.|  
|**Options - Authentication Trusted**|Select this check box to specify that BizTalk should trust this host.|  
|**Options - 32-bit only**|Select this check box if you want the host instance process to be created as 32-bit on both 32-bit and 64-bit servers. If this check box is cleared, the host instance process will be created as 32-bit on 32-bit servers and as 64-bit on 64-bit servers.|  
|**Options - Make this the default host in the group**|Select this check box to identify this host as the default host. The orchestration enlistment process automatically uses the default host to host the orchestration, unless you explicitly select a different host. If this check box is selected and unavailable, this host is the default.|  
|**Windows group**|Type the local or domain group for the host. Members of the Windows group will have permissions to run instances of this host.|  
  
## Certificates Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Decryption certificate - Common Name**|Displays the common name of the displayed decryption certificate.|  
|**Decryption certificate - Thumbprint**|Displays the thumbprint of the private key certificate used to decrypt inbound messages for this host. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number 0 to 9 or a letter A to F).|  
|**Decryption certificate - Remove certificate**|Click to remove the displayed decryption certificate from the host.|  
|**Decryption certificate - Browse**|Click to display the **Select Certificate** dialog box, where you select the decryption certificate from the Personal store that you want to use with the host.|  
  
## See Also  
 [Hosts](../core/hosts.md)   
 [Host Groups](../core/host-groups.md)   
 [Host Instances](../core/host-instances.md)   
 [How to Create a New Host](../core/how-to-create-a-new-host.md)   
 [How to Delete a Host](../core/how-to-delete-a-host.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)