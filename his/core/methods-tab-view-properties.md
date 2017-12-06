---
title: "Methods Tab (View Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15337"
ms.assetid: 51c1c4ef-1276-4665-86b6-932e1d11df73
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Methods Tab (View Properties)
Use the **Methods** tab to view or change the methods associated with the object view and the method resolution details. You can use this page to add and remove methods on the object view. Double-click a row in the grid to edit the resolution information.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Object methods**|View all the methods that are defined in the object. Each row contains a summary of the resolution information for a single method. Rows in the list cannot be deleted. The columns are:<br /><br /> <ul><li>**Include** Select to include the method in the object view.</li><li>**Method** View the name of the method. Double-click the method name to launch the **Method Resolution Criteria** dialog box.</li><li>**Endpoint** View one of the endpoints defined in the local environment associated with the view. To change the content of this field, double-click the **Endpoints** field for a specific method.</li><li>**Resolution Type** Displays one of the possible resolution types:<br /><br /> <ul><li>**Endpoint** The endpoint resolution type is the simplest means of resolving a request to a method. A data stream directed to a port always executes a single method on a view. This model is considered "raw sockets," and represents a single synchronous exchange of data.</li><li>**Transaction Request Message (TRM)** The TRM resolution type is specific to the IBM CICS Concurrent Server model and the Microsoft variant, MSLink model. It represents a double exchange sequence.</li><li>**Enhanced Listener Message (ELM)**:</li><li>**Data** Similar to **Endpoint** in that it adds the ability to identify a string in the data stream directed to a port that is used to associate the request with a specific method in the view. This model is considered "raw sockets." It represents a single synchronous exchange of data.</li><li>**Link to Program Name:** Select **Link to Program Name** to resolve all the methods of a new object view using the data information specified when the object view was created.</li></ul><br />     To change the content of this field, double-click the **Resolution Type** field for a specific method.</li><li>**Resolution Data** Identifies the data used to select the method to be executed. To change the content of this field, double-click the **Resolution Data** field for a specific method.</li><li>**Resolution Position** Displays the resolution position. If **Data Resolution** is selected, this information is used by the TI runtime to identify the starting point in the data stream in which to look for the data defined in the resolution data field to determine which method is to be executed. To change the content of this field, double-click the **Resolution Position** field for a specific method.</li></ul>|  
  
> [!NOTE]
>  When viewed from the ***view*** node under the application ***listener*** node, the method properties are read-only. If you want to change a method property, right-click the specific ***view* Node** under the **object Node**, and then left-click **Properties** on the shortcut menu. The properties on that page are read-write.  
  
> [!CAUTION]
>  The properties on an object view are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the object view to function incorrectly.  
  
## See Also  
 [View Node (listener)](../core/view-node-listener.md)   
 [View Node (object)](../core/view-node-object.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)