---
title: "Exporting Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exporting certificates"
  - "certificates, exporting"
ms.assetid: edeeb300-19d6-44a8-b730-dcd15891cdf9
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exporting Certificates
This topic describes how to export a certificate by using the Certificate Export Wizard. Use this wizard to export either a public certificate or a private certificate.  
  
### To export a partner certificate  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. Expand **Certificates (Local Computer)**, expand **Other People**, and then click **Certificates**.  
  
3. In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.  
  
4. On the **Welcome to the Certificate Export Wizard** page, click **Next**.  
  
5. On the **Export File Format** page, select the format that you want to use for the file. This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.  
  
   > [!NOTE]
   >  Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.  
  
6. On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.  
  
### To export the home organization certificate  
  
1. Click **Start**, click **Run**, type **runas /user:\<host service\> mmc**, where \<*hostservice*\> is the name of the service that you associated with the host service when you installed [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)], and then click **OK** to run the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) in the context of the host service.  
  
   > [!NOTE]
   >  You run the **runas** command to assume the identity of the host service, which is required to access the home-organization certificate.  
  
2. Expand **Certificates - Current User**, expand **Personal**, and then click **Certificates**.  
  
3. In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.  
  
4. On the **Welcome to the Certificate Export Wizard** page, click **Next**.  
  
5. To export the public key associated with the private key of a certificate, leave **No, do not export the private key** selected. To export the private key, select **Yes, export the private key**.  
  
   > [!NOTE]
   >  If you select **Yes, export the private key**, it is highly recommended that you do not send the resulting file to a partner.  
  
   > [!NOTE]
   >  The **Yes, export the private key** option will not be available if you did not make the private key exportable when you first imported it.  
  
6. On the **Export File Format** page, select the format that you want to use for the file. This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.  
  
   > [!NOTE]
   >  Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.  
  
7. On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.  
  
## See Also  
 [Managing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)