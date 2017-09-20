---
title: "Adding Certificates to the Certificates Store on the Client | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, adding to certificates store"
  - "certificates store"
ms.assetid: 9e2722ee-dd6f-4b14-9796-2f2157e8cad2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding Certificates to the Certificates Store on the Client
Use the following steps to add certificates to the Personal folder in the certificates store on each client computer. The certificates must be added to the Personal folder in the Certificates - Current User store.  
  
> [!IMPORTANT]
>  If your certificates are not distributed via an enterprise trusted Certification Authority, you must import the Certification Authority's root certificate onto the client computer(s). Otherwise, your personal certificates will not work. Import the Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) node.  
  
### To add certificates to the certificate store  
  
1.  Click **Start**, and then click **Run**. Enter **mmc**, and then click **OK**.  
  
2.  In the Console1 dialog box, click **File**, and then click **Add/Remove Snap-in**.  
  
3.  In the Add/Remove Snap-in dialog box, click **Add**.  
  
4.  In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.  
  
5.  In the Certificates snap-in dialog box, click **My user account**, and then click **Finish**.  
  
6.  In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.  
  
7.  In the Certificates snap-in dialog box, click **Computer account**, and then click **Next**.  
  
8.  In the Select Computer dialog box, make sure **Local computer** is selected, and then click **Finish**.  
  
9. In the Add Standalone Snap-in dialog box, click **Close**.  
  
10. In the Add/Remove Snap-in dialog box, click **OK**.  
  
11. In the **Console Root** pane of the Console1 dialog box, expand the **Certificates - Current User** folders.  
  
12. Under **Certificates - Current User**, expand **Personal**.  
  
13. Right-click **Certificates**, point to **All Tasks**, and then click **Import**.  
  
14. On the Welcome to the Certificate Import Wizard page, click **Next**.  
  
15. On the File to Import page, click **Browse**.  
  
16. In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.  
  
17. On the File to Import page, click **Next**.  
  
18. On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Personal** is displayed in the **Certificate Store** box, and then click **Next**.  
  
19. On the Completing the Certificate Import Wizard page, click **Finish**.  
  
20. In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.  
  
21. Repeat steps 13 through 20 for all other certificates that you will use in message repair and new submission.