---
title: "Security Tab for SNA (Remote Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15219"
ms.assetid: 81c135ea-c13a-4e6e-b639-16f0b0d55320
caps.latest.revision: 3
robots: noindex,nofollow
---
# Security Tab for SNA (Remote Environment Properties)
Use the **Security** tab to set the security properties of the remote environment for SNA.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Single Sign-on**|Select this option to require that the TI run-time environment uses Single Sign-on (SSO). Clear this option to allow TI to communicate with the mainframe region without setting user ID and password information.|  
|**Affiliate application**|Select the SSO affiliate application to be queried for credentials. The list displays all the affiliate applications defined in the SSO. The display name of the affiliate application is a concatenation of the affiliate application name and description, separated by a hyphen.|  
|**COM+ Single Sign-on mapping use:**|Identifies the source of the host user ID and password. **Important:**  This setting is for COM+ applications only. If you are using .NET applications, the credentials used by the TI runtime are the same credentials set on the IIS virtual directory where the .NET objects are stored. You can set or change the .NET credentials by using the "identity" element in the file web.config.|  
|**User credentials**|Select this option to have the TI run-time environment obtain the user ID and password information associated with the user logon in which the client application is executing. **Caution:**  For the COM server to impersonate the security credentials of the client application, the client application must grant the COM server permission to impersonate it.|  
|**COM+ application credentials**|Select this option to have the TI run-time environment obtain the user ID and password information as defined for a component's COM+ application. To administer this security information, use Component Services (COM+) in Windows Server. This setting is ignored when a TI component is deployed in a COM+ application which itself is configured as a Library application (instead of a Server application) on the Activation tab of the COM+ application property sheet. A Library application runs using the Windows user credentials of the process that invoked it, and TI attempts to map this name to a corresponding host user name.|  
|**Allow application to override selected authentication**|Select this option to enable the TI run-time environment to use the application override mechanism for obtaining user ID and password information. The client application must be written to support the TI security override mechanism. Clear this option to base the user ID and password solely on previously selected user or package credentials. This security option can be applied to a TI component deployed in a Library COM+ or ASP.NET application or in a Server COM+ or ASP.NET application.<br /><br /> This option appears only if **Enable Single Sign-on** is selected.|  
|**Require client provided security**|Select this option to require the client to provide the security credentials, either by using the client context or by making call-back security available.<br /><br /> This option appears only if **Enable Single Sign-on** is cleared.|  
|**Use already verified or persistent verification authentication**|Select this option to have the TI run-time environment use "Already Verified," "Persistent Verification" or "No authentication," depending on the configuration of the mainframe region. "Already Verified" sends only the user ID and no password. "Persistent Verification" sends a user ID and password on the first transaction from the given user and only the user ID thereafter. "No authentication" neither sends a user ID nor a password. The host configuration controls the actual authentication to be used when this option is enabled. In a CICS region, for example, these settings correspond to the ATTACHSEC options Identify, Persistent, and None, respectively. This security option can be applied to a TI component deployed in a Library application or in a Server application. This security option can be applied to a TI component deployed in a Library COM+ application or in a Server COM+ application.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [How To Impersonate Client Application Security Credentials &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/23535123-2e13-4e15-82c6-662eec3bd893)   
 [Remote Environments Node](../core/remote-environments-node.md)   
 [Remote Environment Node](../core/remote-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)