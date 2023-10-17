---
description: "Learn more about: Excluding CertSrv from Managed Paths on a Single-Computer Deployment"
title: "Excluding CertSrv from Managed Paths on a Single-Computer Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managed paths"
  - "certificate server (CertSrv)"
  - "certificates, certificate server (CertSrv)"
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Excluding CertSrv from Managed Paths on a Single-Computer Deployment
If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer and also installed the certificate server on the same computer, you need to exclude the certificate server (CertSrv) from the managed paths in Microsoft SharePoint Server Central Administration.  
  
### To exclude CertSrv from the managed paths  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  
  
2.  In the Central Administration window, in the **Virtual Server Configuration** section, click **Configure virtual server settings**.  
  
3.  In the Virtual Server List window, click **Default Web Site**.  
  
4.  In the Virtual Server Settings window, in the **Virtual Server Management** section, click **Define managed paths**.  
  
5.  In the Define Managed Paths window, in the **Add a New Path** section, enter **CertSrv** in the **Path** text box. In the **Type** section, click **Excluded Path**. Click **OK**.  
  
6.  Close the Define Managed Paths window.
