---
title: "Tutorial: Creating an RE Override | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35ef1cdf-68af-4a49-a856-750512d34d9e
caps.latest.revision: 3
---
# Tutorial: Creating an RE Override
When your application uses a Transaction Integrator (TI) component, you can specify the remote environment (RE) used by the TI run-time environment. This tutorial describes how to create such an RE override, using the REOverride sample found in the Host Integration Server SDK. After you are finished with this tutorial, you will be able to:  
  
-   Set up SimHost  
  
-   Import a host application definition  
  
-   Create and deploy a host application interface  
  
-   Create an application that performs an RE override.  
  
## Compiling and Running the REOverride Sample  
 The following procedures describe how to compile and run the REOverride sample application. After you have run the application once, you can perform the tutorial to rebuild the sample in a step-by-step process.  
  
#### To start the primary instance of SimHost for the REOverride tutorial  
  
1.  Right-click **Start**, and then click **Explore**.  
  
2.  Locate the **SimHost** folder.  
  
     For this tutorial, the SimHost folder is located in \<*Installation directory*>\Program Files\Microsoft Host Integration Server\System.  
  
3.  Double-click **SimHost.exe**.  
  
     This starts the Microsoft Transaction Integrator Host Simulator. You can use the Host Simulator to simulate a host environment. For this tutorial, you will use it to act as a remote host operating over a TCP/IP CICS connection.  
  
4.  Click **Options**, and then click **Reset to default values**.  
  
5.  Click **Start TCP**.  
  
#### To start the secondary instance of SimHost for the REOverride tutorial  
  
1.  Double-click **SimHost.exe**.  
  
2.  Click **Options**, and then click **Reset to default values**.  
  
3.  In the **TCP/IP CICS ELM** dialog box, in the **Link Port** field, enter `6511`.  
  
4.  Make sure there are no duplicate port numbers being used by the Host Simulator.  
  
5.  Click **Start TCP**.  
  
#### To import the host application definitions for the REOverride tutorial  
  
1.  In TI Manager, expand the **Transaction Integrator** node.  
  
2.  Right-click the **Window-Initiated Processing** node, and then click **Import**.  
  
3.  On the **Welcome to the Import WIP Definitions Wizard** page, click **Next**.  
  
4.  On the **Define Import Characteristics** page, confirm that the **Use Original Definitions** option button is selected.  
  
5.  Use **Browse** to locate the **TIHostApplicationDef** folder, and then click **Next**.  
  
     The TIHostApplicationDef folder contains all of the relevant files for describing the host environment for this tutorial. The folder is located in \<*Installation directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\AppInt\REOverride\TIHostApplicationDef.  
  
6.  On the **Importing WIP Definitions** page, wait for the import to complete, and then click **Next**.  
  
     Note that the RE0Banking.Accounts.1 file is registered to the "SimHost ELM Link" host, and not to the "SimHost ELM Link Secondary" host.  
  
7.  On the **Completing the Import WIP Definitions Wizard** page, click **Finish**.  
  
#### To build and execute the REOverride sample  
  
1.  In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, click **Open**, and then click **Project/Solution**.  
  
2.  In the **Open Project** dialog box, locate the folder that contains the tutorial solution file.  
  
     For this tutorial, the tutorial solution file is located in \<*Installation directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\AppInt\REOverride.  
  
3.  Click **REOverride.sln**, and then click **Open**.  
  
4.  Click **Build**, and then click **Build Solution**.  
  
5.  Click **Debug**, and then click **Start Debugging**.  
  
     A console window appears and displays the output of the application. You should see one message for the primary host simulator, and one for the secondary host simulator.  
  
6.  End the debugging session by closing the console window.  
  
#### To cause the REOverride sample to fail  
  
1.  click **Stop TCP** on the secondary SimHost.  
  
2.  Build and execute the REOverride sample again.  
  
     The call to the primary SimHost will succeed, while the call with the RE Override will fail.  
  
## A Step-by-Step Guide to the RE Override Tutorial  
 After you have set up and run the REOverride sample, you can go back and rebuild the solution manually by creating the TI project, adding a [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] client object, importing the host definition file, deploying the .hdf file, and then creating and coding the application.  
  
### Step 1: Create a Transaction Integrator Project  
  
##### To create a new project for the RE Override tutorial  
  
1.  In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2.  In the **New Project** dialog box, in the **Project Types** pane, select **Host Integration Projects**.  
  
3.  In the **Templates** pane, select **Transaction Integrator Project**.  
  
4.  In the **Name** field, type `REOverrideTutorial`.  
  
5.  In the **Location** field, type the location where you want to save the tutorial, and then click **OK**.  
  
     For this tutorial, the location of the project will be \<*Installation directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration.  
  
### Step 2: Add a .NET Client Object  
  
##### To add a .NET client object  
  
1.  In Solution Explorer, right-click **REOverrideTutorial**, point to **Add**, and then click **Add .NET Client Library**.  
  
2.  In the **Add New Item** dialog box, confirm that **.NET Client Library** is selected in the **Templates** pane.  
  
3.  In the **Name** field, type `REOBanking`, and then click **Add**.  
  
4.  On the **.NET Client Library** page, click **Next**.  
  
5.  On the **Library** page, in the **Interface Name** field, type `GetBalance`, and then click **Next**.  
  
6.  On the **Remote Environment** page, in the **Programming Model** list, select **ELM Link**, and then click **Next**.  
  
7.  Click **Create**.  
  
### Step 3: Import the Host Definition File  
  
##### To import the host definition file  
  
1.  On the menu bar in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], click **View**, and then click **Properties Window**.  
  
2.  On the **REOBanking.dll** tab, right-click the **REOBanking** node, point to **Import**, and then click **Host Definition**.  
  
3.  On the **Welcome to the Import COBOL Wizard** page, click **Next**.  
  
4.  On the **Import COBOL Source File** page, click **Browse**, and then locate the **TIHostApplicationDef** folder.  
  
     For this tutorial, the TIHostApplicationDef folder is located at \<*Installation directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\REOBanking\TIHostApplicationDef.  
  
5.  Click the **GetBalance.cbl** file, click **Open**, and then click **Next**.  
  
6.  On the **Import Options** page, click **Next**.  
  
7.  On the **01 DFHCOMMAREA** page, select the check box next to the **DFHCOMMAREA** node, and then click **Next**.  
  
8.  Expand the **DFHCOMMAREA** node.  
  
9. Click the arrows next to the **name** field, and then click **In**.  
  
10. Click the arrows next to the **ACCNUM** field, and then click **In**.  
  
11. Click the arrows next to the **ACCBAL** field, and then click **Out**.  
  
12. Click **Next**.  
  
13. On the **Data Tables, Structures and Unions** page, click **Next**.  
  
14. On the **Completing the Import COBOL Wizard** page, click **Modify**.  
  
### Step 4: Save and Deploy the Interface  
  
##### To save and deploy the GetAInfo interface  
  
1.  On the **REOBanking.dll** tab, click the **GetBalance** node.  
  
2.  In the **Properties** window, click the **Include Context Parameters** field, and then click **True** in the list.  
  
3.  On the **File** menu, click **Save All**.  
  
4.  On the **REOBanking.dll** tab, click the **REOBanking** node.  
  
5.  In the **Properties** window, click the **Remote Environment** field, and then select **SimHost using ELM Link**.  
  
6.  On the **REOBanking.dll** tab, right-click the **REOBanking** node, and then click **Deploy**.  
  
### Step 5: Create a Visual Studio Project  
  
##### To create a Visual C# project for the tutorial  
  
1.  In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Add**, and then click **New Project**.  
  
2.  In the **Add New Project** dialog box, in the **Project Types** pane, click **Visual C#**.  
  
3.  In the **Templates** pane, click **Console Application**, and then click **OK**.  
  
### Step 6: Code the Client Application  
  
##### To code the C# application for the RE Override tutorial  
  
1.  In Solution Explorer, expand the **ConsoleApplication1** node.  
  
2.  Right-click **References**, and then click **Add Reference**.  
  
3.  In the **Add Reference** dialog box, click the **Browse** tab, and locate the **REOverride** folder.  
  
     For this tutorial, the REOverride folder is located at \<*Installation directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\WindowsInitiated\REOverride.  
  
4.  Click **REOBanking.dll**, and then click **OK**.  
  
5.  Add the following code to your Program.cs file:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.HostIntegration.TI;  
    using REOBanking;  
  
    namespace REOverride  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                object[] contextArray = null;  
                decimal Balance = 0.0m;  
                ClientContext TIClientContext = new ClientContext();  
                REOBanking.Accounts MyBankObj = new REOBanking.Accounts();  
                try  
                {  
                    MyBankObj.GetBalance("Kim Akers", "123456", out Balance, ref contextArray);  
                    Console.WriteLine("Account balance from the primary RE {0,9:C2}\n", Balance);  
                    TIClientContext.WriteContext("REOverride", "SimHost ELM Link Secondary", ref contextArray);  
                    MyBankObj.GetBalance("Kim Akers", "123456", out Balance, ref contextArray);  
                    Console.WriteLine("Account balance from the Secondary RE {0,9:C2}\n", Balance);  
                }  
  
                catch (Microsoft.HostIntegration.TI.CustomTIException Ex)  
                {  
                    Console.WriteLine("Exception: TI Runtime Error {0}", Ex.Message);  
                }  
                catch (Exception Ex)  
                {  
                    Console.WriteLine("Exception: {0}", Ex.Message);  
                    if (Ex.Message.StartsWith("ClassFactory cannot supply requested class", StringComparison.CurrentCultureIgnoreCase))  
                    {  
                        Console.WriteLine("Error: REOBanking object could not be created. Use TI Manager to ensure it is registered");  
                    }  
                }  
  
                Console.WriteLine("\nPress any key to continue...");  
                Console.Read();  
            }  
        }  
    ```  
  
6.  }On the **File** menu, click **Save All**.  
  
7.  Click **Build**, and then click **Build ConsoleApplication1**.  
  
8.  Click **Debug**, and then click **Start**.