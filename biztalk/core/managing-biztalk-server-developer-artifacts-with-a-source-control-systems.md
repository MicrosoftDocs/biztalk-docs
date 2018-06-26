---
title: "Managing BizTalk Server Developer Artifacts with a Source Control Systems | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce25b112-38c9-40c8-9a5f-a2855572aabb
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing BizTalk Server Developer Artifacts with a Source Control Systems
Protecting your BizTalk project from unexpected system failures should be a top priority. One way to protect project files is to use a source code control system like Team Foundation Server Source Control and Microsoft Visual SourceSafe. This topic discusses some basic strategies for organizing projects to best work with any source control system, and then provides specific suggestions for using Visual SourceSafe.  
  
## Basic Organization Strategies  
 You can follow some basic organization strategies regardless of the source control system you will ultimately use. These strategies ensure your BizTalk project file structure is organized for both development and source code control.  
  
### Use a Consistent Folder Structure for Solutions and Projects  
 Development in a team environment is easier to manage if a common structure for storing [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solutions and projects is used across the whole team. This is especially true when each BizTalk project will be generating and using files such as binding files that will be required by build, test, and deployment teams.  
  
 It is often easy to start development without taking the time to standardize on the folder structures. This will inevitably cost more time later on as project links and test harnesses need to be "patched" as the solution develops.  
  
### Keep Source Control and File System Structures Identical  
 To simplify the management of multiple developers' environments, set up a folder structure within the source control system that matches your local file system structure. This helps ensure that a developer can simply get a latest version and know that the structure on the disk complies with the team's standards.  
  
### Define and Use a Common Root Folder  
 It is recommended that you keep all project code and deliverables under a single folder root that can in turn be created on all developers' computers. Managing development artifacts and maintaining a consistent configuration is simplified when all developers use the same root. For example, create a root folder of $/SysInteg2009 within Visual SourceSafe, and all developers can create C:\SysInteg2009 on their local file systems.  
  
### Create a Master Solution That Will Hold All Projects  
 The master solution will typically be used as the main build solution. This is recommended for medium to high-complexity BizTalk projects.  
  
### Store All BizTalk Projects Under the Master Solution  
 It is useful to organize all related BizTalk projects under the master solution. The structure in the source control system should mirror this hierarchy.  
  
### Divide the Folder Structure into Shared and Process-Specific Sections  
 When you create the file structure, you typically divide the folder structure to separate the shared entities from the business process-specific entities. The shared entities are common to multiple projects and may include helper classes.  
  
 For example, the first three folders in the following list are organized by shared entity and the last two are organized by business process:  
  
 C:\SysInteg2009\\_Master_Solution\Shared\  
  
 C:\SysInteg2009\\_Master_Solution\Shared\EmailHelper  
  
 C:\SysInteg2009\\_Master_Solution\Shared\SharedSchema  
  
 C:\SysInteg2009\\_Master_Solution\AccountRequest\  
  
 C:\SysInteg2009\\_Master_Solution\AccountValidate\  
  
### Separate Pipeline Projects into Distinct Projects  
 During development of pipeline components, it is a common requirement to modify and retest a pipeline independent of the rest of the solution. For this reason it is often helpful to keep pipeline solutions as a separate BizTalk project, resulting in a separate pipeline assembly that can be removed and redeployed without the need to rebind the rest of the solution.  
  
 Additionally it is common practice to keep the code that implements the actual pipeline interfaces and pipeline processing logic in a separate project with a reference from the BizTalk project (containing the .btp files) to the [!INCLUDE[btsCSharp](../includes/btscsharp-md.md)] or Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)] project.  
  
### Keep Deployment and Test Scripts with Their Projects  
 To enable the development of a unified build and deployment process, build and install scripts should be built by the individual developers, but viewed as reusable parts of the complete solution. If the scripts are written to be reusable then tasks like the deployment of a complete solution package can reuse the scripts. For example, if the deployment and undeployment scripts accept parameters to specify the paths for the DLL and binding file folder locations, the scripts can be reused when the compiled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies are in a different location.  
  
 Using this approach, developers add the install scripts for their specific processes to the folder and then a single process can easily be written to perform a full deployment of all processes.  
  
### Use Unique Strong Name Keys When Appropriate  
 Typically a single [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution uses a single key file. This is true because the solution is treated as a single entity and is managed as such. If the business solution being developed is actually composed of two or more distinct parts, then consider if two key files should be used. Multiple keys in this scenario allow the parts to be treated as independent entities in the future, for example with differing upgrade paths.  
  
 When considering helper projects, the same considerations apply. If the helper project is (or will be) a separate entity then it should be built using a separate strong name key.  
  
### Put Dependent DLLs into a Separate Folder  
 When creating the folder structure it is helpful to create a common folder to hold DLLS that are referenced as file dependencies. By ensuring that all developers follow the same folder structure, file references will not become broken when solutions are moved between developers or workstations.  
  
### Keep Test Messages in a "Msgs" Folder  
 When developing schemas and using messages it is common to spend considerable effort testing many different sample messages against XML schema and orchestration processes.  
  
 In a real-world solution, sample messages are a valuable asset because they contain data that is meaningful to the business solution. Random or dummy values in the same message will typically cause the process to fail. For this reason sample messages should be treated with as much care as the code of the solution.  
  
 To assist in managing the message files, keep test messages under a specific folder called "msgs". In cases where there are both "generated instances" and "example messages" (for example, messages from an existing system), it is useful to keep these messages separate to allow comparison between the developed schema and actual data.  
  
 It is common in an integration project to have multiple versions of schemas and consequently, multiple versions of message files. To tell the sample messages apart, use version numbers when naming files.  
  
### Managing Other Files  
 Some types of files can be grouped and stored in a distinct folder; others can be stored with other files under a common folder. Draw up a policy on how to handle each file type and then consistently follow it.  
  
## Working with BizTalk Server and Visual SourceSafe  
 This section discusses specific considerations for working with Visual SourceSafe including handling Unicode, using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] for source control, when to check in, version control, and other issues.  
  
### Solution Character Sets  
 There is a known limitation with Visual SourceSafe related to the handling of Unicode files. When working with BizTalk solutions it is necessary to prevent Visual SourceSafe from corrupting BizTalk Server Unicode files.  
  
##### To enable Visual SourceSafe to work with BizTalk Server Unicode files  
  
1. Start Visual SourceSafe 8.0 Admin.  
  
2. Select the SourceSafe database to be used.  
  
3. On the **Tools** menu, click **Options**.  
  
4. Click the **File Types** tab.  
  
5. Add the following to the end of the list of binary files. Verify there are semicolons between each file type:  
  
    *.btm;\*.btp;\*.xsd;\*.odx  
  
6. Click **OK**.  
  
   Now Visual SourceSafe will not inspect BizTalk Server files and attempt to change their formatting.  
  
### Use Visual Studio for Source Control Operations  
 All project creation and manipulation within Visual SourceSafe should be performed by using the integrated Visual SourceSafe support menus within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Do not use Visual SourceSafe Explorer to perform these operations.  
  
### When to Check in BizTalk Server Projects  
 The recommended approach to using Visual SourceSafe is to check in code only when it has successfully passed functional tests and the developer is confident that the code will successfully build without breaking any related code. Applying this model to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] results in the following guidelines:  
  
- BizTalk projects that contain only message schemas should not be checked in until the schemas have been successfully tested against a variety of sample messages.  
  
- BizTalk projects that contain a business process should not be checked in until the solution has been successfully tested using the appropriate input and output messages and using the correct send and receive ports.  
  
- ASP.NET Web service projects should not be checked in until the Web service code has been tested against the initiating system or by using a test harness.  
  
  If this model is followed, then the Visual SourceSafe repository will always hold a build that can be successfully built and tested. This principle is important if the approach of "nightly builds" is to be adhered to.  
  
### Checking in Intermediate Versions  
 An alternative approach to checking in files is that of checking in "intermediate" versions. In this approach an intermediate version has not yet successfully passed functional tests and can be thought of as "between builds." This is generally not a recommended approach because it breaks the general principle of always having a buildable version within the source control system. However some teams prefer this approach because it allows developers to use the source control system to check in and roll back versions without needing to fulfill the criteria for checking in a formal build.  
  
 If the approach of checking in intermediate versions is required, then you cannot assume that the source control system contains a "buildable" version. Instead you must distinguish between intermediate versions and build versions. By using Visual SourceSafe you can do this in a variety of ways, either automatic or process based. For example:  
  
-   Developers follow a process of notifying the build manager when a "buildable" version is added to Visual SourceSafe.  
  
-   Developers check in a tested version, ready for building, into a "promoted area" within Visual SourceSafe. This promoted area is then used as the source upon which the master build is based.  
  
-   Code or script can be written that uses the Visual SourceSafe COM interfaces. For example, a specific label can be used to denote code ready for a build, and the script searches for this label and then "pins" this source into a separate Visual SourceSafe branch. This branch is then used as the source for master builds.  
  
### Comparing Files  
 You can use Visual SourceSafe to find the differences between two different versions of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] source file. This can be done with artifacts including maps and schemas and related files such as test messages and even exported configuration files.  
  
> [!NOTE]
>  When comparing maps, you must edit the map prior to checking it in or Visual SourceSafe will do a binary comparison when looking for differences between it and the next version. This is because encoding information is not added to the map XML until you edit it.  
  
### Version Controlling Non-BizTalk Server Project Files  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses additional files that can beneficially be versioned and stored in Visual SourceSafe. The following files are examples:  
  
- Binding files (both development and test)  
  
- Custom pipeline assemblies  
  
- Test data (for example, test messages)  
  
- Test harnesses (which may change over the project lifetime)  
  
- Build, deployment, and start-and-stop scripts that may need to be shared between development and build teams  
  
  If these files are related to a specific [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, then they can be included within the BizTalk project and managed by using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] integrated source control functions.  
  
##### To include a file or folder into an existing Visual Studio project  
  
1.  In Solution Explorer, click **Show All Files**.  
  
2.  Select the folder or file to include in the solution.  
  
3.  Right-click the folder or file, and then click **Include In Project**.  
  
> [!NOTE]
>  Visual SourceSafe Explorer should NOT be used to manage any items that are part of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project under source control.  
  
### Checking the Visual SourceSafe Database  
 When Visual SourceSafe databases are large, heavily used, or being accessed by many concurrent users, it is recommended that you regularly run the "Analyze VSS DB" command from the Visual SourceSafe menu. If the analysis detects errors, then they can be fixed by using the "Analyze and Fix VSS DB" command. Both these commands need to lock the Visual SourceSafe database, and hence require everyone to be disconnected from Visual SourceSafe.