---
description: "Learn more about: Installing Password Synchronization"
title: "Installing Password Synchronization"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing Password Synchronization
As with the other Single Sign-On (SSO) features, Password Synchronization is not installed in the default [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] installation, and must be specifically selected during Setup.

### To install Password Synchronization

1. Run the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup program, and select **Custom Installation**.

2. Under the **Security Integration** feature, select the **Enterprise Single Sign-On Password Synchronization** sub feature.

3. Complete the installation.

   You also need Password Synchronization adapters to send and receive password changes to the external system. Other topics in this section describe how to configure your own adapters. For more information, see [Administering Password Synchronization](../esso/administering-password-synchronization.md). You can contact support aliases to obtain information about these Password Synchronization adapters.

   Finally, to capture password changes made in Active Directory, in addition to installing the ENTSSO Password Sync feature, you must install components on the domain controllers to capture password changes. Both the Windows Password Capture component and [Password Change Notification Service (PCNS)](https://www.microsoft.com/download/details.aspx?id=19495) must be installed on all domain controllers from which you will be capturing passwords.

   Read the accompanying documentation before you proceed with the installation on the domain controller.

## See Also
 [Password Synchronization](../esso/password-synchronization3.md)
