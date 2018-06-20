---
title: "Step 3: Importing Public and Private Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "public certificates"
  - "importing certificates"
  - "private certificates"
  - "double action tutorial, importing certificates"
  - "certificates, importing"
ms.assetid: 955bdd69-9fbc-4100-ab8a-8f5dd4a17cbb
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Importing Public and Private Certificates
In this step, you import the certificates you created in [Step 2: Creating Public and Private Certificates &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) to the Contoso and Fabrikam computers. Each computer imports its own private certificates and imports the public certificates of the other organization.  
  
> [!NOTE]
>  You have to transfer the Fabrikam private certificates and Contoso public certificates to the Fabrikam computer to import them. This step assumes that you put these certificates in the C:\Certs folder on the Fabrikam computer.  
  
### To import the Contoso private certificates on the Contoso computer  
  
1. On the Contoso computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, move to **\<**<em>drive</em>**\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.  
  
3. At the command prompt, type **CertWizard /Privatekey "\<**<em>drive</em>**\>:\Certs\Contoso Private Encryption.pfx"**, and then press **Enter**.  
  
4. At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.  
  
5. At the **Enter password for identity <contoso_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.  
  
   > [!NOTE]
   >  If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.  
  
6. At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.  
  
    The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.  
  
7. Repeat steps 3-6 for the Contoso Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt noted in step 6.  
  
### To import the Fabrikam public certificates on the Contoso computer  
  
1.  On the Contoso computer, click **Start**, click **Run,** type **cmd**, and then click **OK**.  
  
2.  At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.  
  
3.  At the command prompt, type **CertWizard /Publickey "***\<drive\>***:\Certs\Fabrikam Public Encryption.cer"**, and then press **Enter**.  
  
4.  Repeat step 3 for the Fabrikam Public Signature.cer certificate.  
  
### To import the Fabrikam private certificates on the Fabrikam computer  
  
1.  Copy the following files from the Contoso computer to the \<drive\>:\Certs folder on the Fabrikam computer: Contoso Public Encryption.cer, Contoso Public Signature.cer, Fabrikam Private Encryption.pfx, and Fabrikam Private Signature.pfx.  
  
2.  On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
3.  At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.  
  
4.  At the command prompt, type **CertWizard /Privatekey "***\<drive\>***:\Certs\Fabrikam Private Encryption.pfx"**, and then press **Enter**.  
  
5.  At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.  
  
6.  At the **Enter password for identity <fabrikam_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.  
  
    > [!NOTE]
    >  If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.  
  
7.  At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.  
  
     The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.  
  
8.  Repeat steps 4-7 for the Fabrikam Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt in step 6.  
  
### To import the Contoso public certificates on the Fabrikam computer  
  
1.  On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.  
  
3.  At the command prompt, type **CertWizard /Publickey "***\<drive\>***:\Certs\Contoso Public Encryption.cer"**, and then press **Enter**.  
  
4.  Repeat step 3 for the Contoso Public Signature.cer certificate.  
  
## See Also  
 [Step 4: Enabling Secure Sockets Layer in IIS](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)