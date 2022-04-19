---
description: "Learn more about: Loopback Adapter Sample"
title: "Loopback Adapter Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b9344e8-7759-432d-bff8-001f4393728d
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Loopback Adapter Sample
The Loopback Adapter sample is a password sync adapter for Enterprise Single-Sign on (ENTSSO) implemented as a windows NT service written in C#. The sample demonstrates how to use the SSOPSHelper COM component and the ISSOPSWrapper interface to develop a password sync adapter in managed code.  
  
## Location in the SDK  
 \<drive>\Program Files\Common Files\Enterprise Single Sign-On\SDK\Samples\LoopbackAdapter  
  
### File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Contains the assembly information for the project.|  
|Createadapter_LoopbackAdapter.xml|Used with the ssops command-line tool to create the prototype adapter.|  
|LoopbackAdapter.cs<br /><br /> LoopbackAdapter.csproj<br /><br /> LoopbackAdapter.Designer.cs<br /><br /> LoopbackAdapter.resx|Contains the sample code for crating the Loopback adapter.|  
|LoopbackAdapter.sln|Organizes all the projects, project items, and solution items into the Loopback Solution by providing the environment with references to their locations on disk. Use Visual Studio to view this file, or double-click the file to start Visual Studio  and displays the solution in Solution Explorer.|  
|LoopbackAdapter.suo|Records all of the options associated with the Loopback Adapter Solution so that each time you open it, it includes customizations that you have made.|  
|ProjectInstaller.cs<br /><br /> ProjectInstaller.Designer.cs<br /><br /> ProjectInstaller.resx|Contains the sample code for the project installer.|  
|Properties_LoopbackAdapter.xml|Property definitions for the Loopback Adapter.|  
|Program.cs|Contains the basic framework of the application.|  
|README.txt|Shows the steps to build and run the application.|  
  
## See Also  
 [Creating a Single Sign-On Application](../esso/creating-a-single-sign-on-application.md)
