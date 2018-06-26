---
title: "Medical Claims Processing and Testing Policies (BizTalk Server Sample) | Microsoft Docs"
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
ms.assetid: c0bdf7b7-3e55-4560-a5a8-00c5b661d14d
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Medical Claims Processing and Testing Policies (BizTalk Server Sample)
The Medical Claims Processing and Testing Policies sample demonstrates how to create a rule set containing multiple rules that examine facts derived from a database table and the inbound document, and which use .NET-based objects to record the results of the claims processing.  
  
 This sample demonstrates end-end execution of the claim processing scenario using a simple .NET-based application that uses the Business Rule Engine to run a medical claims rule set against incoming claims to determine the STATUS of the claim and the REASON for the status.  
  
> [!NOTE]
>  This sample also demonstrates how to trace Business Rule Engine execution using a debug trace file.  
  
## What This Sample Does  
 This sample applies the following sequence of rules to submitted claims:  
  
1.  Rejects the claim if the total amount claimed exceeds the maximum permitted by the policy.  
  
2.  Rejects the claim if the client has stayed in hospitals more nights than the maximum permitted by the policy.  
  
3.  Rejects the claim if the date on the claim is in the future.  
  
4.  Rejects the claim if the policy is not valid.  
  
5.  Sends a lead to the sales department with the policy ID and customer name if the policy has expired.  
  
6.  Otherwise, approves the claim.  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|Create_PolicyValidity_Table.sql|SQL script that adds a new table named PolicyValidity to the Northwind sample database.|  
|Setup.bat|Used to build and initialize this sample.|  
|In the \Claims folder:<br /><br /> AssemblyInfo.cs, Claims.csproj, Claims.sln, Claims.cs|Project, solution, source, and related files for the portion of this sample that records the result of the claims processing, called the **THEN** portion of a rule.|  
|In the \FactRetrieverForClaimsProcessing folder:<br /><br /> AssemblyInfo.cs, FactRetrieverForClaimsProcessing.cs, FactRetrieverForClaimsProcessing.csproj, FactRetrieverForClaimsProcessing.sln|Project, solution, source, and related files for the portion of this sample that provides the long-term fact retriever that retrieves information from the PolicyValidity table created by this sample.|  
|In the \RulesForMedicalClaims folder:<br /><br /> App.ico, AssemblyInfo.cs, RulesForMedicalClaims.cs, RulesForMedicalClaims.csproj, RulesForMedicalClaims.sln|Project, solution, source, and related files for the portion of this sample that constitutes the main executable for this sample (RulesForMedicalClaims.exe), and which programmatically defines and stores the rule set, constructs sample facts, and then runs the rule set using a **PolicyTester** object.|  
|In the \RulesForMedicalClaims folder:<br /><br /> MedicalClaims.xsd|Schema file that defines the structure of the sample medical claims submitted to this sample.|  
|In the \RulesForMedicalClaims folder:<br /><br /> sampleClaim.xml|Sample input file that conforms to the schema defined in the file MedicalClaims.xsd.|  
  
## Building and Initializing This Sample  
  
#### To build and initialize the Medical Claims Processing and Testing Policies sample  
  
1. Make sure that you have the Northwind database on your machine.  
  
   > [!IMPORTANT]
   >  To run this sample, you must have the Northwind SQL Server sample database. [Download](https://www.microsoft.com/download/details.aspx?id=23654), and install. 
  
2. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\  
  
3. Run the file Setup.bat, which performs the following actions:  
  
   - Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, including Claims.dll, FactRetrieverForClaimsProcessing.dll, and RulesForMedicalClaims.dll.  
  
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
   > 
   > [!NOTE]
   >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assemblies.  
  
   - Runs the provided SQL script Create_PolicyValidity_Table.sql using SQL Query Analyzer. The script creates the table, PolicyValidity, with two sample rows in the Northwind sample database. This table has two columns: ID and PolicyStatus.  
  
   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.  
  
   - Enables the receive location, and starts the send port.  
  
   - Enlists and starts orchestration.  
  
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running This Sample  
  
#### To run the Medical Claims Processing and Testing Policies sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\RulesForMedicalClaims\bin\Debug\  
  
2. Run the file RulesForMedicalClaims.exe on the command line.  
  
   > [!NOTE]
   >  You can change the values of individual elements in the sample claim file sampleClaim.xml and run the sample repeatedly. The expected outputs for different values in these elements are shown in the list that follows.  
  
   Output scenarios based on various combinations of values in the submitted sample claims file are:  
  
-   For a claim whose amount exceeds $1000, the following output is obtained:  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of claim has exceeded Policy limit  
    ```  
  
-   For a claim whose number of nights exceeds 10, the following output is obtained:  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of Nights has exceeded Policy limit  
    ```  
  
-   For a claim whose date is not valid (date > current date), the following output in obtained:  
  
    ```  
    Status:  REJECTED!  
    Reason:  Cannot submit claims for future dates!  
    ```  
  
-   For a claim with a policy ID that is not valid (for example, by changing the **ID** element to have a value of 2) because of policy expiration, the following output is obtained:  
  
    ```  
    Sending to Renewal Department for Customer Smir with Policy # 2  
    Status:  REJECTED!  
    Reason:  Policy ID is invalid  
    ```  
  
-   For a claim that is valid, the following output is obtained:  
  
    ```  
    Status:  Claim Accepted!  
    Reason:  
    ```  
  
    > [!NOTE]
    >  A text file, outputtrace.txt, is created in the folder ...\RulesForMedicalClaims\bin\Debug folder every time you run this sample. It contains a debug trace of rule execution, and it is created after every execution cycle under the folder \RulesForMedicalClaims\bin\Debug. You can examine this file to see the output trace of rule execution.  
  
## Comments  
 The fact sources used in the rule set evaluation are:  
  
- A long-term fact retriever, a .NET-based application that implements the **IFactReriever** interface, is built in the folder FactRetrieverForClaimsProcessing. It is used by the medical claims processing policy to retrieve data (in the form of a dataset) from the PolicyValidity database and to use in rule condition evaluation.  
  
- The claim is in the form of an XML document that contains the following information, stored in sibling elements: Name, ID, Amount, Nights, and Date.  
  
- A .NET-based class library (Claims), with a **ClaimResults** class is used to record the STATUS and REASON of the claim using properties, and to send a lead (if the policy is not valid) by invoking the **SendLeads** method with ID and name as parameters.  
  
  Based on these fact sources, you can informally describe the rules defined for this scenario as follows:  
  
1. Check to see if the incoming claim is valid. The claim is not valid if the amount is over the allowable limit for a claim, if the policy has expired (verified by checking the database table), if the number of nights has exceeded the maximum allowable limit, and if the claim is made for a future date. If the claim has been determined to be not valid, set the STATUS and REASON of the claim appropriately.  
  
2. If the policy ID of the incoming claim has expired, send a lead (with policy ID and customer name) to the policy renewal department.  
  
3. If the claim is valid, set the STATUS and REASON of the claim appropriately.  
  
   A more formal representation of the rules and their term bindings is as follows:  
  
-   **Rule 1. Amount check**  
  
    ```  
    IF Amount in the XML document is > 1000  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"\  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Rule 2. Nights spent in the hospital**  
  
    ```  
    IF number of nights in the XML document is > 10  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Rule 3. Date validity**  
  
    ```  
    IF date on the incoming XML claim is > Today  
      AND   
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Cannot submit claims in the future!"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Rule 4. Policy validity**  
  
    ```  
    IF Policy is invalid for the ID in the XML claim (check database)  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Policy Invalid"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Rule 5. Sales lead**  
  
    ```  
    IF Claim.ClaimResults.Reason = "Policy invalid"  
  
    THEN send a lead to the policy department by invoking the function Claim.ClaimResults.SendLead with customer ID and Name from the incoming XML document.  
  
    ```  
  
-   **Rule 6. Claim accepted**  
  
    ```  
    IF Claim.ClaimResults.Status = null  
  
    THEN Set the claim status to be valid  
         &&  
         Send the lead to the sales department  
  
    ```  
  
## See Also  
 [Business Rules (BizTalk Server Samples Folder)](../core/business-rules-biztalk-server-samples-folder.md)