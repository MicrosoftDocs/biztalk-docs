---
description: "Learn more about: Step 1: Submitting a 0C2 Request"
title: "Step 1: Submitting a 0C2 Request"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 1: Submitting a 0C2 Request
In this step, you prepare and submit a request using the Partner Interface Process (PIP) for an 0C2 - Asynchronous Test Request. This PIP ensures that an asynchronous communication channel is working correctly between two different organizations. This PIP follows the same pattern as other asynchronous double action PIPs, such as the 3A4 - Request Purchase Order PIP.  
  
### To submit a 0C2 - Asynchronous Test Request  
  
1.  On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.  
  
2.  On the **Submit Message** page, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Home Organization**|Type **FABRIKAM**.|  
    |**Partner Organization**|Type **CONTOSO**.|  
    |**Pip Code**|Type **0C2**.|  
    |**Pip Version**|Type **R01.02**.|  
    |**Pip Instance ID**|Type **0C2_Test**. **Important:**  You must make sure that the **PIP** is unique for each message that you submit to avoid duplicate message ID errors. If you run the 0C2 test in the future, you will have to change this field.|  
    |**Message Category**|Type **Action**.|  
  
3.  Using Notepad or another text editor, open the 0C2_Request.xml file in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.  
  
    > [!NOTE]
    >  To delete the existing text in the Service Content field of the Submit Message form, place the cursor at the beginning of the text, press and hold the **Shift** and **Ctrl** buttons, click **End**, and then click **Delete**.  
  
4.  Click **Submit** to submit the 0C2 request to the Contoso computer.  
  
### To verify successful communication on the Fabrikam computer  
  
-   On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.  
  
    > [!NOTE]
    >  You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer. You should then receive a category 50 message that is the response message from the Contoso computer. A category -99 message signifies an error. You can use **Event Viewer** to determine the actual error message.  
  
### To verify successful communication on the Contoso computer  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.  
  
    > [!NOTE]
    >  If the SQL Server Agent is not started, right-click it, and then click **Start**.  
  
3.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4.  In the \<table\> text dialog box, select **BTARNDATA** from the list, and then click **OK**.  
  
5.  In the SQL window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  On the **Query** menu, click **Execute** to run the SQL statement.  
  
7.  In the Query window, in the Results pane, verify that you see two incoming messages.  
  
    > [!NOTE]
    >  You should first receive a category 10 message that represents the original request sent by the Fabrikam computer. You should then receive a category 25 message signifying the receipt acknowledgement message.  
  
8.  In the SQL window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Click **Execute** to run the SQL statement.  
  
10. In the Query window, in the Results pane, verify that you see one outgoing message.  
  
    > [!NOTE]
    >  You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer. You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.  
  
## See Also  
 [Step 2: Submitting a 0C4 Query](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md)   
 [Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)
