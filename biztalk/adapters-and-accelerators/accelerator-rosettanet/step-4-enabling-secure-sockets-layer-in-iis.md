---
title: "Step 4: Enabling Secure Sockets Layer in IIS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Secure Socket Layers"
  - "IIS"
  - "double action tutorial, enabling SSL in IIS"
  - "SSL"
ms.assetid: 96109294-595a-46ac-974e-33123df79ed5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Enabling Secure Sockets Layer in IIS
Secure Sockets Layer (SSL) is a protocol designed to secure the communication channel between a client and a server. By enabling SSL in Microsoft® Internet Information Services (IIS) 7.5/7.0, the Contoso and Fabrikam organizations communicate using authentication and encryption for all data transfers. In this step, you learn how to enable SSL in IIS 7.5/7.0.  
  
> [!NOTE]
>  You have to perform this step on both the Contoso and Fabrikam computers.  
  
### To prepare a new server certificate  
  
1. Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. In the Internet Information Services left pane, expand **\<**<em>computer_name</em>**\>** (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.  
  
3. In the Default Web Sites dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.  
  
4. On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.  
  
5. On the **Server Certificate** page, select **Create a new certificate**, and then click **Next**.  
  
6. On the **Delayed or immediate request** page, click **Next**.  
  
7. On the **Name and Security Settings** page, click **Next**, keeping the defaults.  
  
8. On the **Organization Information** page, in the **Organization** box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the **Organizational unit** box, type **Test**, and then click **Next**.  
  
9. On the **Your Site's Common Name** page, in the **Common name** box, type the name of your computer, and then click **Next**.  
  
10. On the **Geographical Information** page, in the **State/province** box, type your state/province, in the **City/locality** box, type your city/locality, and then click **Next**.  
  
11. On the **Certificate Request File Name** page, in the **File name** box, leave the default **C:\certreq.txt**, and then click **Next**.  
  
12. On the **Request File Summary** page, click **Next**.  
  
13. On the **Completing the Web Server Certificate Wizard** page, click **Finish** to close the **IIS Certificate Wizard**.  
  
### To generate a new server certificate  
  
1.  In Internet Explorer, locate and open http://\<*contoso_machine*\>/CertSrv.  
  
    > [!NOTE]
    >  In step 1, open http://\<*contoso_machine*\>/CertSrv on the Contoso or Fabrikam computer.  
  
2.  On the **Microsoft Certificate Services Wizard Welcome** page, click **Request a certificate.**  
  
3.  On the **Request a Certificate** page, click **advanced certificate request**.  
  
4.  On the **Advanced Certificate Request** page, click **Submit a certificate request by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file**.  
  
5.  On the **Submit a Certificate Request or Renewal Request** page, click **Browse for a file to insert**.  
  
    > [!NOTE]
    >  If you receive a security error when clicking the link, open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box, and then click **Submit**. You can then go to step 10.  
  
6.  Click **Browse** to open the **Choose File** dialog box.  
  
7.  In the **Choose File** dialog box, locate the *\<drive\>*:\ folder, select the certreq.txt file, and then click **Open**.  
  
8.  On the **Submit a Certificate Request or Renewal Request** page, click **Read**.  
  
9. On the **Submit a Certificate Request or Renewal Request** page, click **Submit** to generate the new certificate.  
  
10. On the **Certificate Issued** page, click **Download Certificate**.  
  
11. In the **File Download** dialog box, click **Save**.  
  
12. In the **Save As** dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.  
  
13. Click **Close** to close the **Download Complete** dialog box.  
  
### To Prepare a new Server Certificate for IIS  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In the Internet Information Services left pane, click <computer_name> (local computer), double click **Server Certificates** in the right pane. Select **Create Certificate Request** from Actions pane.  
  
3.  In Distinguished Name Properties dialog box type the name of the computer in the Common name: text box, in the Organization: box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the Organizational unit: box type Test, in the City/locality box, type your city/locality, in the State/province box, type your state/province, in the Country/region drop down, select your Country/region and then click **Next**.  
  
4.  In the Cryptographic Service Provider Properties dialog box, click **Next**.  
  
5.  In the File Name dialog box, specify C:\certreq.txt in the text box, click **Finish**.  
  
### To generate a new server certificate for IIS  
  
1.  In Internet Explorer, locate and open http://<contoso_machine>/CertSrv.  
  
    > [!NOTE]
    >  In step 1, open http://<contoso_machine>/CertSrv on the Contoso or Fabrikam computer.  
  
2.  On the Microsoft Certificate Services Wizard Welcome page, click **Request a certificate**.  
  
3.  On the Request a Certificate page, click **Advanced Certificate Request**.  
  
4.  On the Advanced Certificate Request page, click **Submit a certificate request** by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file.  
  
5.  Open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box on the Submit a Certificate Request or Renewal Request page, and then click **Submit**.  
  
6.  On the Certificate Issued page, click **Download Certificate**.  
  
7.  In the File Download dialog box, click **Save**.  
  
8.  In the Save As dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.  
  
### To import the server certificate into IIS  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In the Internet Information Services left pane, click **(local computer)**, double click **Server Certificates** in the right pane. Select **Complete Certificate Request** from the Actions pane.  
  
3.  In Specify Certificate Authority Response dialog box type **\<drive\>:\Certs\SSLCert.cer** in **File name containing the certification authority’s response** text box. In Friendly name text box type **ContosoSSLCert**.  
  
### To enable SSL bindings for IIS  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In the Internet Information Services left pane, expand **(local computer)**, expand **Sites**, right-click **Default Web Site**, and then click **Edit Bindings**.  
  
3.  In Site Bindings dialog box click **Add**. In the Add Site Binding dialog box select **https** from Type drop down, select **ContosoSSLCert** from SSL certificate drop down, click **OK**, click **Close**.  
  
### To import the server certificate into IIS  
  
1. Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. In the Internet Information Services left pane, expand **\<**<em>computer_name</em>\> (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.  
  
3. In the Default Web Site Properties dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.  
  
4. On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.  
  
5. On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.  
  
6. On the **Process a Pending Request** page, in the **Path and file name** box, type **\<drive\>:\Certs\SSLCert.cer** (or browse to that file) and then click **Next**.  
  
7. On the **SSL Port page**, click **Next**.  
  
8. On the **Certificate Summary** page, click **Next**.  
  
9. On the **Completing the Web Server Certificate Wizard** page, click **Finish**.  
  
## See Also  
 [Creating and Configuring the Contoso Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)