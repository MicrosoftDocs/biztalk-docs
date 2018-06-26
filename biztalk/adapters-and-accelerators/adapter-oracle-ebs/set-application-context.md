---
title: "Set application context | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9697155-70c0-4173-80d2-d02d103c397b
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Set application context
In [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], setting application context is mandatory for some Oracle E-Business Suite artifacts (interface tables, interface views, concurrent programs, and request sets) before you can perform operations on them. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not allow you to perform operations on these artifacts until you have set the application context. However, for artifacts in the underlying Oracle database, it is up to the user whether they want to set the application context or not.  
  
## What is application context  
 Application context is a set of elements associated with an artifact in Oracle E-Business Suite that implements user preferences and access control on the artifact. Application context consists of the following elements:  
  
- **User name**: A user that can connect to Oracle E-Business Suite.  
  
- **Responsibility**: A responsibility is an access level in Oracle E-Business Suite that allows users to access only those data and functions that are appropriate to their roles in an organization. Responsibilities can allow access to a specific application, operating units, set of books, and a restricted list of windows, functions, and other responsibilities. By virtue of assigning responsibilities to a user, you can grant/restrict access of the user in Oracle E-Business Suite.  
  
- **Organization ID**: Oracle E-Business Suite supports setting up of multiple organizations. These different organizations are uniquely identified by a value, Organization ID, in the Org_ID column of the table in Oracle E-Business Suite that stores information about these organizations. By virtue of assigning a responsibility to an organization or selecting an organization explicitly, you can grant/restrict access of a user to an organization.  
  
  For more information about responsibility, multiple organizations, and Organization ID in Oracle E-Business Suite, search the [Oracle help center](http://docs.oracle.com).  
  
## Setting application context  
 As the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] connects to the underlying database in the Oracle E-Business Suite, application context for the Oracle E-Business Suite artifacts are not established or initialized in the adapter. You can initialize or set the application context for these artifacts in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by using either of the following:  
  
- **Binding properties**: The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the following binding properties for setting the application context: **OracleEBSOrganizationId**, **OracleUserName**, **OraclePassword**, **OracleEBSResponsibilityKey**, **OracleEBSResponsibilityName**, and **ApplicationShortName**. You do not need to specify values for all these binding properties to set application context for various artifacts. For information about the binding properties required for setting application context for an artifact, see [Binding Properties for Setting Application Context For Various Artifacts](#Binding) later in this topic.  
  
- **Message context properties**: The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the following message context properties for setting the application context: **ApplicationShortName**, **OrganizationID**, **ResponsibilityKey**, and **ResponsibilityName**. For specifying the user name and password, you must use the binding properties. For information about how to set application context using message context properties, see [Configure the Application Context Using Message Context Properties](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
> [!IMPORTANT]
>  The value specified for the **OracleEBSResponsibilityKey** binding property overrides the value of the **OracleEBSResponsibilityName** binding property. Similarly, the value specified for the **ResponsibilityKey** message context property overrides the value specified for the **ResponsibilityName** message context property.  
  
### Precedence order (binding properties vs. message context properties)  
 If you set the application context using both the binding properties and message context properties, the values specified for message context properties takes precedence and overrides the values specified for the binding properties. But, for example, if you specify the application short name as a message context property and the others as binding properties, only the value for the application short name is taken from the message context property and the rest are picked from the relevant binding properties.  
  
 **Precedence Order for Application Short Name**  
  
 While setting the application context, the application short name is used in the following precedence order (highest to lowest):  
  
- The application short name specified in the **ApplicationShortName** message context property.  
  
- The application short name specified in the SOAP action (for interface tables, interface views, concurrent programs, and request sets only).  
  
- The application short name specified in the **ApplicationShortName** binding property.  
  
  However, for interface tables, interface views, concurrent programs, and request sets, this precedence order is only applicable while setting the application context. To identify the interface tables, interface views, concurrent programs, and request sets, the application short name in the SOAP action is used.  
  
  **Precedence Order for Responsibility Key and Responsibility Name**  
  
  While setting the application context, the responsibility key and responsibility name are used in the following precedence order (highest to lowest):  
  
- The responsibility key specified in the **ResponsibilityKey** message context property.  
  
- The responsibility name specified in the **ResponsibilityName** message context property.  
  
- The responsibility key specified in the **OracleEBSResponsibilityKey** binding property.  
  
- The responsibility name specified in the **OracleEBSResponsibilityName** binding property.  
  
> [!TIP]
>  **Why use message context properties over binding properties to set the application context?** If you set the application context using binding properties, the WCF-Custom send port for the Oracle E-Business adapter can be used only for the specific organization ID, responsibility, and application that you specified for the binding properties. On the contrary, if you use the message context property you can configure a “generic” WCF-Custom send port and set the application context at the message level.  
  
### Setting Application Context For Interface Tables, Interface Views, Concurrent Programs, and Request Sets (Mandatory)  
 You must set the application context before performing operations on interface tables, interface views, concurrent programs, and request sets in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. To do this, you have to provide appropriate values for the binding properties or the message context properties as specified earlier.  
  
> [!IMPORTANT]
>  You cannot perform operations on interface tables, interface views, concurrent programs, and request sets unless you have set appropriate values for the required binding properties or the message context properties.  
  
### Setting Application Context For PL/SQL APIs, Procedures, Functions, Tables, and Views  
  
- **PL/SQL APIs**: The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes PL/SQL APIs associated with the Oracle database as well as the Oracle E-Business Suite application. While it is optional to set the application context for the PL/SQL APIs associated with the Oracle database, it is mandatory to set the application context for the PL/SQL APIs associated with the Oracle E-Business Suite application.  
  
- **Procedures and Functions**: It is not mandatory to set the application context to perform operations on procedures and functions in the Oracle database.  
  
- **Tables and Views**: It is not mandatory to set the application context to perform operations on tables and views in the Oracle database. However, for custom Oracle E-Business Suite application, users may or may not register the base database tables as interface tables. If a database table is not registered as an interface table, it will be displayed along with the database tables in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Because these tables are associated with an Oracle E-Business application, for any operation on these tables you must set the application context.  
  
  To set the application context for these artifacts, you must provide appropriate values for the binding properties or the message context properties as specified earlier.  
  
### Setting Application Context For Poll, ExecuteNonQuery, ExecuteReader, ExecuteScalar, and Composite Operations  
 Apart from the artifacts, you can also set the application context for various operations that are performed on these artifacts.  
  
-   To set the application context for the Poll operation, you can only use the binding properties as specified earlier. For setting application context, you must provide appropriate values for the binding properties that are applicable for the artifact on which the Poll operation is performed. For example, if the Poll operation is performed on an interface table then you must specify values for the binding properties for the interface table.  
  
-   To set the application context for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations, you must provide appropriate values for the binding properties or the message context properties as specified earlier. For setting application context for these operations, you must provide appropriate values for the binding properties or the message context properties that are applicable for the artifact on which the operations are performed.  
  
-   To set the application context for composite operations, you must provide appropriate values for the binding properties or the message context properties as specified earlier. For setting application context for composite operations, you must provide appropriate values for the binding properties or the message context properties that are applicable for the individual operations. For example, if a composite operation contains two operations: one on the interface table and the other on the database table then you must specify values for the binding properties or the message context properties for the interface table as well as the binding properties or the message context properties for the database table.  
  
    > [!IMPORTANT]
    >  For all these operations, it is mandatory to set the application context if the operation is performed on an artifact in Oracle E-Business Suite (interface table, interface view, concurrent programs or request sets). If the operation is performed on an artifact in the underlying database, it is not mandatory to set the application context. For example, if you are performing the Poll operation on an interface table, it is mandatory to set the application context whereas if the Poll operation is performed on a table, it is not mandatory to set the application context.  
  
## Setting the Language for Performing Operations  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports the Multi-Language Support (MLS) feature of Oracle E-Business Suite, and allows you to specify a language while performing operations. The adapter exposes the **Language** binding property under the **MlsSettings** binding property and the **Language** message context property to specify a language for performing operations.  
  
 The value specified for the **Language** message context property overrides the value of the **Language** binding property under the **MlsSettings** binding property. For more information about the **MlsSettings** binding property, see [Read about  BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
##  <a name="Binding"></a> Binding Properties for Setting Application Context For Various Artifacts  
 The following table provides information about the binding properties for which you must specify appropriate values to set application context for various artifacts:  
  
|Artifacts|OracleEBSOrganizationId|OracleUserName|OraclePassword|OracleEBSResponsibilityKey<br />or<br />OracleEBSResponsibilityName|ApplicationShortName|  
|---|---|---|---|---|---|  
|Interface Tables and Interface Views|√*|√|√|√||  
|Concurrent Programs|√*|√|√|√||  
|Request Sets|√*|√|√|√||  
|PL/SQL APIs|√*|√|√|√|√|  
|Procedures and Functions|√*|√|√|√|√|  
|Tables and Views|√*|√|√|√|√|  
  
 **√\* = Optional**  
  
> [!IMPORTANT]
> - The default value of the **OracleEBSOrganizationId** binding property (optional) is null. If you specify a value for the **OracleEBSOrganizationId** binding property, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sets the ORG_ID of the session to this value while setting the application context.  
>   -   The value specified for the **OracleEBSResponsibilityKey** binding property overrides the value specified for the **OracleEBSResponsibilityName** binding property.  
  
 For detailed information about each of these binding properties, see [Read about  BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)