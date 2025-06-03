---
description: "Learn more about: Creating a Price and Availability Request with the Fabrikam Sample"
title: "Creating a Price and Availability Request with the Fabrikam Sample"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Creating a Price and Availability Request with the Fabrikam Sample
In this step, you create a 3A2 Price and Availability request using the LOBWebApplication tool.  
  
### To submit a 3A2 Price and Availability request to Contoso  
  
1.  In Internet Explorer, move to http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx.  
  
2.  On the **LOBWebApplication** page, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Home Organization**|Type **FABRIKAM**.|  
    |**Partner Organization**|Type **CONTOSO**.|  
    |**PIP Code**|Type **3A2**.|  
    |**PIP Version**|Type **R02.00.00A**.|  
    |**Message Category**|Type **Action**.|  
  
3.  Using Notepad or another text editor, open the **3A2_Request.xml** file in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder and copy and paste the text into the **Service Content** field in the LOBWebApplication tool.  
  
4.  Click **Submit** to submit the 3A2 request to Contoso.  
  
### To verify successful communication on the Fabrikam computer  
  
1.  On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.  
  
    > [!NOTE]
    >  You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer. You should then receive a category 50 message that is the response message from the Contoso computer. A category -99 message signifies an error. You can use **Event Viewer** to determine the actual error message.  
  
2.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
3.  In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.  
  
4.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
5.  In the **\<table\> text** dialog box, select **BTARNDATA** from the list.  
  
6.  In the **SQL** window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
7.  Click **Execute** to run the SQL statement.  
  
8.  In the Query window, in the Results pane, verify that you see two incoming messages.  
  
    > [!NOTE]
    >  You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer. You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer. You can also use the ServiceContent field to verify the response.  
  
### To verify successful communication on the Contoso computer  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.  
  
3.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4.  In the **\<table\> text** dialog box, select **BTARNDATA** from the list.  
  
5.  In the **SQL** window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Click **Execute** to run the SQL statement.  
  
7.  In the Query window, in the Results pane, verify that you see two incoming messages.  
  
    > [!NOTE]
    >  You should first receive a category 10 message that represents the original request sent by the Fabrikam computer. You should then receive a category 25 message signifying the receipt acknowledgement message.  
  
8.  In the **SQL** window, type the following SQL statement:  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Click **Execute** to run the SQL statement.  
  
10. In the Query window, in the Results pane, verify that you see one outgoing message.  
  
    > [!NOTE]
    >  You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer. You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.  
  
## See Also  
 [Private Process Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/private-process-tutorial.md)
