---
description: "Learn more about: Setting Filter Expressions on Send Ports"
title: "Setting Filter Expressions on Send Ports"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Setting Filter Expressions on Send Ports
You set context properties in filter expressions on the send port to control what the port sends. You can set the filter expressions with a number of operators that offer you flexibility in how you filter the property (equality or inequality, exists, greater than, great than or equal to, less than, and less than or equal to).  
  
### To set the filter expression on a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** (or another application). Click **Send Ports**.  
  
2.  Right-click the send port that you want to set the filter expression for, and then click **Properties**.  
  
3.  In the console tree of the Send Port Properties dialog box, click **Filters**.  
  
4.  Click the text box in the **Property** column, and then select the context property from the **Property** drop-down list.  
  
5.  Click the **Operator** box in the row for the property, and select the operator for the property from the drop-down list.  
  
6.  Click the **Value** box in the row for the property, and type a value expression.  
  
7.  If you need to add another  clause for the filter expression, click the **Group By** box in the row for the property, and select **And** or **Or** to determine the relationship of the clauses.  
  
8.  Repeat steps 4 through 6 to add another filter clause.  
  
9. Verify that the filter expression is correct in the pane at the bottom of the **Filters** pane.  
  
10. When you have added all filter clauses, click **OK**.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using Context Properties](../../adapters-and-accelerators/accelerator-hl7/using-context-properties.md)
