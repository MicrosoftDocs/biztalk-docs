---
description: "Learn more about: Working with Large Schemas"
title: "Working with Large Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Working with Large Schemas
When your schemas become very large, you may find that refreshing the XSD view is increasingly slow and that the response of other aspects of the user interface can be impacted as well. The solution to this issue is to turn off the auto-refresh feature and instead use the manual **Refresh** link in the XSD view to periodically refresh the XSD view. For step-by-step instructions about how turn the auto-refresh feature on an off, see the procedure "To turn automatic refresh of the XSD view on and off" in [Managing the XSD View](../core/how-to-manage-the-xsd-view.md).  
  
 Performance may also be slow in large schemas with multiple roots attached to the **schema** node. Setting the **Root Reference** property may increase performance in the user interface. Setting **Root Reference** improves performance because the compiler creates C# classes for all root schemas. A single root means the creation of fewer classes.  
  
 **Validate Instance** may appear slow in the user interface because a validation is always done on the schema before validating the instance. Schema validation occurs only in the user interface. Setting the **Root Reference** property also improves user interface performance in this case.  
  
## See Also  
 [Using BizTalk Editor](../core/using-biztalk-editor.md)
