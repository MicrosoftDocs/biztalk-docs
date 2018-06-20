---
title: "Business Rules Hello World2 (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, business rules"
  - "business rules, examples"
ms.assetid: 2a88a2a0-8cb6-4373-8441-0ab04345a477
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Business Rules Hello World2 (BizTalk Server Sample)
The Business Rules Hello World2 sample extends the Business Rules Hello World1 sample by demonstrating how to version, publish, and deploy the XML rule set to the shared SQL rule store, and how to run the policy using the **Policy** object provided by the Business Rules Framework. The sample also demonstrates dynamic policy updates in action.  
  
> [!NOTE]
>  This sample assumes that the user has installed the Rule Engine Update Service and Business Rules Components (located under the "Additional Software" node) during installation of the product.  
  
> [!NOTE]
>  You use **Policy** objects to integrate the rule engine into any stand-alone application. The **Policy** object is the abstraction through which multiple rule engine instances are managed, rule sets are retrieved and instantiated from the shared SQL store, and updates to the policies are retrieved and published to the hosting application.  
  
 For basic information about the rule set defined, and sample facts constructed by this sample, see [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md).  
  
## What This Sample Does  
 This sample creates an executable that performs the following sequence of steps:  
  
1.  Calls the method **CreateRuleset** to build the rule set described in the Remarks section.  
  
2.  Calls the method **SaveToFile** to demonstrate saving a rule set to a file.  
  
3.  Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.  
  
4.  Deploys the rule set to a shared SQL rule store.  
  
5.  Runs the rule set by using a **Policy** object, and by using the same set of sample facts used in the Business Rules Hello World1 sample.  
  
6.  Pauses, enabling you to modify the rule set file **SampleRuleStore.xml** in a specific way.  
  
7.  Runs the rule set again using a **Policy** object, the now modified rule set, and again with the same set of sample facts used in the Business Rules Hello World1 sample.  
  
8.  Cleans up by deleting the rule set file and the deployed rule set records in preparation for subsequent running of the sample.  
  
> [!NOTE]
>  For important information about all samples in this SDK, see [Samples](../core/samples-in-the-sdk.md).  
  
## Where to Find This Sample  
 *\<Samples Path\>*\Business Rules\Business Rules Hello World2\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld2.csproj, BusinessRulesHelloWorld2.sln|Project, solution, and related files for the portion of this sample that creates, saves, loads, deploys, and executes a rule set.|  
|HelloWorld2.cs|Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, loading a rule set from a file, deploying the rule set to a shared Microsoft SQL Server rule store, and then running the rule set by using a **Policy** object.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|SampleDocumentInstance.xml|Sample input file that conforms to the schema defined in the file SampleSchema.xsd.|  
|SampleSchema.xsd|Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file Class1.cs.|  
|Setup.bat|Used to build and initialize this sample.|  
|In the \HelloWorld2Library folder:<br /><br /> AssemblyInfo.cs, HelloWorld2Library.csproj, HelloWorld2Library.sln|Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.|  
|In the \HelloWorld2Library folder:<br /><br /> HelloWorld2LibraryClass.cs|Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.|  
  
### To build and initialize the Business Rules Hello World2 sample  
  
1. In a command window, navigate to the following folder:  
  
    *\<Samples Path\>*\Business Rules\Business Rules Hello World2\  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  
  
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
   > 
   > [!NOTE]
   >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assemblies.  
   > 
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
### To run the Business Rules Hello World2 sample  
  
1.  In a command window, navigate to the following folder:  
  
     *\<Samples Path\>*\Business Rules\Business Rules Hello World2\bin\Debug\  
  
2.  In the command window, type the name of the file for this sample (**BusinessRulesHelloWorld2.exe**), and then press ENTER.  
  
## Hello World2 Output  
 Based on the nature of the created rule set, described in the Comments section of [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md), if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Deploying the ruleset ...  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...  
Grabbing the policy ...  
Executing the policy...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
The major version of the policy was: 1  
The minor version of the policy was: 0  
Press the ENTER to continue after updating the policy...  
```  
  
> [!NOTE]
>  The output shown in bold is the output produced by the sample business object, defined by the files in the **HelloWorld2Library** folder that the rule set references. At this point, the application is left waiting in this state.  
  
 The next part of running the sample involves using the Business Rules Composer to change the business rules.  
  
#### To use the Business Rules Composer to change the business rules  
  
1. To open the Business Rules Composer, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Composer**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2. If a SQL Server dialog box appears on the computer running SQL Server, click **OK** to connect to the rule store.  
  
3. In **Policy Explorer**, below the **SampleRuleSet** node, right-click the node **Version 1.0 – Deployed**, and then click **Copy**.  
  
4. Right-click **SampleRuleSet**, and then click **Paste (Policy Version)**.  
  
5. You can change the rule condition and action to meet your needs. For this procedure, click **rule1** in **Version 1.1 (not saved)**. In the right pane, right-click **Conditions**, and then click **Add Logical NOT**. Adding a **Logical NOT** operation to **Not Equal** to predicate is equivalent to using an **Equal** predicate.  
  
6. Right-click the node **Version 1.1(not saved)**, and then click **Save**. Right-click again, and then click **Publish**. Right-click a third time and click **Deploy**.  
  
7. In the paused command window asking you to press any key to continue after updating the policy, press any key.  
  
   Output (assuming you changed the rule by adding a logical Not) from the executable file BusinessRulesHelloWorld2.exe continues as follows:  
  
```  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...         
Grabbing the policy ...         
Executing the policy...         
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5         
The major version of the policy was: 1         
The minor version of the policy was: 1         
Press ENTER to continue after updating the policy...         
```  
  
 Notice how the output has changed:  
  
-   The output line in the method **MySampleMethod** only prints once now, for the instance of the **MySampleBusinessObject** class for which the **MyValue** property is equal to 1, rather than the previous rule of printing when the **MyValue** property is not equal to 1.  
  
-   The minor version number of the policy is now 1.  
  
## See Also  
 [Business Rules (BizTalk Server Samples Folder)](../core/business-rules-biztalk-server-samples-folder.md)