---
title: "Installing Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccfb0005-f629-4749-8e54-d3e960448f23
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Installing Password Synchronization
As with the other Single Sign-On (SSO) features, Password Synchronization is not installed in the default [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] installation, and must be specifically selected during Setup.  
  
### To install Password Synchronization  
  
1. Run the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup program, and select **Custom Installation**.  
  
2. Under the **Security Integration** feature, select the **Enterprise Single Sign-On Password Synchronization** sub feature.  
  
3. Complete the installation.  
  
   You also need Password Synchronization adapters to send and receive password changes to the external system. Other topics in this section describe how to configure your own adapters. For more information, see [Administering Password Synchronization](../esso/administering-password-synchronization.md). You can also view a list of currently available adapters at the following location: [http://go.microsoft.com/fwlink/?LinkId=68145](http://go.microsoft.com/fwlink/?LinkId=68145). You can contact support aliases to obtain information about these Password Synchronization adapters.  
  
   Finally, to capture password changes made in Active Directory, in addition to installing the ENTSSO Password Sync feature, you must install components on the domain controllers to capture password changes. Both the Windows Password Capture component and Password Change Notification Service (PCNS) must be installed on all domain controllers from which you will be capturing passwords. You can find these components in the following location:  
  
   http://www.microsoft.com/downloads/details.aspx?FamilyID=C0964F2E-FA9F-4FC7-AC13-C43928EFEE9D&displaylang=en  
  
   Read the accompanying documentation before you proceed with the installation on the domain controller.  
  
## See Also  
 [Password Synchronization](../esso/password-synchronization3.md)