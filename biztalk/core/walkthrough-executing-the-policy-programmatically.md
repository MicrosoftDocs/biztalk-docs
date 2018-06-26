---
title: "Walkthrough: Executing the Policy Programmatically | Microsoft Docs"
ms.custom: ""
ms.date: "2016-04-05"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6398e7af-2ed1-4596-879c-3b7d000b8de2
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Executing the Policy Programmatically
This walkthrough provides step-by-step procedures for invoking the policy you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough from a console application programmatically.  

## Prerequisites  
 You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.  

## Overview of This Walkthrough  
 This walkthrough contains two procedures, as described in the following table.  

|Procedure title|Procedure description|  
|---------------------|---------------------------|  
|To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method|Provides step-by-step instructions for invoking a policy by using the **Policy.Execute** method.|  
|To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method|Provides step-by-step instructions for invoking a policy by using the **RuleEngine.Execute** method.|  

### To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method  

1. Start **Microsoft Visual Studio**.  

2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  

3. In the **New Project** dialog box, do the following:  


   |             Use this              |                             To do this                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **Project types**         |                        Click **Visual C#**.                         |
   |           **Templates**           |                   Click **Console Application**.                    |
   |             **Name**              |                       Type **ConsoleClient**.                       |
   |           **Location**            |     Specify a folder where you want to save the project files.      |
   |         **Solution Name**         |                     Type **ConsoleClientSol**.                      |
   | **Create directory for solution** | Select this check box to create a directory for the solution files. |


4. Click **OK**. The **ConsoleClient** project should appear in Solution Explorer. If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.  

5. In Solution Explorer, right-click **References**, and then click **Add Reference**.  

6. Click **Browse**, browse to the **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.  

7. Add the following lines to the top of the **Program.cs** file after the existing `using` statements:  

   ```  
   //To use the XmlDocument class  
   using System.Xml;  
   //To use the TypedXmlDocument and Policy classes  
   using Microsoft.RuleEngine;   
   ```  

8. Add the following code to the **Main** function to create a **TypedXmlDocument** object based on the XML document:  

   ```  
   XmlDocument doc = new XmlDocument();  
   //Loading the XML from SamplePO.xml file.  
   //Change the directory as needed  
   doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
   TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
   ```  

9. Add the following code to the **Main** function to execute the policy:  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

10. Print the output XML to confirm that the value of the **Status** field is set to **Approved**. Note that unlike the Business Rule Composer, invoking the **Policy.Execute** method does not change the original document.  

    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  

11. On the **Build** menu, click **Build ConsoleClient**.  

12. Press CTRL+F5 to execute the application. Confirm that the value of the **Status** field is set to **Approved**.  

### To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method  

1.  In Solution Explorer, right-click **References**, and then click **Add Reference**.  

2.  Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.BizTalk.RuleEngineExtensions.dll**.  

3.  Comment out the following lines in the **Program.cs** file:  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

4.  Add the following code after the commented-out code to get access to the Rule Engine database:  

    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  

5.  Add the following code to get access to **RuleSetInfoCollection** for the ProcessPurchaseOrder policy:  

    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  

6.  Add the following code to create a **RuleSet** object based on the rule set information for the ProcessPurchaseOrder policy:  

    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  

7.  Add the following code to create the **RuleEngine** object:  

    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  

8.  Add the following code to assert the **TypedXmlDocument** object into the working memory of the rule engine:  

    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  

9. Now add the code to execute the policy by using the **RuleEngine.Execute** method:  

    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  

10. Make sure that the **Console.WriteLine** statement is the last statement in the **Main** function.  

11. On the **Build** menu, click **Build ConsoleClient**.  

12. Press CTRL+F5 to execute the application. Confirm that the value of the **Status** field is set to **Approved**.  

## Comments  

-   Complete code for the **Main** function to execute the ProcessPurchaseOrder policy by using the **Policy.Execute** method is as follows:  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    policy.Execute(txd);  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   Complete code for executing the ProcessPurchaseOrder policy by using the **RuleEngine.Execute** method is as follows:  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    engine.Assert(txd);  
    engine.Execute();  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   You may want to add a **Console.ReadLine()** statement at the end of the **Main** function so that the application waits for you to terminate the application.  

-   In this walkthrough, the client submits only one fact to the ProcessPurchaseOrder policy. If the client needs to submit more than one fact to a policy, it needs to create an array of facts and use the overloaded **Execute** method that takes an array as a parameter. The following sample code shows how to do that:  

    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  

-   The first parameter to the **TypedXmlDocument** constructor in the code is the name of the type you used to build the policy.  

-   The **Policy.Execute** method is basically a wrapper around the **RuleEngine.Execute** method. Therefore, using the **Policy.Execute** method is the easiest way of invoking a policy, as you have seen in this walkthrough.  

-   For more control over the execution of the policy, you may want to use the **RuleEngine.Execute** method instead of using **Policy.Execute**. For example, you can halt the engine temporarily by using the **Halt** function, and then resume it by using the **Execute** function. For more information, see [Halt](../core/halt.md).  

## See Also  
 [How to Execute Policies](../core/how-to-execute-policies.md)