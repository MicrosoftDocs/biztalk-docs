---
title: "Using IntelliSense to Create an Interceptor Configuration File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 349ea1bf-a5d1-4464-bf4b-d8746c622377
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using IntelliSense to Create an Interceptor Configuration File
You can use IntelliSense and schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to help you construct interceptor configuration files that are schematically valid. The BAM management utility validates your interceptor configuration file against the base interceptor configuration schema and, if the file is not valid, does not deploy the schema. If the file passes validation against the base interceptor configuration schema, it is validated against technology-specific schemas like the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema or the [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema during run time and if errors are encountered, no interception will occur. You can avoid these errors by using schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] when constructing your interceptor configuration file.  
  
> [!NOTE]
>  The sample BAM interceptor configuration XSD files are installed with the SDK files. They can be found at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs:  
> 
> - CommonInterceptorConfiguration.xsd  
>   -   WcfInterceptorConfiguration.xsd  
>   -   WorkflowInterceptorConfiguration.xsd  
  
### To obtain a copy of the interceptor schemas  
  
1. Open Notepad or another text editor.  
  
2. Navigate to the [Interceptor Configuration Schema](../core/interceptor-configuration-schema.md) topic.  
  
3. Paste the contents into a new document in the open text editor, and then save the file as a text file using the name **CommonInterceptorConfiguration.xsd** (or one of your own choosing) to your hard disk.  
  
4. Repeat these steps for the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema and [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema topics using the file names **WorkflowInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** or names of your own choosing.  
  
### To use IntelliSense with your interceptor configuration file  
  
1. Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Click **File**, click **New**, and then click **File**.  
  
3. In the **New File** dialog box, select **XML File** and then click **Open**.  
  
4. View the Properties pane by right-clicking the edit pane, and then clicking **Properties**.  
  
5. In the Properties pane, click **Schemas**, and then click the ellipsis (**…**).  
  
6. In the **XML Schemas** dialog box, click **Add** and then navigate to the location of the schemas and select **CommonInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor configuration file, or **WorkflowInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor configuration file.  
  
   > [!NOTE]
   >  If you saved the files using different names, select those files instead.  
  
7. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will now validate your interceptor configuration file when it is opened and supply IntelliSense help as you create and modify the file.  
  
## See Also  
 [Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md)   
 [Windows Communication Foundation Schema](../core/windows-communication-foundation-schema.md)