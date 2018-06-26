---
title: "Certificate Wizard Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ff72810-c7b3-4f67-8f9f-e127eacc153e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Certificate Wizard Utility
You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 The source code for the Certificate Wizard can be found in the **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Utilities\Certificate Wizard** folder. With a 64-bit operating system and version of BizTalk Server, it will be in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\SDK\Utilities\Certificate Wizard** folder. To use the Certificate Wizard you will first have to build it using Visual Studio.  
  
 CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store. When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.  
  
 **Syntax Description**  
  
 The following table describes each part of the syntax that the CertWizard utility uses.  
  
|||  
|-|-|  
|Syntax|Description|  
|Privatekey|Used to import a private key.|  
|Publickey|Used to import a public key.|  
|Rootkey|Used to import a root key—from a certification authority.|  
|filename.pfx (or .cer)|Full path for the .pfx (private keys) or .cer (public keys) file.|  
|Filepassword|The password required to unlock the .pfx file.|  
|Useridentity|A service identity that one or more BizTalk Hosts uses. Enter a user account if you do not want to specify the host, but want to import a certificate under a user account. **Note:**  If you do not add the Useridentity switch, the utility imports and set the certificate for all users. **Note:**  If you add the Useridentity switch, but do not enter a value, WMI automatically generates the user identity.|  
|Password|The password for the service identity user.|  
|Thumbprint|The thumbprint of a specific certificate, in case the file contains more than one certificate. **Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file. For a private certificate file, the utility prompts you to select the certificate to import.|  
|Usage|The intended usage of the imported private certificate. Can be one of the following:<br /><br /> **sign** (for a signing certificate)<br /><br /> **decrypt** (for a decryption certificate)<br /><br /> **both** (for a certificate that is both a signing certificate and a decryption certificate)<br /><br /> **none** (also for a certificate that is both a signing certificate and a decryption certificate). **Note:**  If you set the /Usage switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.|  
|Exportable|Can be **True** or **False**. If **True**, the private key can be re-exported.|  
  
 **Syntax for Importing a Private Key**  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
 **Syntax for Importing a Public Key**  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
 **Syntax for Importing a Root Key**  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
- You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To run the certificate wizard  
  
1. Open a command prompt.  
  
2. Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities.  
  
3. At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press **Enter**.  
  
   > [!NOTE]
   >  If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.  
  
## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)