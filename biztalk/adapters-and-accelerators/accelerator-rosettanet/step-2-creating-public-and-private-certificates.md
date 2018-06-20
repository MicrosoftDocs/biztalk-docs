---
title: "Step 2: Creating Public and Private Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, creating certificates"
  - "public certificates"
  - "certificates, public certificates"
  - "creating, certificates"
  - "private certificates"
ms.assetid: 0a925d89-03d9-41fe-907b-85a6ae42362a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Creating Public and Private Certificates
In this step, you use the Certification Authority created in [Step 1: Creating a Certification Authority &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md) to generate the public and private certificates that the Contoso and Fabrikam organizations use.  

### To generate the Contoso and Fabrikam encryption certificates  

1. On the computer you used as the Certification Authority, in Internet Explorer, locate and open http://<contoso_computername>/certsrv.  

2. On the **Welcome** page, click **Request a certificate**.  

3. On the **Request a Certificate** page, click **advanced certificate request**.  

4. On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.  

5. On the **Advanced Certificate Request** page, do the following:  


   |            Use this            |                                                                         To do this                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **Name**            |                                                               Type **Fabrikam Encryption**.                                                                |
   |           **E-Mail**           |                                                          Type <strong>jdoe@fabrikam.com</strong>.                                                          |
   |          **Company**           |                                                                     Type **Fabrikam**.                                                                     |
   |         **Department**         |                                                                       Type **Test**.                                                                       |
   |            **City**            |                                                                       Type **Test**.                                                                       |
   |           **State**            |                                                                       Type **Test**.                                                                       |
   |       **Country/Region**       |                                                                        Type **US**.                                                                        |
   | **Type of Certificate Needed** |                                             Select **E-Mail Protection Certificate** from the drop down list.                                              |
   |         **Key Usage**          |                                                              Select the **Exchange** option.                                                               |
   |   **Additional Key Options**   | Place a check in the following options:<br /><br /> -   **Mark keys as exportable**<br />-   **Store certificate in the local computer certificate store** |
   |       **Friendly Name**        |                                                               Type **Fabrikam Encryption**.                                                                |


6. Click **Submit**, and then click **Yes** in **Web Access Confirmation** dialog box.  

7. On the **Certificate Issued** page, click **Install this certificate**.  

8. Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Encryption**.  

### To generate the Contoso and Fabrikam Signing Certificates  

1. In Internet Explorer, locate and open http://<contoso_computername>/certsrv.  

2. On the **Welcome** page, click **Request a certificate**.  

3. On the **Request a Certificate** page, click **advanced certificate request**.  

4. On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.  

5. On the **Advanced Certificate Request** page, do the following:  


   |            Use this            |                                                                         To do this                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **Name**            |                                                                Type **Fabrikam Signature**.                                                                |
   |           **E-Mail**           |                                                          Type <strong>jdoe@fabrikam.com</strong>.                                                          |
   |          **Company**           |                                                                     Type **Fabrikam**.                                                                     |
   |         **Department**         |                                                                       Type **Test**.                                                                       |
   |            **City**            |                                                                       Type **Test**.                                                                       |
   |           **State**            |                                                                       Type **Test**.                                                                       |
   |       **Country/Region**       |                                                                        Type **US**.                                                                        |
   | **Type of Certificate Needed** |                                             Select **E-Mail Protection Certificate**.from the drop down list.                                              |
   |         **Key Usage**          |                                                              Select the **Signature** option.                                                              |
   |   **Additional Key Options**   | Place a check in the following options:<br /><br /> -   **Mark keys as exportable**<br />-   **Store certificate in the local computer certificate store** |
   |       **Friendly Name**        |                                                                Type **Fabrikam Signature**.                                                                |


6. Click **Submit**, and then click **Yes** when asked to request the certificate.  

7. On the **Certificate Issued** page, click **Install this certificate**.  

8. Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Signature**.  

### To generate private certificates for the Encryption and Signature certificates  

1.  Click **Start**, click **Run**, type **MMC**, and then click **OK**.  

2.  In the Console1 window, on the **File** menu, click **Add/Remove Snap-in**.  

3.  In the Add/Remove Snap-in dialog box, on the **Standalone** tab, click **Add**.  

4.  In the Add Standalone Snap-in dialog box, select the **Certificates** snap-in from the **Available Standalone Snap-ins** list, and then click **Add**.  

5.  In the Certificates snap-in dialog box, select **My user account**, and then click **Next**.  

6.  In the Select Computer dialog box, click **Finish**.  

7.  In the Add Standalone Snap-in dialog box, click **Close**.  

8.  In the Add/Remove Snap-in dialog box, click **OK**.  

9. In the Console1 window, expand **Certificates (Local Computer)**, expand **Personal**, and then click **Certificates**.  

10. In the right pane, right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.  

11. On the **Welcome to the Certificate Export Wizard** page, click **Next**.  

12. On the **Export Private Key** page, select **Yes, export the private key**, and then click **Next**.  

13. On the **Export File Format** page, make sure that **Personal Information Exchange** is the only option selected, and then click **Next**.  

14. On the **Password** page, in the **Password** and **Confirm Password** boxes, type **mysecret**, and then click **Next**.  

15. On the **File To Export** page, click **Browse**.  

16. In the **Save As** dialog box, save the certificate using the file path *\<drive\>*:\Certs\Fabrikam Private Encryption.pfx.  

17. On the **File to Export** page, click **Next**.  

18. On the **Completing the Certificate Export Wizard** page, click **Finish**.  

19. In the Certificate Export Wizard popup indicating a successful export, click **OK**.  

20. Repeat steps 10-19 for the Fabrikam Signature certificate using the file name Fabrikam Private Signature.pfx.  

21. Repeat steps 10-19 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Private Signature.pfx and Contoso Private Encryption.pfx, respectively.  

### To generate public certificates for the Encryption and Signature certificates  

1.  In the Console1 window, expand **Certificates – Current User**, expand **Personal**, and then click **Certificates**.  

2.  Right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.  

3.  On the **Welcome to the Certificate Export Wizard** page, click **Next**.  

4.  On the **Export Private Key** page, select **No, do not export the private key**, and then click **Next**.  

5.  On the **Export File Format** page, click **Next**.  

6.  On the **File To Export** page, click **Browse**.  

7.  In the Save As dialog box, enter **\<drive\>:\Certs** for **Save in**, **Fabrikam Public Encryption.cer** as **File name**, and **\*.cer** for **Save as type**, and then click **Save**.  

8.  On the **File to Export** page, click **Next**.  

9. On the **Completing the Certificate Export Wizard** page, click **Finish**.  

10. In the Certificate Export Wizard popup indicating a successful export, click **OK**.  

11. Repeat steps 1-9 for the Fabrikam Signature certificate using the file name Fabrikam Public Signature.cer.  

12. Repeat steps 1-9 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Public Signature.cer and Contoso Public Encryption.cer, respectively.  

## See Also  
 [Step 3: Importing Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)