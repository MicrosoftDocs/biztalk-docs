---
description: "Learn more about: AddResource Command"
title: "AddResource Command"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# AddResource Command
The topics in this section provide reference information about the parameters of the AddResource command. The parameters that you use with this command vary according to the type of artifact that you want to add. To obtain complete lists of artifact types, use the **ListTypes** command, as described in [ListTypes Command](../core/listtypes-command.md).  
  
 To get help for adding a particular artifact type, type the following command:  
  
 **BTSTask AddResource /Type:**\<*type name*\> **/?**  
  
> [!NOTE]
>  If the artifact you are adding has a very long path name, including the file name, the operation to add the artifact to an application may fail. A path cannot exceed 260 characters.  
>   
>  If an add operation fails, all actions taken during the operation are rolled back, except that assemblies are not removed from the global assembly cache if they were added by this command, and entries are not removed from the Windows registry if any entries were made.  
  
## In This Section  
  
-   [AddResource Command: BizTalk Assembly](../core/addresource-command-biztalk-assembly.md)  
  
-   [AddResource Command: BizTalk Binding](../core/addresource-command-biztalk-binding.md)  
  
-   [AddResource Command: .NET Assembly](../core/addresource-command-net-assembly.md)  
  
-   [AddResource Command: BAM Artifact](../core/addresource-command-bam-artifact.md)  
  
-   [AddResource Command: Certificate](../core/addresource-command-certificate.md)  
  
-   [AddResource Command: COM Component](../core/addresource-command-com-component.md)  
  
-   [AddResource Command: File](../core/addresource-command-file.md)  
  
-   [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md)  
  
-   [AddResource Command: Postprocessing Script](../core/addresource-command-postprocessing-script.md)  
  
-   [AddResource Command: Policy](../core/addresource-command-policy.md)  
  
-   [AddResource Command: Virtual Directory](../core/addresource-command-virtual-directory.md)
