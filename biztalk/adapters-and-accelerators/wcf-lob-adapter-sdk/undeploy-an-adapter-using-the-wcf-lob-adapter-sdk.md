---
title: "Undeploy an adapter using the WCF LOB adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98f9a124-9e63-4451-af0e-ffee752fbeac
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Undeploy an adapter using the WCF LOB adapter SDK
To undeploy an adapter from a computer, the user needs to perform the following two tasks:  
  
1.  Uninstall the adapter assembly (and any dependent assemblies) from the global assembly cache (GAC).  
  
2.  Remove the adapter binding and adapter binding element in the machine.config file.  
  
## Uninstall an Assembly from the GAC  
  
#### Use the Windows interface  
  
1.  Open Windows Explorer as follows: Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  
  
2.  Browse to the GAC, which is located at %systemdrive%\Windows\Assembly.  
  
3.  Right-click each assembly file that is included in your application, click **Uninstall**, and then click **Yes** to confirm.  
  
#### Use the command line  
  
1. Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.  
  
2. At the command prompt, type the following command:  
  
    **gacutil /u** \<*fully qualified*<em>assembly name</em>\>  
  
    In this command, the assembly name is the name of the assembly to uninstall from the GAC.  
  
    The following example removes an assembly named hello.dll from the GAC.  
  
    `gacutil /u "MyAdapter,Version=1.0.0.0, Culture=neutral, PublicKeyToken=fafafafafafafafa"`
  
## Remove the Adapter Binding from the Machine.config File  
 You can manually edit the machine.config file to remove the adapter binding, or use the Service Configuration Editor. This section lists both steps. 
  
#### Manually edit the machine.config file  
  
1.  Edit the machine.config file located in the Microsoft .NET configuration folder. To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.  
  
    > [!NOTE]
    >  Make a backup of the machine.config file before you make changes to guard against editing mistakes.  
  
2.  Update the machine.config file. Find the bindingExtensions element for the adapter you want to remove. Based on the other information that is present, do one of the following:  
  
    -   If there are other bindingExtensions, remove only your adapter extension.  
  
    -   If there are no other bindingExtensions, you can remove the bindingExtensions section (including your adapter extension).  
  
    -   If there are no other bindingExtensions or extensions, you can remove the extensions section.  
  
    -   Finally, if system.serviceModel contains only your adapter extension, you can remove the entire system.serviceModel section.  
  
3.  Repeat step 2 for the bindingElementExtensions element.  
  
4.  Close and save the machine.config file.  
  
#### Use the Service Configuration Editor do change the machine.config file  
  
1.  Open Service Configuration Editor. See [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) for more information.
  
2.  In the tree view pane (labeled **Configuration**), expand the node tree. Click the **Advanced** folder, click the **Extensions** folder, and then select the binding extensions element.  
  
3.  In the details pane of the Binding Extensions Editor, click the binding extension that you want to delete, and then click **Delete**. In the following figure, MyAdapterExtension is highlighted and will be deleted.  
  
     ![Service configuration editor with added extension.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")  
  
4.  Close the Service Configuration Editor.  
  
## See Also  
 [Deploy an adapter using the WCF LOB adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)