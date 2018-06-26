---
title: "Business Rules Hello World1 (BizTalk Server Sample) | Microsoft Docs"
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
ms.assetid: 0623ad20-96cc-430e-bb36-35431a5d17ee
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Business Rules Hello World1 (BizTalk Server Sample)
The Business Rules Hello World1 sample demonstrates how to create a BizTalk rule set, save it to a file (SampleRuleSet.xml), load it, and run it based on a sample set of facts. The sample rule set contains a simple rule that involves an XML element, and .NET-based objects (properties and members) as terms in rule definition.  
  
## What This Sample Does  
 This sample creates an executable that performs the following sequence of steps:  
  
1.  Calls the method **CreateRuleset** to build the rule set described in the Remarks section.  
  
2.  Calls the method **SaveToFile** to demonstrate saving a rule set to a file.  
  
3.  Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.  
  
4.  Constructs sample facts against which to run the rule set.  
  
5.  Runs the rule set against the sample facts, producing screen output.  
  
6.  Pauses, enabling you to examine the rule set file SampleRuleStore.xml.  
  
7.  Cleans up by deleting the rule set file in preparation for subsequent runs of the sample.  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Business Rules\Business Rules Hello World1\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld1.csproj, BusinessRulesHelloWorld1.sln|Project, solution, and related files for the portion of this sample that creates, saves, loads, and runs a rule set.|  
|HelloWorld1.cs|Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, and loading a rule set from a file. Also contains surrounding code that calls these methods and then runs the created rule set.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|SampleDocumentInstance.xml|Sample input file that conforms to the schema defined in the file SampleSchema.xsd.|  
|SampleSchema.xsd|Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file HelloWorld1.cs.|  
|Setup.bat|Used to build and initialize this sample.|  
|In the \MySampleLibrary folder:<br /><br /> AssemblyInfo.cs, MySampleLibrary.csproj, MySampleLibrary.sln|Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.|  
|In the \MySampleLibrary folder:<br /><br /> MySampleLibraryClass.cs|Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.|  
  
## Building and Initializing This Sample  
 Use the following procedure to build and initialize the Business Rules Hello World1 sample.  
  
#### To build and initialize this sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Business Rules\Business Rules Hello World1\  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  
  
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
   > 
   > [!NOTE]
   >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assemblies.  
   > 
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running This Sample  
 Use the following procedure to run the Business Rules Hello World1 sample.  
  
#### To run this sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Business Rules\Business Rules Hello World1\bin\Debug\  
  
2. In the command window, type the name of the executable file for this sample (BusinessRulesHelloWorld1.exe), and then press ENTER.  
  
   > [!NOTE]
   >  While running, this sample produces the rule set file SampleRuleStore.xml in the **bin\Debug** folder. When the executable pauses, waiting for you to press ENTER to finish, you can examine the contents of this file. Remember to close it before pressing any key to finish. Otherwise, the executable may not be able to delete it in preparation for subsequent runs of the sample.  
  
   Based on the nature of the created rule set, if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
> [!NOTE]
>  The output shown in bold, both in the preceding code and in the code that follows, is the output produced by the sample business object, defined by the files in the **MySampleLibrary** folder, which is referenced by the rule set.  
  
 If you change the value associated with the **ID** element in the sample input file **SampleDocumentInstance.xml** from one (1) to two (2), the output would change as follows:  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
 You will not get an output line for any objects of the **MySampleBusinessObject** class that have their **MyValue** property set to a value (during construction) that matches the value associated with the **ID** element in the sample input file SampleDocumentInstance.xml.  
  
## Comments  
 The rule created programmatically within the **CreateRuleset()** method shows:  
  
 **IF**  
  
 **MySampleBusinessObject.MyValue** is not equal to the value of the **ID** element in the XML document.  
  
 **THEN**  
  
 **MySampleBusinessObject.MySampleMethod(int)** with an integer parameter, hard coded to the constant five (5) in this case. This method produces the output lines that begin **MySampleBusinessObject Class –-**.  
  
 This rule depends on the following:  
  
- A **MySampleBusinessObject** class with a public property called **MyValue** and a public method called **MySampleMethod** (that takes in an integer parameter).  
  
- An XML schema definition language (XSD) schema that defines an XML document that contains an **ID** element.  
  
  You define rules in terms of classes and schemas, but during execution, object instances of the relevant classes and document instances of the relevant schemas are required. You evaluate the rules against these run-time instances (known as facts). In this sample, the facts are multiple instances of the **MySampleBusinessObject** object, constructed with different values for their **MyValue** property, and a single XML instance of the defined schema that contains a value for the **ID** element.  
  
## See Also  
 [Business Rules (BizTalk Server Samples Folder)](../core/business-rules-biztalk-server-samples-folder.md)