---
title: "How to Configure the Receive Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filter expressions, Receive shape [Orchestration Designer]"
  - "Receive shape [Orchestration Designer], about Receive shape"
  - "configuring [Orchestration Designer], Receive shapes"
  - "Receive shape [Orchestration Designer]"
  - "Receive shape [Orchestration Designer], filter expressions"
ms.assetid: 15aadee4-fa05-4edd-a191-e4d191c1ea22
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Receive Shape
![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")  
Receive shape  

 A **Receive** shape can be used to start an orchestration. If you set the **Activate** property to **True**, the runtime engine will test an incoming message to see whether it is of the right type and, if a filter has been applied, whether the filter expression is satisfied. If the criteria for receipt of the message are met, the runtime engine creates and runs a new orchestration instance, and the **Receive** shape receives the message.  

> [!NOTE]
>  If the **Activate** property of a Receive shape is set to True, the **Receive** must be the first action in the orchestration.  

> [!NOTE]
>  If the **Activate** property is set to False on all **Receive** shapes, your orchestration must be called by another orchestration in order to run.  

> [!NOTE]
>  If you put a **Receive** shape inside a scope with the **Activate** property set to **True**, and then add a .NET Class variable to your orchestration without changing the variable's **Use Default Constructor** property to **False**, the activate receive statement will be outside of the scope in the generated XLANG/S code, but the design surface will continue to show it as being inside the scope.  

 Each orchestration must have at least one **Receive** shape with the **Activate** property set to **True**.  

 If you expect to receive an indirect or asynchronous response (not on a request-response port) to a message that you have previously sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance. You can apply an initializing correlation set to the Receive shape if you plan to do subsequent correlation on values in the incoming message, or a following correlation set for correlating using a previously initialized correlation set. For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).  

### To configure a Receive shape  

1.  Set a message and a port operation.  

    1.  In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the message type being received.  

         In the Properties window, select the message to receive from the **Message** property drop-down list.  

    2.  In the Properties window, select the port operation to receive the message from the **Operation** drop-down list.  

         —Or—  

         Drag the receive connector from the **Receive** shape to the port socket that will receive the message.  

2.  Specify that the **Receive** shape will activate the orchestration.  

3.  In the Properties window, set the Activate property to True.  

    1.  In the Properties window, click the **Ellipsis** (**...**) button for the Filter Expression property to create a filter to restrict the messages that this **Receive** shape accepts.  

         —Or—  

         Right-click the **Receive** shape and then click **Edit Filter Expression**.  

    2.  The **Filter Expression** dialog box appears. Use this dialog box to create one or more filter expressions.  

        > [!NOTE]
        >  A message type must be defined and assigned to the **Receive** shape before you can apply a filter to it.  

4.  Specify correlation sets to restrict the messages the **Receive** shape accepts.  

    -   For each correlation set you want to follow, check a correlation set from the drop-down on the **Following Correlation Sets** property.  

    -   For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.  

## Filter Expression grid control  
 You build a filter expression by using this grid control to define the predicates that make up the expression. You can add, edit, and delete predicates from the cells of the grid. This grid control has four columns: Property, Operator, Value, and Grouping.  

- **Property.** You can type a property reference, or select one from the cell's drop-down list. The list contains properties on the incoming message.  

- **Operator.** You can type in this cell, or select an operator from the drop-down list. Possible selections are:  


  | Operand |           Meaning           |
  |---------|-----------------------------|
  |   ==    |         Is equal to         |
  |   !=    |       Is not equal to       |
  |    <    |        Is less than         |
  |   \<=   |  Is less than or equal to   |
  |    >    |       Is greater than       |
  |   \>=   | Is greater than or equal to |
  | Exists  |           Exists            |


- **Value.** Cells in the **Value** column can hold any constant that you type in: a string-literal, an integer-literal, or null.  

  > [!NOTE]
  >  If the property selected is of type string, the value needs to be in quotes. For example, SMTP.From = "MyServer".  

- **Grouping.** Use this column to control predicate grouping. Filter expressions are always expressed in Disjunctive Normal Form (DNF) so grouping can be determined automatically. AND means the predicate is to be grouped with the predicate following it, while OR means the predicate is separate from the predicate in the next row. Gray brackets to the left of the grid control appear when predicates are grouped together. Predicate groups cannot be nested. If you do not specify a value in this cell, the value of the cell defaults to AND.  

  For example, you might create an expression like the following:  

  `MSMQ.MsgID = 1`  

  With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.  

  You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:  

  `MSMQ.MsgID = 1 OR`  

  `SMTP.From = "MyServer"`  

  In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.  

## Hint label  
 This field provides user guidance. The label text changes depending on which column contains the active cell. The text displays the column name followed by guidance text as follows:  

-   **Property.** Please select a property on the incoming message from the list.  

-   **Operator.** Select an operator to compare the Property with the Value.  

-   **Value.** Select a message property from the list, or type in a literal value.  

-   **Grouping.** Specify how this row is to be grouped with the next row. 'AND' will join the rows, and 'OR' will separate them.  

## Move Up button  
 Click this to move a selected row up. (First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)  

## Move Down button  
 Click this to move a selected row down. (First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)  

## Filter Expression Created field  
 This read-only text box shows the expression as you are building it.  

## In This Section  
 [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md)