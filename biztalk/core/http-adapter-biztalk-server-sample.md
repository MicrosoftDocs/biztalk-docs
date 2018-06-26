---
title: "HTTP Adapter (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, examples"
  - "examples, HTTP adapters"
ms.assetid: f3bd8172-15c4-42fa-aa17-e4bed9d4aba4
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter (BizTalk Server Sample)
The HTTP Adapter sample demonstrates how to implement the request/response and solicit/response communication paradigms used in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## Where to Find This Sample  
 *\<Samples Path\>*\AdaptersDevelopment\HttpAdapter\  

 The following table shows the files in this sample and describes their purpose.  

|File(s)|Description|  
|---------------|-----------------|  
|\Design-Time\Adapter Management|Contains the project that implements the design time portion of this adapter.|  
|\Run-Time\HttpReceive|Contains the project that implements the request/response adapter communication pattern. This is an isolated receiver.|  
|\Run-Time\HttpSend|Contains the project that implements the solicit/response adapter communication pattern.|  

## How to Use This Sample  
 This sample is meant as a framework for you to use in developing custom adapters. In some cases BizTalk Server may need to transport messages to a specific custom application or use a protocol for which a native adapter that does not exist. Third-party companies have written adapters to support additional protocols. You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter. If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.  

 Writing a custom adapter can be a challenging exercise. To simplify this process Microsoft has developed a foundation called the Adapter Framework. You can use this framework as a basis for your development along with sample adapter source code in the BizTalk Server SDK.  For more information on custom adapters, and the Adapter Framework, please refer to the **See Also** section at the end of this document.  

## Building and Initializing the Sample Adapter  

> [!IMPORTANT]
>  If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.  

#### To build and initialize the HTTP Adapter sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\AdaptersDevelopment\HttpAdapter  

2. Run the file Setup.bat, which performs the following actions:  

   -   Compiles the HTTPAdapter and all of its dependencies.  

   -   Creates an Internet Information Services (IIS) application used by the receiver side of the adapter.  

   On IIS 7.0, you must ensure the identity of the application pool running this IIS application is a member of the following groups:  

-   BizTalk Isolated Host Users group.  

-   IIS_WPG group.  

-   On IIS 7.0, you must migrate the application to work with the Integrated .NET mode. You can migrate the application configuration, including the contents of the \<httpHandlers\> configuration section, by using the following from a command line window (the window must be running as Administrator):  

    ```  
    %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/HttpReceive"  
    ```  

-   After you migrate your application, it will run in both Classic and Integrated .NET modes, as well as on downlevel platforms.  

> [!NOTE]
>  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  

> [!NOTE]
>  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assemblies.  

> [!NOTE]
>  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Registering the Sample Adapter  

#### To register the HTTP Adapter sample  

1. In Windows Explorer, navigate to the installation drive for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then navigate to \<Samples Path\>\AdaptersDevelopment\HTTPAdapter.  

2. To add the sample adapter to the registry, double-click **HTTP.NET.reg**.  

   > [!NOTE]
   >  HTTP.NET.reg includes hard-coded paths to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation directory. If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must modify the file HTTP.NET.reg with the appropriate paths. Update the paths associated with the "OutboundAssemblyPath" and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.  
   > 
   > [!IMPORTANT]
   >  If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **HTTP.NET.reg** registry file.  

3. In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.  

4. To close Windows Explorer, on the **File** menu, click **Close**.  

## Installing the Sample Adapter  

#### To install the HTTP Adapter sample  

1. Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand the **BizTalk Group** tree, then expand the **Platform Settings** tree.  

3. Right-click **Adapters**, click **New**, and then click **Adapter**.  

4. In the **Adapter Properties** dialog box, do the following.  


   |  Use this   |                  To do this                  |
   |-------------|----------------------------------------------|
   |    Name     |              Type **HTTP.NET**.              |
   |   Adapter   | Select **HTTP.NET** from the drop-down list. |
   | Description |      Type **Sample HTTP.NET Adapter**.       |


5. Click **OK**.  

6. The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.  

## Stopping and Restarting the Host Instance  

#### To stop and restart the host instance for the HTTP Adapter sample  

1. Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and select [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand **Platform Settings**, and click **Host Instances**.  

3. In the results pane, right-click the host instance (typically, the computer name), and then click **Stop**.  

    The status of the host instance changes to **Stopped**.  

4. In the results pane, right-click the host instance, and then click **Start**.  

   The HTTP.NET adapter is now ready to be used by your application. When configuring the adapter, the format for the **Virtual Directory** transport property is of the form: /httpreceive/httpreceive.aspx?optionalQueryString.  

## Comments  
 The HTTP.NET adapter makes use of the BaseAdapter classes provided in *\<Samples Path\>*\AdaptersDevelopment\BaseAdapter\v1.0..2\\. The classes provided in the BaseAdapter project are intended to accelerate adapter development. Refer to the BaseAdapter code comments for details about the classes provided.  

## See Also  
 [Registering an Adapter](../core/registering-an-adapter.md)   
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)   
 [Developing Custom Adapters](../core/developing-custom-adapters.md)   
 [What Is the Adapter Framework?](../core/what-is-the-adapter-framework.md)   
 [Using the Adapter Framework Tools](../core/using-the-adapter-framework-tools.md)   
 [Developing a Receive Adapter](../core/developing-a-receive-adapter.md)   
 [Developing a Send Adapter](../core/developing-a-send-adapter.md)   
 [How to Deploy a Custom Adapter](../core/how-to-deploy-a-custom-adapter.md)   
 [Tips for Designing Your Adapter](../core/tips-for-designing-your-adapter.md)   
 [Adapter Design-Time Configuration](../core/adapter-design-time-configuration.md)