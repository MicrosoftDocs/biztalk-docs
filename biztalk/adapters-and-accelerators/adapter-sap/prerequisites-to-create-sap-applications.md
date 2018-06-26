---
title: "Prerequisites to create SAP applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51ae9569-4081-4142-9ee2-8ae0069e9d90
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Prerequisites to create SAP applications
This section provides information about tasks that you must perform before developing BizTalk applications using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The section also lists some BizTalk Server tools that are used to develop BizTalk applications.  

## Create a strong-name key file

You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. A strong name consists of the project's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature. The strong-name key file contains the public key and the private key.  

> [!IMPORTANT]
>  Creating a strong-name key file is a one-time task. You can use the same key for all the BizTalk applications you develop.  

1.  Open the developer command prompt for Visual Studio.  

2.  At the command prompt navigate to the location where you want to create the key file. For example, type **cd C:\Sample**,and then press ENTER.  

3.  At the command prompt, type `sn -k <key file name\>.snk`, and then press ENTER.  

    > [!NOTE]
    >  You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.  

4.  At the command prompt, type **exit**, and then press ENTER.  

## Learn the BizTalk Server tools

The topics on how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md) assume that you have working knowledge of a number of BizTalk Server tools. You will use the following tools to develop BizTalk applications using [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  

- Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] 

- Orchestration eesigner  

- Pipeline designer  

- BizTalk mapper  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console  


### Prerequisites  
 You must install [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.  

### BizTalk Server Tools  
 The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.  


|                                   Tool                                    |                                                                                                                                                                                              Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation                                                                                                                                                                                               |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] | -   [Using Visual Studio](../../core/using-visual-studio.md) <br />-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)<br />-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx). |
|                          Orchestration Designer                           |                                                                                                                                                                                          [Creating orchestrations using orchestration designer](../../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                           |
|                             Pipeline Designer                             |                                                                                                                                                                                                    [Creating pipelines using pipeline designer](../../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                     |
|                              BizTalk Mapper                               |                                                                                                                                                                                                            [Creating maps using BizTalk mapper](../../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                             |
|                   BizTalk Server Administration console                   |                                                                                                                                                                                               [Using the BizTalk Server Administration console](../../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                                |

## Next
[Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)