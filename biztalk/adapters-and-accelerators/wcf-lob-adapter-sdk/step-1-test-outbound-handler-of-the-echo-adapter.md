---
description: "Learn more about: Step 1: Test Outbound Handler of the Echo Adapter"
title: "Step 1: Test Outbound Handler of the Echo Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad4a8164-a584-436f-b20b-4c884f6e2b37
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Test Outbound Handler of the Echo Adapter
![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Time to Complete:** 15 minutes  
  
 In this step, you will test the three outbound operations provided by the Echo Adapter. You will do this using Visual Studio, the Add Adapter Service Reference Visual Studio Plug-In and custom code.  
  
## Prerequisites  
 To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).  
  
## Create a Visual Studio project  
  
1.  Start Visual Studio.  
  
2.  In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Project types**|Click **Visual C#**.|  
    |**Templates**|Click **Console Application**.|  
    |**Name**|Type **ConsumeEchoAdapter_Outbound**.|  
    |**Location**|Type **C:\Tutorials**.|  
    |**Solution Name**|Type **ConsumeEchoAdapter_Outbound**.|  
  
4.  Click **OK**.  
  
5.  In Visual Studio, on the **File** menu, click **Save All**.  
  
## Browse, search, and generate the WCF client  
  
1.  In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Outbound** project, then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.  
  
2.  In the **Add Adapter Service Reference** screen, choose a binding. This is done by choosing **echoAdapterBindingV2**.  
  
3.  Next, configure the adapter and connection properties by clicking **Configure…**.  This will bring up the **Configure Adapter** screen.  
  
4.  In the **Configure Adapter** screen, select the **URI Properties** tab to configure connection properties. Notice that the custom Echo Adapter categories are shown — **Connection** and **Format**. Under the **Format** category, change **EchoInUpperCase** to **True**.  
  
5.  In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties. Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown. Under the **Misc** category, change **Count** to **3**.  
  
6.  Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.  
  
7.  Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports). After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.  
  
8.  In the Category Tree, click **Main Category**. This will populate the list of available categories and operations with three outbound operations. There will be no categories.  
  
    > [!NOTE]
    >  The default contract type is Outbound. Category results will match this contract type.  
  
9. In the **Available Categories and Operations**, select all three operations. When there are a large number of operations, you might use search to narrow down the selection; in this case, there are only three. Click **Add** to make the selected operations part of the generated WCF interface.  
  
10. Click **OK** to generate the WCF interface. This will add an application configuration file (app.config) and a WCF client proxy (EchoAdapterBindingClient.cs) to the project.  
  
11. Click **File** on the Visual Studio menu and choose **Save All**.  
  
## Configure adapter authentication  
  
1.  In Visual Studio Solution pane, double-click **app.config**.  
  
2.  Find the `address` attribute in the `endpoint` element. It should look similar to the following:  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=False&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
     Change **enableAuthentication** from **False** to **True** as shown below. This will require the calling application to pass credentials to the adapter.  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=True&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
3.  Save the solution by clicking **File** on the Visual Studio menu and choosing **Save All**.  
  
## Create a sample XML file  
  
1.  Start an instance of Notepad. Using the Start menu, click **All Programs** &#124; **Accessories** and then choose **Notepad**.  
  
2.  Copy the following sample data into the Notepad editor.  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <ns0:greeting xmlns:ns0="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes">  
      <ns0:address>  
        <ns0:street1>123 Microsoft Way</ns0:street1>  
        <ns0:street2>Building # 4599</ns0:street2>  
        <ns0:city>Redmond</ns0:city>  
        <ns0:state>WA</ns0:state>  
        <ns0:zip>98052</ns0:zip>  
      </ns0:address>  
      <ns0:greetingText>Welcome to Redmond!</ns0:greetingText>  
    </ns0:greeting>              
    ```  
  
3.  On the Notepad menu, click **File** and then choose **Save As…**. Type in "CustomGreetingInstance.xml" for the file name and choose Unicode for the encoding and then save it to the project directory or another suitable location. Note the full path and filename for later reference.  
  
4.  Close the text editor when the file is successfully saved.  
  
## Test the Echo Adapter  
  
1.  In Solution Explorer, double-click the **Program.cs** file.  
  
2.  In the Visual Studio editor, inside the **Main** method, add the following line of code to create an instance of the generated WCF client.  
  
    ```csharp  
    EchoOutboundContractClient client = new EchoOutboundContractClient();  
    ```  
  
3.  Now add code that establishes credentials for the adapter. When authentication is enabled in the Echo Adapter, it will check for the existence of a user name but will not check the value.  
  
    ```csharp  
    // pass client credentials  
    client.ClientCredentials.UserName.UserName = "username";  
    ```  
  
4.  Continue by adding code to invoke the EchoStrings operation.  
  
    ```csharp  
    // Invoke EchoStrings()  
    Console.WriteLine("Invoking EchoStrings() method against the adapter...");  
    string[] response = client.EchoStrings("Bonjour!");  
    foreach (string data in response)  
    {  
        Console.WriteLine(data);  
    }  
    ```  
  
5.  Continue by adding code to invoke the EchoGreetings operation.  
  
    ```csharp  
    // Invoke EchoGreetings()  
    Console.WriteLine("\nInvoking EchoGreetings() method against the adapter...");  
    microsoft.adapters.samples.echov2.Types.Greeting greeting = new microsoft.adapters.samples.echov2.Types.Greeting();  
    greeting.id = Guid.NewGuid();  
    greeting.sentDateTime = DateTime.Now;  
    greeting.greetingText = "Hello World!";  
    greeting.name = new microsoft.adapters.samples.echov2.Types.Name();  
    greeting.name.salutation = microsoft.adapters.samples.echov2.Types.Salutation.Miss;  
    greeting.name.firstName = "Jane";  
    greeting.name.middleName = "Z.";  
    greeting.name.lastName = "Smith";  
    microsoft.adapters.samples.echov2.Types.Greeting[] greetingArray = client.EchoGreetings(greeting);  
    foreach (microsoft.adapters.samples.echov2.Types.Greeting data in greetingArray)  
    {  
        Console.WriteLine(data.id + " " + data.sentDateTime + " " + data.greetingText + " " + data.name.firstName );  
    }  
    ```  
  
6.  Continue by adding code to invoke the EchoCustomGreetingsFromFile operation.  
  
    ```csharp  
    // Invoke EchoCustomGreetingFromFile()  
    Console.WriteLine("\nInvoking EchoCustomGreetingFromFile() method against the adapter ...");  
    // Copy the sample data from CustomGreeting-instance.xml file and place in appropriate folder  
    // as specified in the operation parameter  
    microsoft.adapters.samples.echov2.PreDefinedTypes.CustomGreeting   
    // change the Uri to point to the greeting instance xml file you created  
    customGreeting = client.EchoCustomGreetingFromFile(new Uri(@"c:\CustomGreetingInstance.xml"));  
    Console.WriteLine(customGreeting.greetingText + " " + customGreeting.address.city);  
    client.Close();  
    Console.ReadLine();  
    ```  
  
7.  In the EchoCustomGreetingsFromFile test code, make sure the custom greeting uses the file you created in a previous procedure. Change the code to reflect the location of your file.  
  
8.  In Visual Studio, on the **File** menu, click **Save All**.  
  
9. Run the application. You should see output similar to the following:  
  
     **Invoking EchoStrings() method against the adapter...**  
  
     **Bonjour!**  
  
     **Bonjour!**  
  
     **Bonjour!**  
  
     **Bonjour!**  
  
     **Bonjour!**  
  
     **Invoking EchoGreetings() method against the adapter...**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**  
  
     **Invoking EchoCustomGreetingFromFile() method against the adapter ...**  
  
     **Welcome to Redmond! Redmond**  
  
10. Press the Enter key to stop the program.  
  
## What Did I Just Do?  
 In this step, you created a test application for the three outbound operations exposed by the Echo Adapter developed in Tutorial 1. To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service. Finally, you ran the test application.  
  
## Next Steps  
 To test the Inbound operation, proceed to [Step 2: Test Inbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md).  
  
## See Also  
  [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [Step 2: Test Inbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)
