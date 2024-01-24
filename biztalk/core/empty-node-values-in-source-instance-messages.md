---
description: "Learn more about: Empty Node Values in Source Instance Messages"
title: "Empty Node Values in Source Instance Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Empty Node Values in Source Instance Messages
There may be times when you do not want content in all of the schema nodes when you test a map.  

## Ceate empty node values  

1. Generate instance data using BizTalk Editor. For more information about generating instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).  

2. Open the input instance message in a text editor, delete the data from elements and attributes that you want to be empty, and then save the modified instance file.  

3. Configure BizTalk Mapper to use the file you just modified when the schema is validated and tested. You set the file in the Properties window for the schema. For more information about setting properties, see **Map File Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## See Also  
- [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md)   
- **Schema Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
