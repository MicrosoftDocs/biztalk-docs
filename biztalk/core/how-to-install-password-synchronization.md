---
description: "Learn more about: How to Install Password Synchronization"
title: "How to Install Password Synchronization"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Install Password Synchronization
As with the other Single Sign-On features, Password Synchronization is not installed in the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, and must be specifically selected during setup.

### To install Password Synchronization

1. On the BizTalk Server CD, browse to the **\<CDRoot\>\Platforms\SSO** folder.

2. Run **setup.exe** and follow the instructions in the wizard.

3. Select the **Password Synchronization** feature and proceed with the installation.

   In addition to this, Password synchronization adapters are necessary to send and receive password changes to the external system. The topics in this section describe how to configure your own adapters.

   You can also contact support aliases to obtain information on available Password synchronization adapters.

   Finally, to capture password changes made in Active Directory, in addition to installing the ENTSSO Password Sync feature, components need to be installed on the domain controllers to capture password changes.

   Both the Windows Password Capture component and [Password Change Notification Service (PCNS)](https://www.microsoft.com/download/details.aspx?id=19495) must be installed on all domain controllers from which you will be capturing passwords.

   Read the accompanying documentation (also located in this folder) before you proceed with the installation on the domain controller.

## See Also
 [Password Synchronization](../core/password-synchronization2.md)
