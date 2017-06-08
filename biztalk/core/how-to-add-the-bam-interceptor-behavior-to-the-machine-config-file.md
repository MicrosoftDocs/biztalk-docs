---
title: "How to Add the BAM Interceptor Behavior to the Machine.config File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ea09925-264f-4976-8e34-f63bad70f886
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add the BAM Interceptor Behavior to the Machine.config File
To intercept data in BAM, you must add the BAM interceptor behavior to the Microsoft .NET machine.config file. You can do this in two ways:  
  
-   Manually edit the machine.config file to include the behavior.  
  
-   Use the Service Configuration Editor to include the behavior.  
  
### To manually edit the machine.config file  
  
1.  Edit the machine.config file located in the Microsoft .NET configuration folder. To do this, click **Start**, click **Run**, type notepad c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config, and then click **OK**.  
  
2.  Update the machine.config file with the following behavior extensions.  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="BAMEndPointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
3.  Close and save the machine.config file.  
  
#### To edit the machine.config file using the Service Configuration Editor  
  
1.  Open the Service Configuration Editor. For information about using the Service Configuration Editor, see [http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557).  
  
2.  In the tree view pane (labeled **Configuration**), expand the node tree. Click the **Advanced** folder, click the **Extensions** folder, and then select the **behavior element extensions** element.  
  
3.  Create a new behavior element extension. Click the **New** button to open the Extension Configuration Element Editor dialog box. In **Configuration Name** enter a unique name for the behavior, for example BAMEndPointBehaviorExtension.  
  
     ![Extension Configuration Element Editor](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")  
  
4.  Click the **Type** field, and then click the ellipsis button (**...**) button to open the Behavior Extension Type Browser dialog box.  
  
5.  Click the global assembly cache (GAC) icon to list the DLLs in GAC.  
  
6.  Select the Microsoft.BizTalk.Bam.Interceptors assembly.  
  
7.  Click the **Open** button to select the assembly, and then close the dialog box.  
  
     ![Bejavopr Extension Type Browser](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")  
  
8.  In the Type Name pane of the Behavior Extension Type Browser dialog box, double-click the Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior type (as highlighted in the following screen).  
  
     ![Bejavopr Extension Type Browser](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")  
  
     This opens the Extension Configuration Element Editor.  
  
9. Click **OK** to close the Extension Configuration Element Editor dialog box.  
  
10. In the details pane of the Service Configuration Editor, verify that the BAMEndPointBehaviorExtension appears.  
  
11. Close the Service Configuration Editor.  
  
## Next Steps  
 [How to Configure the BAM WCF Interception](../core/how-to-configure-the-bam-wcf-interception.md)  
  
## See Also  
 [Configuring the WCF Adapter to Intercept BAM Data](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)