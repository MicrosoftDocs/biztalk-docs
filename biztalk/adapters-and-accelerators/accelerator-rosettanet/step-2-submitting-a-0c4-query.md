---
description: "Learn more about: Step 2: Submitting a 0C4 Query"
title: "Step 2: Submitting a 0C4 Query"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 2: Submitting a 0C4 Query
In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 0C4 - Synchronous Test Query. RosettaNet defines this PIP to make sure a successful synchronous communication channel is working correctly between two different organizations. Because this PIP has a synchronous communication pattern, [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] does not send receipt acknowledgements. This PIP follows the same pattern as other synchronous double action PIPs, such as PIP 2A9 - Query Technical Product Information.  
  
### To submit a 0C4 - Synchronous Test Query  
  
1.  On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.  
  
2.  On the **Submit Message** page, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Home Organization**|Type **FABRIKAM**.|  
    |**Partner Organization**|Type **CONTOSO**.|  
    |**Pip Code**|Type **0C4**.|  
    |**Pip Version**|Type **R01.02**.|  
    |**Pip Instance ID**|Type **0C4_Test**. **Important:**  To avoid duplicate message ID errors, you must make sure that the **PIP** is unique for each message that you submit. If you run the 0C4 test in the future, you will have to change this field.|  
    |**Message Category**|Type **Action**.|  
  
3.  Using Notepad or another text editor, open the 0C4_Request.xml file in the *\<drive\>*:\Program Files\Microsoft BizTalk 2009 Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.  
  
4.  Click **Submit** to submit the 0C4 query to the Contoso computer.  
  
### To verify successful communication on the Fabrikam computer  
  
-   On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.  
  
    > [!NOTE]
    >  You should receive a category 50 message that is the response message from the Contoso computer. A category -99 message signifies an error. You can use the Event Viewer to determine the actual error message.  
  
### To verify successful communication on the Contoso computer  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.  
  
    > [!NOTE]
    >  If the SQL Server Agent is not started, right-click it, and then click **Start**.  
  
3.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4.  In the \<table\> text box, select **BTARNDATA** from the list.  
  
5.  In the SQL window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Click **Execute** to run the SQL statement.  
  
7.  In the Query window, in the Results pane, verify that you see one incoming message.  
  
    > [!NOTE]
    >  You should see a category 10 message that represents the original request that the Fabrikam computer sent.  
  
8.  In the SQL window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Click **Execute** to run the SQL statement.  
  
10. In the Query window, in the Results pane, verify that you see one outgoing message.  
  
    > [!NOTE]
    >  You should see a category 50 message that represents the Contoso response to the PIP 0C4 query that Fabrikam sent. In a double action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial query message. The response message serves as the acknowledgement.  
  
## See Also  
 [Step 3: Submitting a 3A2 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md)   
 [Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)
