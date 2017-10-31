---
title: "Sign-On Errors2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 515348ed-9ce3-4708-abf9-648d21327358
caps.latest.revision: 5
---
# Sign-On Errors
The following table lists sign-on error constants, values, SqlState, SqlCode and a description of the error.  
  
||||  
|-|-|-|  
|**SqlState**|**SqlCode**|**Description**|  
|HY000|-702|**Message** : Enterprise single sign-on is not supported on this configuration.<br /><br /> **Reason** : The client does not support the Enterprise Single Sign-On feature.<br /><br /> **Action** : Contact your client administrator. Use an alternative method of authentication. For more information, see topic on Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|HY000|-703|**Message** : Enterprise single sign-on could not load: 0x80040154.<br /><br /> **Reason** : The client could not contact the Enterprise Single Sign-On Lookup Service to obtain the foreign credentials.<br /><br /> **Action** : Verify connection information to ensure the ESSO Affiliate Application name matches the value for the server and current user defined by the Enterprise Single Sign-On administrator. For more information, see topic on Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|HY000|-1000|**Message** : The user does not have the authority to access the host resource. Check your authentication credentials or contact your system administrator.<br /><br /> **Reason** : The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action** : Verify connection information to ensure the User Name (User Identifier), Password and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|HY000|-1001|**Message** : The user does not have the authority to access the host resource. The password has expired.<br /><br /> **Reason** : The server cannot authenticate the user with the credentials presented at connection. The client Password Expiration Management (PEM) feature will return this message, when the password has expired.<br /><br /> **Action** : Verify connection information to ensure the User Name (User Identifier) and Password for interactive sign-on security match the server requirements defined for the current user. Specify a new password using the client Change Password Management (PCM) feature using the Data Access Tool or Data Access Library. For more information, see topics on User Name, Password and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|HY000|-1002|**Message** : The new authentication credentials are invalid. Check your authentication credentials or contact your system administrator.<br /><br /> **Reason** : The server cannot change the password with the credentials presented when the client executes the Password Change Management (PCM) feature.<br /><br /> **Action** : Verify the User Name (User Identifier), existing expired Password, New Password, and Confirm New Password properties, when using the Password Change Management (PCM) feature of the Data Access Tool or Data Access Library. Check the Password length and other restrictions for the DB2 database platform and version. For more information, see topics on Password a, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|HY000||**Message** : Password change management is not supported.<br /><br /> **Reason** : The server does not support the client Password Change Management (PCM) feature.<br /><br /> **Action** : Contact your system administrator.|  
|HY000|-1004|**Message** : Authentication method USRIDNWPWD is not supported.<br /><br /> **Reason** : The server does not support the client Password Change Management (PCM) feature.<br /><br /> **Action** : Contact your system administrator.|