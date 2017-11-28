---
title: "Step 1: Creating a Certification Authority | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, creating"
  - "double action tutorial, creating certificates"
  - "creating, certificates"
ms.assetid: b6ecd534-6b03-4336-8337-33ec18a0802a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Creating a Certification Authority
In this topic, you install the Certificate Services [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] component. You use it to generate the certificates that you need to promote secure communication between the Contoso and Fabrikam organizations. Each trading partner will have a private encryption certificate for communication and a private signature certificate for identification purposes. Additionally, the partners will share their public key certificates with each other to promote secure communication when implementing the 3A2 Partner Interface Process (PIP).  
  
### To install the certificate server  
  
1.  Click **Start**, point to **Settings**, and then click **Control Panel**. Double-click **Add or Remove Programs**.  
  
2.  In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.  
  
3.  On the **Windows Components Wizard** page, in the **Components** section, select **Certificate Services**, click **Yes**, and then click **Next** to start the Configuring Components Wizard.  
  
    > [!NOTE]
    >  If the **Certificates ServicesWindows** component is already selected, skip the rest of this procedure.  
  
4.  On the **CA Type** page, make sure that **Stand-alone root CA** is selected, and then click **Next**.  
  
5.  On the **CA Identifying Information** page, in the **Common name for this CA** box, type **Contoso-FabrikamCA**, and then click **Next**.  
  
6.  On the **Certificate Database Settings** page, leave the defaults, and then click **Next**.  
  
7.  Click **Yes** when the wizard prompts you to stop Internet Information Services (IIS).  
  
8.  Click **Yes** if the **Configuring Components Wizard** prompts you to enable Active Server Pages.  
  
9. Click **Finish** to close the **Windows Components Wizard**.  
  
    > [!NOTE]
    >  You only have to use one computer as the Certification Authority. You do not have to repeat this step on the second computer. This tutorial uses the Contoso computer as the Certification Authority.  
  
### To install a root Certification Authority (CA) for Windows Server 2008  
  
1.  Open Server Manager, click **Add Roles** in Roles, click **Next**, and click **Active Directory Certificate** Services check box. Click **Next** twice.  
  
2.  On the Select Role Services page, click **Certification Authority and Certification Authority Web Enrollment**. Click **Next**.  
  
3.  On the Specify Setup Type page, click **Standalone**. Click **Next**.  
  
4.  On the Specify CA Type page, click Root CA. Click **Next**.  
  
5.  On the Set Up Private Key page, click Create a new private key. Click **Next**.  
  
6.  On the Configure Cryptography for CA page. Click **Next**.  
  
7.  On Configure CA Name, in the Common name for this CA box, type Contoso-FabrikamCA, and then click **Next**.  
  
8.  On the Set Validity Period page, click **Next**.  
  
9. On the Configure Certificate Database page, Click **Next**.  
  
10. On the Confirm Installation Options page, click **Install**.  
  
### Configuring the Web site for the CA to use HTTPS authentication  
  
1.  On the computer you used as the Certification Authority, click Start, point to All Programs, point to Administrative Tools, and then click Internet Information Services (IIS) Manager.  
  
2.  In the Internet Information Services (IIS) Manager dialog box, right click **Default Web Site and select Edit Bindings…** from the popup menu.  
  
3.  In Site Bindings dialog box click **Add**.  
  
4.  In Add Site Binding dialog box select **https** in Type drop down, select the certificate from **SSL certificate** drop down and click **OK**.  
  
5.  Click **Close** to close the Site Bindings… dialog box.  
  
### To download the CA certificate  
  
1.  In Internet Explorer, locate and open http://<contoso_computername>/certsrv/Default.asp.  
  
2.  On the Default.asp page, click **Download a CA certificate, certificate chain, or CRL**.  
  
3.  Make sure that **Current[Contoso-FabrikamCA]** is selected in the **CA Certificate** list, and then click **Download CA Certificate**.  
  
4.  Save the certificate to C:\Certs\Contoso-FabrikamCA.cer on both the Contoso and the Fabrikam computer.  
  
### To import the CA certificate to the Trusted Root Certification Authorities store  
  
1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  At the command prompt, move to **\<drive\>:\Program Files\MicrosoftBizTalk \<version\> Accelerator for RosettaNet\SDK**, and then press **Enter**.  
  
3.  At the command prompt, type **CertWizard /Rootkey "\<drive\>:\Certs\Contoso-FabrikamCA.cer"**, and then press **Enter**.  
  
    > [!IMPORTANT]
    >  Perform this procedure on both the Contoso and Fabrikam computers.  
  
### To enable automatic certificate issuing  
  
1.  On the computer you used as the Certification Authority, click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Certification Authority**.  
  
2.  In the Certification Authority dialog box, right-click **Contoso-FabrikamCA**, and then click **Properties**.  
  
3.  In the Contoso-FabrikamCA Properties dialog box, on the **Policy Module** tab, click **Properties**.  
  
4.  In the Properties dialog box, select **Follow the settings in the certificate template**, and then click **OK**.  
  
5.  Click **OK** to close the Contoso-FabrikamCA dialog box.  
  
6.  Close the Certification Authority dialog box.  
  
    > [!NOTE]
    >  By enabling automatic certificate issuing, Certificate Services automates the certificate issuing procedure. You will have to restart Certificate Services to apply this change.  
    >   
    >  You may need to install the Root Certificate Contoso-FabrikamCA.cer in the Current User\Trusted Root Certification authorities.  
  
## See Also  
 [Step 2: Creating Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)