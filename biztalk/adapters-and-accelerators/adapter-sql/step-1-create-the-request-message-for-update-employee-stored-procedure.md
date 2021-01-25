---
description: "Learn more about: Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure"
title: "Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4dd975d9-4b38-46e0-a926-4b325b0d7b5e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure
![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Time to complete:** 10 minutes  
  
 **Objective:** In this step, you add a C# class library project to your solution. This library creates an in-memory request message for the **UPDATE_EMPLOYEE** stored procedure. In later steps, the orchestration sends this message to SQL Server to execute the stored procedure.  
  
## Prerequisites  
 You must have completed the steps in [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).  
  
### To create a request message for UPDATE_EMPLOYEE stored procedure  
  
1.  Add a Visual C# class library project to your solution. For the name of the project, type `UpdateEmployeeMessageCreator`.  
  
2.  Rename **Class1.cs** to **UpdateEmployeeMessageCreator.cs**.  
  
3.  Copy the following code to the .cs file:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdateEmployeeMessageCreator  
    {  
        public class UpdateEmployeeMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreateEmployeeMessage";  
                try  
                {  
                    ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                    Console.WriteLine("EXCEPTION: " + ex.ToString());  
                    throw ex;  
                }  
  
                //Create Message From XML  
                Message = new XmlDocument();  
  
                Message.PreserveWhitespace = true;  
  
                Message.Load(ResponseDoc);  
  
                return Message;  
            }  
        }  
    }  
  
    ```  
  
     This code snippet expects a request message for the **UPDATE_EMPLOYEE** stored procedure to be present at C:\TestLocation\CreateEmployeeMessage. The code uses the request message to create a similar request message at run time.  
  
4.  Add a strong-name key file to the project. See [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).  
  
    1.  In the Solution Explorer, right-click the **UpdateEmployeeMessageCreator** project, and then click **Properties**.  
  
    2.  In the **Property** window, click **Signing**.  
  
    3.  In the **Signing** tab, select the **Sign the assembly** check box.  
  
    4.  From the **Choose a strong-name key file** list, click **\<Browse\>**.  
  
    5.  Navigate to the folder where you created the strong-name key file, and then click **Open**.  
  
    6.  Click **Save** on the Standard menu bar. Close the **Property** window.  
  
5.  Build the project. Right-click the project, and then click **Build**.  
  
6.  Add a reference of this project to the BizTalk project in the solution.  
  
    1.  In the Solution Explorer, expand the BizTalk project, right-click **References**, and then click **Add Reference**.  
  
    2.  In the **Add Reference** dialog box, click the **Projects** tab.  
  
    3.  From the list of project names, select **UpdateEmployeeMessageCreator**, click **Add**, and then click **OK**.  
  
7.  Building the project creates the assembly DLL under \bin\Debug folder of the project. You must add this DLL to the Global Assembly Cache (GAC).  
  
    1.  Start a Visual Studio Command Prompt.  
  
    2.  From the command prompt, navigate to the \bin\Debug\ folder of the **UpdateEmployeeMessageCreator** project.  
  
    3.  Run the following command on the command prompt:  
  
        ```  
        gacutil /i UpdateEmployeeMessageCreator.dll  
        ```  
  
## What did I just do?  
 In this step, you added an UpdateEmployeeMessageCreator class library project that creates request message at run-time. You added the reference to this project in the BizTalk project and also added the assembly DLL to the GAC.  
  
## Next Steps  
 You send the request message to SQL Server and receive the response, as described in [Step 2: Send the Request Message to SQL Server and Receive Response](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).  
  
## See Also  
 [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)
