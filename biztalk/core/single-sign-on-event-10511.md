---
description: "Learn more about: Single Sign-On: Event 10511"
title: "Single Sign-On: Event 10511"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10511
## Details  

| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                     Enterprise Single Sign-On                                                     |
| Product Version |                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                     |
|    Event ID     |                                                               10511                                                               |
|  Event Source   |                                                              ENTSSO                                                               |
|    Component    |                                                                N\A                                                                |
|  Symbolic Name  |                                                         SSO_ERROR_NO_DSN                                                          |
|  Message Text   | The SQL Server and SSO database names were not found in the registry. Use the SSO administration tools to configure these values. |

## Explanation  
 This Error event indicates that the SQL Server and SSO database names were not found in the registry. The SSO service requires this information so it can connect to the SSO database. This information is set in the registry during configuration. This may indicate that configuration did not complete correctly or that the registry entries have been deleted after configuration was completed.  

## User Action  
 To resolve this error, do one or more of the following:  

- If you suspect a wider configuration failure, unconfigure the product and then reconfigure using the configuration program.  

- Alternatively these specific missing registry entries can be set using the SSO command line tool, ssoconfig.exe located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On. Your SSO installation directory may be different. Use the **-setDB** option to set the required SQL Server and SSO database names.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)
