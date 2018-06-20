---
title: "Step 9: Build and Deploy the Echo Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Build and Deploy the Echo Adapter
![Step 9 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 **Time to complete:** 10 minutes  
  
 In this step, you will perform the tasks necessary to deploy the Echo Adapter. This involves all of the following:  
  
- Create a strong name file and assign it to the Echo Adapter assembly  
  
- Build the Echo Adapter  
  
- Publish the assembly into the GAC  
  
- Register the Echo Adapter with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]  
  
## Prerequisites  
 To successfully complete this step, you should be familiar with strong name files and the GAC. A basic understanding of [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] configuration is helpful but not required.  
  
### To assign a strong name to your assembly  
  
1.  In Solution Explorer, right-click the **EchoAdapter** project, and then click **Properties**.  
  
2.  In the EchoAdapter Property Pages dialog box, select **Signing** from the left pane.  
  
3.  Click the **Sign the assembly** tab.  
  
4.  Choose **\<new…\>** for the strong name file. When prompted for a file name, type **EchoAdapter.snk**,deselect the protect my key file with a password option, then click **OK**.  
  
5.  Click the **Application** tab.  
  
6.  Change the assembly name to **Microsoft.Adapters.Samples.EchoV2**.  
  
7.  Click **File** on the Visual Studio menu then choose **Save All**.  
  
### To build and deploy Echo Adapter  
  
1.  In Solution Explorer, right-click the **EchoAdapter** project, and then click **Build**. If the build does not succeed, fix any errors and try rebuilding the Echo Adapter.  
  
2.  Open a Visual Studio command prompt.  
  
3.  Type the following command:  
  
     **gacutil.exe /if "\<** *path to assembly\Microsoft.Adapters.Samples.EchoV2.dll* **\>"**  
  
     This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.  
  
### To register the Echo Adapter with Windows Communication Foundation  
  
1. Edit the machine.config file located in the Microsoft .NET configuration folder. To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.  
  
2. Update the machine.config file. If your machine.config does not contain a system.serviceModel section, add the following section at the end of the configuration file but before the closing root tag.  
  
   > [!NOTE]
   >  Replace the version, culture, public key token and other assembly-specific information with your adapter's information.  
  
   ```  
   <system.serviceModel>  
     <client>  
       <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
         name="echov2" />  
     </client>  
     <extensions>  
       <bindingElementExtensions>  
         <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
       </bindingElementExtensions>  
       <bindingExtensions>  
         <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
       </bindingExtensions>  
     </extensions>  
   </system.serviceModel>  
   ```  
  
   - OR -  
  
     If your machine.config contains a system.serviceModel section, determine which elements are missing and add them.  
  
   > [!NOTE]
   >  Replace the version, culture, public key token and other assembly-specific information with your adapter's information.  
  
   ```  
   <client>  
     <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
       name="echov2" />  
   </client>  
   <extensions>  
     <bindingElementExtensions>  
       <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
     </bindingElementExtensions>  
     <bindingExtensions>  
       <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
     </bindingExtensions>  
   </extensions>  
   ```  
  
3. Save the machine.config file.  
  
## What Did I Just Do?  
 In this final step of the Echo Adapter tutorial, you added a strong name to the Echo Adapter, built and deployed the adapter, then modified Machine.config to include information about the adapter. At this point, the Echo Adapter should be available to consuming applications.  
  
## Next Steps  
 This tutorial is complete. If you want to test Echo Adapter functionality in a .NET project, see [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).  
  
## See Also  
 [Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)   
 [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)