---
title: "Step 2: Test Inbound Handler of the Echo Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 86dede9b-6b7e-4901-9c79-b75bfee9155f
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Test Inbound Handler of the Echo Adapter
![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **Time to complete:** 10 minutes  
  
 In this step, you test the inbound service provided by the Echo Adapter. You do this using Visual Studio, the Add Adapter Service Reference Visual Studio Plug-In and custom code.  
  
## Prerequisites  
 To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). This step can be completed independent of [Step 1: Test Outbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md).  
  
## Create a Visual Studio project  
  
1.  Start Visual Studio.  
  
2.  In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Project types**|Click **Visual C#**.|  
    |**Templates**|Click **Console Application**.|  
    |**Name**|Type **ConsumeEchoAdapter_Inbound**.|  
    |**Location**|Type **C:\Tutorials**.|  
    |**Solution Name**|Type **ConsumeEchoAdapter_Inbound**.|  
  
4.  Click **OK**.  
  
5.  In Visual Studio, on the **File** menu, click **Save All**.  
  
## Browse, search, and generate the WCF service  
  
1.  In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Inbound** project then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.  
  
2.  In the **Add Adapter Service Reference** screen, choose a binding. This is done by choosing **echoAdapterBindingV2**.  
  
3.  Next, configure the adapter and connection properties by clicking **Configure**.  This opens the **Configure Adapter** screen.  
  
4.  In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties. Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown. Under the **Misc** category, click **InboundFileSystemWatcherFolder** and then enter the directory you want to monitor.  
  
5.  Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.  
  
6.  Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports). After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.  
  
7.  To view available inbound operations, change the **Service contract type** to **Service (Inbound operations)**.  
  
8.  In the Category Tree, click **Main Category**. This populates the list of available categories and operations with a single inbound operation. There are no categories.  
  
9. In the **Available Categories and Operations**, select the **OnReceiveEcho** operation. Click **Add** to make the selected operations part of the generated WCF interface.  
  
10. Click **OK** to generate the WCF interface. This adds an application configuration file (app.config), a WCF interface (EchoAdapterBindingInterface.cs) and a WCF service (EchoAdapterBindingService.cs) to the project.  
  
11. Click **File** on the **Visual Studio** menu and choose **Save All**.  
  
## Test the Echo Adapter  
  
1.  In Solution Explorer, double-click the **EchoAdapterBindingService.cs** file.  
  
2.  In the Visual Studio editor, inside the **OnReceiveEcho** method, replace the existing implementation with the following:  
  
    ```csharp  
    System.Console.WriteLine("path = " + path + ", len = " + length);  
    ```  
  
3.  In Solution Explorer, double-click the **Program.cs** file.  
  
4.  In the Visual Studio editor, inside the Main method, add the following code to host the WCF service.  
  
    ```csharp  
    try  
    {  
        // Create a ServiceHost for the EchoServiceImpl type  
        // and use the base address from app.config  
        System.ServiceModel.ServiceHost host = new System.ServiceModel.ServiceHost(typeof(EchoAdapterBindingNamespace.EchoAdapterBindingService));  
  
        // Open the ServiceHost to start listening for messages  
        host.Open();  
  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost  
        host.Close();  
    }  
    catch (TimeoutException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    catch (System.ServiceModel.CommunicationException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    ```  
  
5.  In Visual Studio, on the **File** menu, click **Save All**.  
  
6.  Press F5 to start the sample.  
  
7.  Drop a file with the "txt" extension into the directory specified earlier in this tutorial. You should see information similar to the following in the program output window:  
  
     **The service is ready.**  
  
     **Press \<ENTER\> to terminate service.**  
  
     **path = file:///C:/Tutorial/InboundTest/InboundTest.txt, len = 229179**  
  
8.  Press the Enter key to stop the service.  
  
## What Did I Just Do?  
 In this step, you created a test application for the inbound operation exposed by the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service. Finally, you ran the test application.  
  
## Next Steps  
 This is the last step of the tutorial. For more information about Inbound operations, see `Microsoft.ServiceModel.Channels.Common.IInboundHandler`. To see an example SDK that demonstrates how to host a WCF Service that requires authentication, download the echo adapter and test code at [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).  
  
## See Also  
 [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)