---
title: "Reuse adapter bindings in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "binding file, definition"
  - "adapter bindings, reusing"
ms.assetid: 1dc17b7a-5397-43f4-b19e-9c50fb0e97ff
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reuse adapter bindings in the Siebel adapter
A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party. This enables communication between different components of a BizTalk business solution. You can create bindings by using the BizTalk Server Administration console.  
  
## What is a binding file?  
A binding file is an XML file that contains binding information for each BizTalk orchestration in the scope of a BizTalk assembly, application, or group. The binding file describes:  
  
- The host to which each orchestration is bound
  
- The trust level of the host
  
- The settings for each send port, receive port, receive location, and party that has been configured
  
  You can generate binding files and then apply the bindings that they contain to an assembly, application, or group. This prevents having to manually configure bindings in different deployment environments and speeds up application deployment.  
  
  A binding file is not automatically generated for a BizTalk assembly, application, or group. However, you can generate a binding file by exporting bindings. You can then import the binding file into an application or group.  
  
  For more information about bindings and about binding files, see [Binding Files and Application Deployment](../../core/binding-files-and-application-deployment.md).
 
  > [!NOTE]
  >  A binding file is not automatically generated for a BizTalk assembly, application, or group. But you can generate a binding file by exporting bindings. You can then import the binding file into an application or group.  
  
## Prerequisites  
Sign in ith an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).

 
## Export bindings
This section describes how to export bindings for a BizTalk application into an XML file. You can then import the bindings from the XML file into another BizTalk application. Importing bindings overwrites any existing bindings of the same name in the application. You can also add bindings to an application, which does not overwrite existing bindings. The bindings that you add do not take effect until you import the application.  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Expand **BizTalk Group**, and then expand **Applications**.  
  
3. Right-click the application whose bindings you want to export, select **Export**, and then select **Bindings**.  
  
4. On the **Export Bindings** page, in **Export to file**, type the absolute path of the XML file to which to export the bindings.  
  
    For example, enter `C:\Bindings\Application1Bindings.Binding1.xml`  
  
5. Confirm that **Export all bindings from the current application** is selected.  
  
6. To export all party information for the group, select the **Export Global Party information** check box.  
  
7. Select **OK**. The bindings are exported into an XML file in the location that you specified.  

## Import bindings
Import bindings using the BizTalk Server Administration console.
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Expand **BizTalk Group**, and then expand **Applications**.  
  
3. Right-click the application into which you want to import bindings, select **Import**, and then select **Bindings**.  
  
4. Select the binding file, and then select **Open**.  
  
The artifacts in the binding file are written to the application. They display in appropriate folders of the application. For example, the send ports imported as part of the bindings display under the **Send Ports** folder.  

## Passwords are removed  
For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console for the send port or receive location. 

For information about specifying user name and passwords, see [Configure the sign in credentials for the Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-sign-in-credentials-for-the-siebel.md).

## See also
[Building blocks to create BizTalk applications with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)