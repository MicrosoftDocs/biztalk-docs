---
description: "Learn more about: Adding Certificates to the Certificates Store on the Server"
title: "Adding Certificates to the Certificates Store on the Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Adding Certificates to the Certificates Store on the Server
Use the following steps to add certificates to the Other People folder in the Certificates (Local Computer) store on the server computer.  
  
### To add certificates to the certificate store  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BizTalk Accelerator for SWIFT Management Console**.  
  
    > [!NOTE]
    >  If you still have the MMC window open from the previous procedure (Adding Certificates to the Certificates Store on the Client), you can use it for this procedure.  
  
2.  In the Administration Console window, expand the **Certificates (Local Computer)** folder, and then expand **Other People**.  
  
3.  Right-click **Certificates**, point to **All Tasks**, and then click **Import**.  
  
4.  On the Welcome to the Certificate Import Wizard page, click **Next**.  
  
5.  On the File to Import page, click **Browse**.  
  
6.  In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.  
  
7.  On the File to Import page, click **Next**.  
  
8.  On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Other People** is displayed in the **Certificate Store** box, and then click **Next**.  
  
9. On the Completing the Certificate Import Wizard page, click **Finish**.  
  
10. In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.  
  
11. Repeat steps 3 through 10 for all other certificates that you will use in message repair and new submission.
