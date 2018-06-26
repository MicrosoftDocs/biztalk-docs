---
title: "Loans Processing Using Business Rules (BizTalk Server Sample) | Microsoft Docs"
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
ms.assetid: 3e1c80c6-adc1-4a0f-83fd-409ce1b8f21f
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Loans Processing Using Business Rules (BizTalk Server Sample)
The Loans Processing Using Business Rules sample demonstrates how to use a set of rules managed within an orchestration, and how to use a combination of inputs known as facts, to calculate settings for some fields within a document being processed. Facts can be the result of calling a .NET-based assembly, the values retrieved from the XML of the message, or the data retrieved from a database. The sample also demonstrates how you can change the rules at any time, affecting subsequent calculations without the need to redeploy.  

## What This Sample Does  
 This sample demonstrates these capabilities within the context of a simplified loan processing scenario. BizTalk Server orchestration picks up and processes a loan application, also known as a loan case, in XML message format. This orchestration uses the Business Rule Engine to evaluate incoming messages according to the rules, modifying the message with the result of the application of the rules, and then writing the message as a file to an output folder.  

 Based on facts from several sources, including the message being processed, this sample sets the **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus** elements of the message being processed.  

## Where to Find This Sample  
 \<*Samples Path*\>\Business Rules\Loans Processing using Business Rules\  

 The following table shows the files in this sample and describes their purpose.  


|                                                                                    File(s)                                                                                    |                                                                                                                Description                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                   Case.xsd                                                                                    |                                                                                 Schema file for inbound loan applications, otherwise known as loan cases.                                                                                  |
|                                                                                  Cleanup.bat                                                                                  |                   Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.                   |
|                                                                           Create_CustInfo_Table.sql                                                                           |                                                                              SQL script for creating the CustInfo table in the SQL Northwind sample database.                                                                              |
|                                                                           LoanProcessorBinding.xml                                                                            |                                                                                               Used for automated setup such as port binding.                                                                                               |
|                                                                   LoansProcessor.btproj, LoansProcessor.sln                                                                   |                                                                                            BizTalk project and solution files for this sample.                                                                                             |
|                                                                             My Sample Service.odx                                                                             |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for this sample.                                                              |
|                                                                                sampleLoan.xml                                                                                 |                                                               Sample input file, with empty values for the four status elements at the end of the XML structure in the file.                                                               |
|                                                                                   Setup.bat                                                                                   |                                                                                                 Used to build and initialize this sample.                                                                                                  |
|         In the \CreateRules folder:<br /><br /> App.ico, AssemblyInfo.cs, Case.xsd, CreateLoanProcessingPolicy.csproj, CreateLoanProcessingPolicy.sln, WriteToBRL.cs          | Visual C# project, solution, source, and related files used to create the application that programmatically creates the rules in the set. For examples of programmatically building sets of rules, refer to the source file WriteToBRL.cs. |
| In the \myFactRetriever folder:<br /><br /> AssemblyInfo.cs<br /><br /> FactRetrieverForLoansProcessing.cs<br /><br /> myFactRetriever.csproj<br /><br /> myFactRetriever.sln |                 Visual C# project, solution, source, and related files used to create an assembly that you use to retrieve information from the CustInfo table added earlier to the Northwind sample SQL Server database.                  |

## Building and Initializing This Sample  

#### To build and initialize the Loans Processing Using Business Rules sample  

1. Make sure that you have the Northwind database on your machine.  

   > [!IMPORTANT]
   >  To run this sample, you must have the Northwind SQL Server sample database. [Download](https://www.microsoft.com/download/details.aspx?id=23654), and install. 

2. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\Business Rules\Loans Processing using Business Rules  

3. Run the file Setup.bat, which performs the following actions:  

   - Cleans up the GAC to eliminate any residual data from previous runs of this sample.  

   - Compiles and deploys the fact retriever program, myFactRetreiever.dll.  

   - Using the SQL script file Create_CustInfo_Table.sql, adds a table named CustInfo to the Northwind sample SQL database.  

   - Cleans up the shared SQL rule store to eliminate residue of previous runs of this sample.  

   - Creates, publishes, and deploys the most recent version (1.0) of the loans processing rule set.  

     > [!NOTE]
     >  You can use the Business Rule Composer tool supplied with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to examine the rules that have been set programmatically.  

   - Creates the input (In) and output (Out) folders for this sample.  

   - Compiles and deploys the remaining [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, including the BizTalk project that contains the orchestration you use to coordinate this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warnings when creating and binding ports:  
     >   
     >  `Warning: Receive handler not specified for receive location "LoansProcessor_1.0.0.0_LoansProcessor.My_Sample_Service_Incoming_ReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "LoansProcessor.My_Sample_Service"; updating with first available host.`  
     >   
     >  You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

   - Enlists and starts the orchestration.  

> [!NOTE]
>  If your BizTalk host name is not BizTalkServerApplication, modify the file Setup.bat and the file LoanProcessorBinding.xml to reflect the proper host name.  
> 
> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
> 
> [!NOTE]
>  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assemblies.  
> 
> [!NOTE]
>  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running This Sample  

#### To run the Loans Processing Using Business Rules sample  

1. Paste a copy of the file sampleLoan.xml into the **\In** folder.  

2. Observe the .xml file created in the folder **Out**. It contains the input XML message with data added to the following four status elements at the end of the XML structure: **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus**.  

   You can use the Business Rule Composer tool to change the rules in the rule set, and then redeploy those rules.  

#### To use the Business Rule Composer tool to change one or more of the rules in a rule set  

1. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rule Composer**.  

   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  

2. In the **SQL Server** dialog box, click **OK** to connect to the rule store.  

3. In **Policy Explorer**, below the node **LoanProcessing**, right-click the **Version 1.0 – Deployed** node, and then click **Copy**.  

4. Right-click **LoanProcessing**, and then click **Paste**.  

5. Change any rule or action in a way that will result in different values for the **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus** elements. Ensure that you also change the value of the negation portion (essentially, the **Else** clause) of any rule that you choose to change.  

    The following table shows the set of rules used by this sample. Unless specifically mentioned otherwise, facts are from the incoming XML message. The string (db) indicates a database as the source of a fact.  


   |  Rule number   |        Rule name        |                                                                             Description                                                                             |
   |----------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       1        |   Income Status Rule    |                                       IF **BasicSalary** + **OtherIncome** > 0<br /><br /> THEN **IncomeStatus** = **Valid**                                        |
   |       2        | Commitments Status Rule | IF **ID** == **ID (db)**<br /><br /> AND<br /><br /> IF **CreditCardBalance (db)** > 500<br /><br /> THEN **CommitmentsStatus** =<br /><br /> "Compute Commitments" |
   |       3        | Employment Status Rule  |                                  IF **EmploymentType &#124; TimeInMonths** > 18<br /><br /> THEN **EmploymentStatus** = **Valid**                                   |
   |       4        |  Residency Status Rule  |                                  IF **PlaceOfResidence &#124; TimeInMonths** > 18<br /><br /> THEN **ResidencyStatus** = **Valid**                                  |
   | !1, !2, !3, !4 |     Negation Rules      |    Conditions that are a logical **NOT** of the corresponding condition described in rules 1–4. Resulting actions are a change in the string that is being set.     |


6. Right-click the **Version 1.1(not saved)** node, and then click **Save**.  

7. Right-click the **Version 1.1** node, and then click **Publish**.  

8. Right-click the **Version 1.1** node, and then click **Deploy**.  

9. Wait for 60 seconds for the changes to propagate to the shared SQL Server rule store.  

10. Paste a copy of the file sampleLoan.xml into the folder **In**.  

11. Observe the .xml file created in the folder **Out**. It contains the input XML message with data added to the following four status elements at the end of the XML structure: **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus**. The data added to these elements will differ, or not, from the previous run, based on the nature of the changes made in step 5in this procedure.  

## Comments  
 If you want to view the tracking information for this sample, you must undeploy and then redeploy the relevant rule set (Loans Processing) by using the Business Rules Engine Deployment Wizard.  

 This sample demonstrates how you can use business rules to apply business policies in the form of rules within an orchestration. It also demonstrates how you can change the policies, and have the change in the policy reflected dynamically within the orchestration without having to recompile or redeploy the orchestration solution.  

 Input loan cases to this sample are XML messages that have the following structure:  

```  
    Name  
    ID  
    Income  
        BasicSalary  
        OtherIncome  
    EmploymentType  
        TimeInMonths  
    PlaceOfResidence  
        TimeInMonths  
    CommitmentsStatus  
    IncomeStatus  
    EmploymentStatus  
    ResidencyStatus  
```  

## See Also  
 [Business Rules (BizTalk Server Samples Folder)](../core/business-rules-biztalk-server-samples-folder.md)