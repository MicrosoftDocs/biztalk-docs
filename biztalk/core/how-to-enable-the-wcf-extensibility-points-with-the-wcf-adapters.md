---
title: "Enable the WCF Extensibility Points with the WCF Adapters | Microsoft Docs"
description: Install assemblies, configure machine.config, add extension to BizTalk Admin, create receive location to enable WCF extensibility points for the WCF adapters in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c2af105-5272-4a6a-95d2-066312ab788e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable the WCF Extensibility Points with the WCF Adapters
Enable three WCF extensibility points—behavior extension, binding element extension, and binding extension—with the WCF-Custom and WCF-CustomIsolated adapters. To do so, you first install the assemblies implementing the WCF extensibility points in the global assembly cache (GAC), then modify the machine.config file on your computers, and then configure the WCF-Custom or the WCF-CustomIsolated adapter by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
See [Extending WCF](https://docs.microsoft.com/dotnet/framework/wcf/extending/extending-wcf) for more info on WCF extensibility points.
  
 
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md) provides more info.  
  
## Install assemblies implementing a WCF extensibility point in the GAC  
  
1. Copy the assemblies implementing the WCF extensibility point to a folder on your local computer.  
  
2. Copy the assemblies that the WCF extensibility point uses, if any, to a folder on your local computer.  
  
3. Start the **Visual Studio Command Prompt**.  
  
4. Type the following command:  
  
    **gacutil.exe /if "\<** *path to the assembly .dll file* **\>"**  
  
5. This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.  
  
6. At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, repeat steps 4 and 5 against all the assemblies you copied in steps 1 and 2 of this procedure.  
  
7. If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 6 of this procedure on all the computers.  
  
   > [!NOTE]
   >  To enable WCF extensibility points for the WCF adapters, the BizTalk Host instance running the adapter must be able to load at run time the assemblies where the WCF extensibility points are implemented.  
  
## Configure the machine.config file for a WCF binding extension  
  
1. At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.  
  
2. In Notepad, if the machine.config file does not have the **\<system.serverModel\>\\<extensions\>** elements, add those elements inside the **\<configuration\>** element of the machine.config file, and then add the **\<bindingExtensions\>** element for a WCF binding extension inside the **\<system.serverModel\>\\<extensions\>** elements. For example, to enable a custom binding extension, netHttpBinding, add the following code inside the **\<configuration\>** element of the machine.config file:  
  
   ```  
   <system.serviceModel>  
     <extensions>  
       <bindingExtensions>  
         <add name="netHttpBinding" type="Microsoft.Samples.Channels.NetHttpBindingCollectionElement, NetHttpBinding, Version=3.0.0.0, Culture=neutral, PublicKeyToken=5b637b51c4aaa2a8" />  
       </bindingExtensions>        
     </extensions>  
   </system.serviceModel>  
   ```  
  
   > [!NOTE]
   >  - You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.  
   >  - See [bindingExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingextensions) on this element.
  
3. In Notepad, save the machine.config file.  
  
4. If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.  
  
   > [!NOTE]
   >  You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Configure a WCF binding extension by using the BizTalk Administration console  
  
1. Open **BizTalk Server Administration**.  
  
   > [!NOTE]
   >  If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.  
  
3. If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.  
  
4. If you want to configure a receive location to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location\>*.  
  
   -   In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.  
  
5. If you want to configure a send port to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port\>*.  
  
   -   In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
6. In the transport properties dialog box, on the **Binding** tab, select the binding extension, and then configure the rest of the settings for the transport.  
  
7. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.  
  
## Configure the machine.config file for a WCF binding element extension  
  
1. At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.  
  
2. In Notepad, if the machine.config file does not have the **\<system.serverModel\>\\<extensions\>** elements, add those elements inside the **\<configuration\>** element of the machine.config file, and then add the **\<bindingElementExtensions\>** element for a WCF binding element extension inside the **\<system.serverModel\>\\<extensions\>** elements. For example, to enable a custom binding element extension, droppingInterceptor, add the following code inside the **\<configuration\>** element of the machine.config file:  
  
   ```  
   <system.serviceModel>  
     <extensions>  
       <bindingElementExtensions>  
         <add name="droppingInterceptor" type="Microsoft.ServiceModel.Samples.DroppingServerElement, MessageInterceptor, Version=0.0.0.0, Culture=neutral, PublicKeyToken=098514eef14aa34a"/>  
       </bindingElementExtensions>  
     </extensions>  
   </system.serviceModel>  
   ```  
  
   > [!NOTE]
   > - You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.  
   > - See [bindingElementExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingelementextensions) on this element.
  
3. In Notepad, save the machine.config file.  
  
4. If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.  
  
   > [!NOTE]
   >  You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Configure a WCF binding element extension by using the BizTalk Administration console  
  
1. Open **BizTalk Server Administration**.  
  
   > [!NOTE]
   >  If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.  
  
3. If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.  
  
4. If you want to configure a receive location to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location\>*.  
  
   -   In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.  
  
5. If you want to configure a send port to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port\>*.  
  
   -   In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
6. In the transport properties dialog box, on the **Binding** tab, in the **Binding Type** drop-down list, select **customBinding**.  
  
7. In the transport properties dialog box, on the **Binding** tab, right-click the client area of the **Binding** list, and then click **Add extension**.  
  
8. In the **Select Binding Element Extension** dialog box, select a binding element extension, and then click **OK**.  
  
9. In the transport properties dialog box, on the **Binding** tab, adjust the order of the binding elements added in the **Binding** list depending on the type of the binding element extension you added in the previous step as follows:  
  
    -   In the **Binding** list, right-click a binding element extension, and then click **Move extension up** or **Move extension down**. The lowest binding element extension in the **Binding** list corresponds to the bottom component of the channel stack. The highest binding element in the **Binding** list corresponds to the top component of the communication stack.  
  
        > [!NOTE]
        >  See [Custom Bindings](https://docs.microsoft.com/dotnet/framework/wcf/extending/custom-bindings) for details about the specific order of the binding elements for the custom binding.
  
10. In the transport properties dialog box, configure the rest of the settings for the transport.  
  
11. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.  
  
## Configure the machine.config file for a WCF behavior extension  
  
1. At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.  
  
2. In Notepad, if the machine.config file does not have the **\<system.serverModel\>\\<extensions\>** elements, add those elements inside the **\<configuration\>** element of the machine.config file, and then add the **\<behaviorExtensions\>** element for a WCF behavior extension inside the **\<system.serverModel\>\\<extensions\>** elements. For example, To enable a custom behavior extension, schemaValidator, add the following code inside the **\<configuration\>** element of the machine.config file:  
  
   ```  
   <system.serviceModel>  
     <extensions>  
       <behaviorExtensions>  
         <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ad307e213604f592"/>  
       </behaviorExtensions>  
     </extensions>  
   </system.serviceModel>  
   ```  
  
   > [!NOTE]
   >  - You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.  
   >  - See [behaviorExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/behaviorextensions) on this element.
  
3. In Notepad, save the machine.config file.  
  
4. If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.  
  
   > [!NOTE]
   >  You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Configure a WCF behavior extension by using the BizTalk Administration console  
  
1. Open **BizTalk Server Administration**.  
  
   > [!NOTE]
   >  If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.  
  
3. If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.  
  
4. If you want to configure a receive location to use a WCF extensibility point, in the BizTalk Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location\>*.  
  
   -   In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.  
  
5. If you want to configure a send port to use a WCF extensibility point, in the BizTalk Administration console, expand **BizTalk Group**, expand *\<BizTalk application\>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port\>*.  
  
   -   In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
6. In the transport properties dialog box, on the **Behavior** tab, right-click **ServiceBehavior** or **EndpointBehavior** depending on the type of the behavior extension, and then, in the **Select Behavior Extension** dialog box, select the behavior extension, and then click **OK**.  
  
7. In the transport properties dialog box, configure the rest of the settings for the transport.  
  
8. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.  
  
## Configure a WCF-Custom receive location with an SSL certificate  
  
-   If a WCF-Custom receive location happens to use the HTTP kernel-mode driver (HTTP.sys) such as the **httpsTransport** binding element, for Secure Sockets Layer (SSL) communications, the receive location must have a certificate registered for each socket (IP address/port combination). Use the HttpCfg.exe tool to bind an SSL certificate to a port on the computer. For more information, see [How To: Configure a Port with An SSL Certificate](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate).