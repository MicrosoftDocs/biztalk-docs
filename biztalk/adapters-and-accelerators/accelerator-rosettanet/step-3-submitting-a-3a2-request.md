---
description: "Learn more about: Step 3: Submitting a 3A2 Request"
title: "Step 3: Submitting a 3A2 Request"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 3: Submitting a 3A2 Request
In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 3A2 - Request Price and Availability. This PIP enables a buyer organization to obtain information about a certain product, such as price and number of available units. The buyer can then process that information through business rules to determine whether to purchase the product from the supplier.  
  
### To submit a 3A2 - Request Price and Availability  
  
1.  On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.  
  
2.  On the **Submit Message** page, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Home Organization**|Type **FABRIKAM**.|  
    |**Partner Organization**|Type **Contoso**.|  
    |**Pip Code**|Type **3A2**. **Important:**  To avoid duplicate message ID errors, you must make sure that the **Pip** is unique for each message that you submit. If you run the 3A2 test in the future, you have to change this field.|  
    |**Pip Version**|Type **R02.00.00A**.|  
    |**Pip Instance ID**|Type **3A2_Test**.|  
    |**Message Category**|Type **Action**.|  
  
3.  Using Notepad or another text editor, open the file 3A2_Request.xml in the *\<drive\>*:\ Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.  
  
4.  Click **Submit** to submit the 3A2 request to the Contoso computer.  
  
### To verify successful communication on the Fabrikam computer  
  
-   On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.  
  
    > [!NOTE]
    >  You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer. You should then receive a category 50 message that is the response message from the Contoso computer. A category -99 message signifies an error. You can use **Event Viewer** to determine the actual error message.  
  
### To verify successful communication on the Contoso computer  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.  
  
3.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4.  In the \<table\> text box, select **BTARNDATA** from the list.  
  
5.  In the SQL window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Click **Execute** to run the SQL statement.  
  
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
 [Step 4: Submitting a 3A4 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md)   
 [Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)
