---
title: "Action Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Action Errors
This section contains detailed information for diagnosing and resolving WCF Action errors.  
  
## Details  
  
|                 |                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                  |
| Product Version |                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                              |
|    Event ID     |                                                                          0                                                                          |
|  Event Source   |                                                                          0                                                                          |
|    Component    |                                                                          0                                                                          |
|  Symbolic Name  |                                                                          0                                                                          |
|  Message Text   | A single action cannot contain new line characters. Remove all new line characters. Or, to specify multiple actions, use the action mapping syntax. |
  
## Explanation  
 This error indicates the action property of a send port contains a new line character, which is not allowed.  
  
> [!NOTE]
>  This restriction does not apply when the action is defined as a mapping.  
  
## User Action  
 Use the following procedure to fix the action property.  
  
 
1. Open **BizTalk Server Administration**.  
  
2. In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application, and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Select **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Select **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, select the **General** tab.  
  
9. In the **SOAP Action header** section, remove the new line character from the **Action** text box.  

## More good info  
 For additional information on actions, see [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)