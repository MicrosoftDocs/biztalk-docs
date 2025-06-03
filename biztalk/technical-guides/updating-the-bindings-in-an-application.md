---
description: "Learn more about: Updating the Bindings in an Application"
title: "Updating the Bindings in an Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Updating the Bindings in an Application
When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings. To avoid this, you can use a binding file to update the same version of the assembly or update an assembly with a newer version.

## Updating the Same Version of an Assembly
 If the assembly has early bound ports or dynamic ports, and you changed the port configuration in the BizTalk Server Administration console, the settings will be lost when you update the assembly with an assembly having the same version number. You can export a binding file for the assembly that you are going to update. After updating the assembly, you can import the assembly into the application and then import its binding file to reapply the previous bindings.

## Updating an Assembly with a Newer Version
 You can update the version of an assembly by exporting the binding associated with a single assembly into a binding file, editing the binding file to reflect a new assembly version, and then importing the bindings of the assembly into the application. For more information about editing a binding file, see [Customizing Binding Files](../core/customizing-binding-files.md) ( HYPERLINK "<https://go.microsoft.com/fwlink/?LinkID=155000>" <https://go.microsoft.com/fwlink/?LinkID=155000>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.
