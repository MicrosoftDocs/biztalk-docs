---
description: "Learn more about: Restrictions on the SMTP Host Property"
title: "Restrictions on the SMTP Host Property"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Restrictions on the SMTP Host Property
The SMTP host property is a string that specifies the SMTP server that the SMTP adapter will use to send messages from the BizTalk server.  
  
 The following rules and restrictions apply to this property:  
  
- This property must be configured on the adapter handler level, on the endpoint level, or in both places.  
  
- The SMTP server property cannot contain the following characters: ` ~ ! @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;  
  
- The length of the SMTP server name must not exceed 256 characters.  
  
  The SMTP adapter always validates the SMTP host name at design time by using the previously mentioned rules. In addition, the SMTP adapter validates the SMTP host name at run time if a message is sent through a dynamic port with the SMTP adapter.  
  
## See Also  
 [Restrictions When Configuring the SMTP Adapter](../core/restrictions-when-configuring-the-smtp-adapter.md)
