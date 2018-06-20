---
title: "Step 17: Create the WSClient Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WSClient application"
  - "message enrichment tutorial, WSClient application"
  - "creating, WSClient application"
ms.assetid: 2849cd4c-30d0-47ab-8161-fab379d5a548
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 17: Create the WSClient Application
WSClient.exe (Web service client) is a console application written in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] that illustrates how to send data to the orchestration that you published as a Web service in the previous steps. The WSClient application accepts four input parameters in order: patient first name, middle name, last name, and social security number, respectively. To send patient information to your Web service, use the following command line syntax:  
  
```  
wsclient john henry smith 123456789  
```  
  
### To create the WSClient application  
  
1. In Solution Explorer, right-click **Solution 'BTAHL7V22Common'**, click **Add**, and then click **New Project**.  
  
2. In the **Add New Project** dialog box, in the **Project Types** pane, click **Visual C#** and in the **Templates** pane, click **Console Application**.  
  
3. In the **Name** field, type **WSClient**. In the **Location** field, browse to **\<*drive*\>:\Tutorial**, and then click **OK**. Solution Explorer adds WSClient to the tree, and the Program.cs file appears.  
  
4. In Solution Explorer, right-click **WSClient**, and then click **Add Web Reference**.  
  
5. In the Add Web Reference dialog box, click **Web services on the local machine**. The local computer searches for available Web services, and then displays them in a list.  
  
6. In the list of Web Services on the Local Machine, click **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, click **Operation_1**, and then click **Add Reference**.  
  
7. Double-click Program.cs.  
  
8. Copy the following code and then paste it into the Program.cs window:  
  
   ```  
   using System;  
  
   namespace WSClient  
   {  
      class Class1  
      {  
         [STAThread]  
         static void Main(string[] args)  
         {  
            try   
            {  
               localhost.DoorbellRoot req=new WSClient.localhost.DoorbellRoot();  
               req.FirstName=args[0];  
               req.MiddleName=args[1];  
               req.LastName=args[2];  
               req.SSN=args[3];  
               localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort sp=new WSClient.localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort();  
               sp.Operation_1(req);  
            }  
            catch (Exception ex)  
            {  
               Console.WriteLine(ex.Message);  
            }  
         }  
      }  
   }  
   ```  
  
9. In Solution Explorer, right-click **WSClient**, and then click **Build**. Ensure that a success message appears in the output window. If no success message appears, troubleshoot **WSClient**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] places a copy of the executable, WSClient.exe, into the \<*drive*\>:\Tutorial\WSClient\bin\Debug folder.  
  
   Proceed to [Step 18: Test Your New Message Enrichment Solution](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)