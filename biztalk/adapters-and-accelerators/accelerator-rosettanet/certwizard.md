---
title: "CertWizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, CertWizard utility"
  - "CertWizard utility"
  - "certificates, importing"
ms.assetid: beeab3c0-d7b1-4bb9-8b19-f79b049d5aa1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CertWizard
You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].  
  
## Location in SDK  
 \<*drive*\>\Program Files (x86)\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\  
  
## Running CertWizard  
  
#### To run CertWizard  
  
1. Open a command prompt.  
  
2. Move to \<*drive*\>\ Program Files (x86)\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
3. At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press ENTER.  
  
## Syntax for CertWizard  
 The following shows the syntax that you use to start this command-line utility:  
  
### Syntax for Importing a Private Key  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
### Syntax for Importing a Public Key  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### Syntax for Importing a Root Key  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### Syntax Description  
 The following table describes each part of the syntax that the CertWizard utility uses.  
  
|**Syntax**|**Description**|  
|----------------|---------------------|  
|**Privatekey**|Used to import a private key.|  
|**Publickey**|Used to import a public key.|  
|**Rootkey**|Used to import a root key—from a certification authority.|  
|**filename.pfx (or .cer)**|Full path for the .pfx (private keys) or .cer (public keys) file.|  
|**Filepassword**|The password required to unlock the .pfx file.|  
|**Useridentity**|A service identity that one or more BizTalk Hosts uses. Enter a user account if you do not want to specify the host, but want to import a certificate under a user account. **Note:**  If you do not add the **Useridentity** switch, the utility imports and set the certificate for all users. **Note:**  If you add the **Useridentity** switch, but do not enter a value, WMI automatically generates the user identity.|  
|**Password**|The password for the service identity user.|  
|**Thumbprint**|The thumbprint of a specific certificate, in case the file contains more than one certificate. **Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file. For a private certificate file, the utility prompts you to select the certificate to import.|  
|**Usage**|The intended usage of the imported private certificate. Can be sign (for a signing certificate), decrypt (for a decryption certificate), both (for a certificate that is both a signing certificate and a decryption certificate), or none (also for a certificate that is both a signing certificate and a decryption certificate). **Note:**  If you set the **/Usage** switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.|  
|**Exportable**|Can be `True` or `False`. If `True`, the private key can be re-exported.|  
  
## Remarks  
 CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store. When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.  
  
 If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [Importing Certificates Using the CertWizard Utility](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)
