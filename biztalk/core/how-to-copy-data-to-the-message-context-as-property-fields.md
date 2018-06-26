---
title: "How to Copy Data to the Message Context as Property Fields | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4fdfe475-d9b4-4cf9-898f-dbd7e719c27c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy Data to the Message Context as Property Fields
You can promote a property as a **Property Field** in much the same way as promoting a property as a **Distinguished Field**, and you can also use the **Quick Promotion** feature to streamline the process.  
  
 You might choose **Property Field** promotion over **Distinguished Field** promotion for the following reasons:  
  
- The values you want to promote are shorter than the 255 character limitation that applies to **Property Fields**.  
  
- You need the values that you promote to be accessible outside of orchestrations, such as within pipelines or ports.  
  
  This topic provides step-by-step instructions for promoting a property as a **Property Field** in both of these ways.  
  
### To promote a property as a Property Field using the Promote Properties dialog box  
  
1.  If necessary, create an appropriate property schema into which you will promote a property. For step-by-step instructions for creating property schemas, see [Creating Property Schemas](../core/how-to-create-property-schemas.md).  
  
    > [!NOTE]
    >  This step might not be necessary if you have already created a property schema and inserted the appropriate **Field Element** nodes as child nodes of the **Schema** node.  
  
2.  In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.  
  
    > [!NOTE]
    >  You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.  
  
3.  Right-click the selected node, click **Promote**, and then click **Show Promotions**.  
  
     The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.  
  
4.  In the **Promote Properties** dialog box, select the **Property Fields** tab.  
  
5.  Confirm that the property schema into which you want to promote a property is present in the **Property Schemas List** in the Property Fields tab. If it is present, skip to step 8.  
  
6.  In the **Property Schemas List** section, click the **Folder** icon. The **BizTalk Type Picker** dialog box appears.  
  
7.  In the **BizTalk Type Picker** dialog box, navigate to the appropriate property schema (that you may have created in step 1), select that schema, and then click **OK**.  
  
    > [!NOTE]
    >  Optionally, you can change the namespace prefix associated with the property schema by changing the string in the appropriate **Prefix** column field.  
  
8.  With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.  
  
     If allowed, the selected node is added to the end of the **Property Fields List** on the **Property Fields** tab. If not allowed, a message box provides an explanation. If not allowed, the **Add** button is not enabled.  
  
9. Double-click **Property** column cell for the row you just added to the **Property Fields List**, and then in the drop-down list, select the **Property Schema** and corresponding **Field Element** node into which you want to promote the selected node. Drop-down list values have the form X:Y, where X is the namespace prefix of a property schema in the **Property Schemas List**, and Y is the node name of a **Field Element** node in that property schema.  
  
     The default value in the drop-down list is the first property schema **(Field Element)** node that has not yet been promoted, sorted alphabetically across all relevant property schemas. This will rarely be the property schema node into which you intend to promote a given schema node.  
  
10. You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** and then performing step 9 after each selection.  
  
11. When complete, click **OK**.  
  
     The nodes that you selected to promote are now **Property Fields** and are associated with a particular **Field Element** node in a property schema.  
  
### To promote a property as a Property Field using the Quick Promotion command  
  
1.  In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.  
  
    > [!NOTE]
    >  You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.  
  
2.  Right-click the selected node, click **Promote**, and then click **Quick Promotion**.  
  
     If the default property schema, as defined by the **Default Property Schema Name** property on the **Property Pages** for the relevant schema, does not exist, you must click **OK** in the confirmation dialog to create the default property schema and configure it with an appropriate **Field Element** node to accommodate your property promotion.  
  
> [!NOTE]
>  You can view and manage properties promoted using the **Quick Promotions** feature by opening the **Promote Properties** dialog box and then clicking the **Property Fields** tab. For step-by-step instructions for opening the **Promote Properties** dialog box, see [Opening the Promote Properties Dialog Box](../core/how-to-open-the-promote-properties-dialog-box.md).  
  
## See Also  
 [Promoting Properties](../core/promoting-properties.md)   
 [How to Create Property Schemas](../core/how-to-create-property-schemas.md)   
 [Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md)