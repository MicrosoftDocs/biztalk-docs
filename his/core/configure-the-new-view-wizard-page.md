---
title: "Configure the New View Wizard Page2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bfb1f6-6b3c-4683-8549-36b5f2208f83
caps.latest.revision: 3
robots: noindex,nofollow
---
# Configure the New View Wizard Page
Use the **Configure the New View** wizard page to select the methods that are included in the object view. Type the name of the view. To specify the methods to be included in the view, select the check box by the method name. Double-click the method name to edit it.  
  
|Use this|To do this|  
|--------------|----------------|  
|**View**|Type the name of the object view. The name can be a maximum of 259 alpha-numeric characters. The name cannot be the same as that of an existing view.|  
|**Object methods**|View all the methods that are defined in the object. Each row contains a summary of the resolution information for a single method. Rows in the list cannot be deleted. The columns are:<br /><br /> <ul><li>**Include** Select this option to include the method in the object view.</li><li>**Method** View the name of the method. Double-click the method name displays the **Method Resolution Criteria** dialog.</li><li>**Endpoints** View one of the endpoints defined in the local environment associated with the view. To change the content of this field, double-click the **Endpoints** field for a specific method.</li><li>**Resolution Type** View one of the possible resolution types:<br /><br /> <ul><li>**Endpoint**</li><li>**Transaction Request Message (TRM)**</li><li>**Enhanced Listener Message (ELM)**</li><li>**Data**</li><li>**Link to Program**</li></ul></li></ul><br /> To change the content of this field, double-click the **Resolution Type** field for a specific method.<br /><br /> -   **Resolution Data** Identifies the data used to select the method to be executed. To change the content of this field, double-click the **Resolution Data** field for a specific method.<br />-   **Resolution Position** View the resolution position. If **Data Resolution** is selected, this information is used by the TI runtime to identify the starting point in the data stream in which to look for the data defined in the resolution data field to determine what method is to be executed. To change the content of this field, double-click the **Resolution Position** field for a specific method.|  
  
## See Also  
 [Method Resolution Criteria Dialog Box (in the New Application Deployment Wizard)](../core/method-resolution-criteria-dialog-box-in-the-new-application-deployment-wizard.md)   
 [New Application Deployment Wizard](../core/new-application-deployment-wizard.md)