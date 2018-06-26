---
title: "Invoke Functions and Procedures in Oracle Database using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, invoke functions and procedures using the WCF service model"
  - "WCF service model, invoking functions and procedures"
ms.assetid: 806fc803-3640-42d6-bdf9-53b08f9c7c50
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke Functions and Procedures in Oracle Database using the WCF Service Model
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces procedures, functions, and packages as operations. In the WCF service model these operations are represented as methods on a WCF client. The WCF service model and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   **Support functions**. The RETURN value of the Oracle function is surfaced as the return value of the WCF client method. Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.  
  
-   **Support procedures**. The first OUT parameter of the Oracle procedure is surfaced as the return value of the WCF client method. All other Oracle parameters are surfaced as parameters (with the appropriate direction as defined below) to the WCF client method.  
  
-   **Support Oracle packages**. The name of the operation and the namespace of its parameter types are qualified by the package name.  
  
-   **Support overloaded functions and procedures**.  
  
-   **Support IN, OUT and IN OUT parameters for basic Oracle data types for both procedures and functions**. OUT parameters are surfaced as **out** parameters on the WCF client method and IN OUT parameters are surfaced as **ref** parameters.  
  
-   **Support IN, OUT, and IN OUT REF CURSOR parameters for procedures and functions, as well as function RETURN values**. For more information, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).  
  
-   **Support IN, OUT, and IN OUT RECORD type parameters for procedures and functions, as well as function RETURN values**. For more information, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).  
  
## About the Examples Used in this Topic  
 The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT overloaded procedure. This procedure reads a record from the SCOTT/ACCOUNT table based on either an account ID or an account name. A script to generate this procedure and table is supplied with the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
## The WCF Client Class  
 The following table shows the name of the WCF client and the method generated for procedures, functions and packages that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces. Unless a function or procedure is overloaded, a single WCF client is used to invoke all of the functions in a schema, all of the procedures in a schema, or all of the functions and procedures in a package.  
  
|Oracle Artifact|WCF Client Operation Name|Example|  
|---------------------|-------------------------------|-------------|  
|Procedure|[SCHEMA]ProcedureClient.[PROC_NAME]|SCOTTProcedureClient.MYPROC|  
|Function|[SCHEMA]FunctionClient.[FUNC_NAME]|SCOTTProcedureClient.MYFUNC|  
|Package (procedure or function)|[SCHEMA]Package[PACKAGE_NAME]Client.[PROC_NAME or FUNC_NAME]|SCOTTPackageMYPACKAGEClient.MYPROC|  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [PROC_NAME] = The name of an Oracle procedure; for example, MYPROC.  
  
 [FUNC_NAME] = The name of an Oracle function; for example, MYFUNC.  
  
 [PACKAGE_NAME] = The name of an Oracle package.  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents Oracle RECORD type parameters and return values as well as the result sets returned by REF CURSOR parameters as complex XML types that contain the row data (or fields) of an Oracle record. In the WCF service model, each of these XML types is represented as a .NET class; the properties of the class represent the fields of the RECORD type or REF CURSOR result set. Oracle RECORD types are always represented as strongly-typed .NET classes. A REF CURSOR result set, however, can be represented as either strongly-typed or weakly-typed records based on whether the REF CURSOR itself is declared as strongly-typed or weakly-typed. The classes that represent REF CURSOR or RECORD type parameters (or return values) are generated in a unique namespace based on the procedure, function, or package. The following table shows these namespaces.  
  
|Oracle Artifact|Namespace|Example|  
|---------------------|---------------|-------------|  
|Procedure|[BASE_NS]. [SCHEMA].Procedure.[PROC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT.Procedure.MYPROC|  
|Function|[BASE_NS]. [SCHEMA].Function.[FUNC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT.Function.MYFUNC|  
|Package (Procedure)|[BASE_NS]. [SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC|  
|Package (Function)|[BASE_NS]. [SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC|  
|Generic Record Set (weakly-typed)|[BASE_NS]|microsoft.lobservices.oracledb._2007._03|  
  
 [BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.  
  
 [FUNC_NAME] = The name of an Oracle function; for example MYFUNC.  
  
 [PACKAGE_NAME] = The name of an Oracle package.  
  
 For information about how these namespaces are used for RECORD parameters, see [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md). For information about how these namespaces are used for REF CURSOR parameters, see [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).  
  
 In general, the Oracle parameters and return values are mapped as follows in the WCF client method:  
  
- Oracle IN parameters are mapped to .NET (input) parameters.  
  
- Oracle OUT parameters are mapped to .NET **out** parameters.  
  
- Oracle IN OUT parameters are mapped to .NET **ref** parameters.  
  
- Function RETURN values are mapped to the method return value.  
  
  However, two important exceptions exist:  
  
- Oracle IN OUT REF CURSOR parameters are split into an input string and an output (**out**) record set. This is because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CUSROR parameters as strings and OUT REF CURSOR parameters as complex types (record sets), these cannot be combined into a single parameter.  
  
- The first OUT parameter in an Oracle procedure is mapped to the return value of the WCF client method. This is standard WCF behavior.  
  
  The following example shows part of a simple Oracle procedure (loaded in the SCOTT schema) and the signature of the WCF client method that is generated to invoke it. The Oracle procedure has three IN parameters, three IN OUT parameters, and three OUT parameters; however, the WCF client method does not map a parameter for the first OUT parameter. Instead it is mapped to the method return value.  
  
```  
CREATE or REPLACE PROCEDURE Sample_Procedure   
    (  
     INNUMBER      IN         NUMBER,  
     INVARCHAR     IN         VARCHAR2,  
     INDATE        IN         DATE,  
     INOUTNUMBER   IN OUT     NUMBER,  
     INOUTVARCHAR  IN OUT     VARCHAR,  
     INOUTDATE     IN OUT     DATE,  
     OUTNUMBER     OUT        NUMBER,  
     OUTVARCHAR    OUT        VARCHAR2,  
     OUTDATE       OUT        DATE  
    ) AS   
    BEGIN  
  
        ...  
  
    END;  
    /  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTProcedureClient : System.ServiceModel.ClientBase<SCOTTProcedure>, SCOTTProcedure {  
  
    public System.Nullable<decimal> SAMPLE_PROCEDURE  
       (  
        System.Nullable<decimal> INNUMBER,   
        string INVARCHAR,   
        System.Nullable\<System.DateTime\> INDATE,   
        ref System.Nullable<decimal> INOUTNUMBER,   
        ref string INOUTVARCHAR,   
        ref System.Nullable\<System.DateTime\> INOUTDATE,   
        out string OUTVARCHAR,   
        out System.Nullable\<System.DateTime\> OUTDATE  
        );  
}  
```  
  
### Support for Overloaded Procedures, Functions and Packages  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports overloaded procedures, functions, and packages by appending a unique string to the node ID and the namespace that it surfaces for each overloaded artifact. This string is "overload1" for the first overload, "overload2" for the next overload, and so on.  
  
 In the WCF service model each overloaded procedure or function is represented by a unique WCF client. This is different from the non-overloaded case in which all of the functions in a SCHEMA, all of the procedures in a SCHEMA, or all of the procedures and functions in a PACKAGE are invoked by the same WCF client. The following table shows the WCF client name and method generated for overloaded procedures, functions, and packages.  
  
|Oracle Artifact|WCF Client Name|Example|  
|---------------------|---------------------|-------------|  
|Overloaded Package (Procedure)|[SCHEMA]Package[PACKAGE_NAME][PROC_NAME] ][OVERLOAD_ID]Client.[PROC_NAME]|SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC|  
|Overloaded Package (Function)|[SCHEMA]Package[PACKAGE_NAME][FUNC_NAME] ][OVERLOAD_ID]Client.[FUNC_NAME]|SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC|  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.  
  
 [FUNC_NAME] = The name of an Oracle function; for example MYFUNC.  
  
 [PACKAGE_NAME] = The name of an Oracle package.  
  
 [OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on.  
  
 The following table shows the namespace generated for overloaded procedures, functions, and packages.  
  
|Oracle Artifact|Namespace|Example|  
|---------------------|---------------|-------------|  
|Package (Procedure)|[BASE_NS]. [SCHEMA].Package.[PACKAGE_NAME].[PROC_NAME] [OVERLOAD_ID]|microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYPROC.overload1|  
|Package (Function)|[BASE_NS]. [SCHEMA].Package.[PACKAGE_NAME].[FUNC_NAME].[OVERLOAD_ID]|microsoft.lobservices.oracledb._2007._03.SCOTT.Package.MYPACKAGE.MYFUNC.overload1|  
|Generic Record Set (weakly-typed)|[BASE_NS]|microsoft.lobservices.oracledb._2007._03|  
  
 [BASE_NS] = The base adapter namespace; microsoft.lobservices.oracledb._2007._03.  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [PROC_NAME] = The name of an Oracle procedure; for example; MYPROC.  
  
 [FUNC_NAME] = The name of an Oracle function; for example MYFUNC.  
  
 [PACKAGE_NAME] = The name of an Oracle package.  
  
 [OVERLOAD_ID] = The unique string that identifies the overloaded artifact; "overload1", "overload2", and so on. The numeric value in the string is the overload ID for the artifact maintained by the Oracle database.  
  
 The following example shows the WCF clients and the method signatures generated for the overloaded GET_ACCOUNT procedure in the ACCOUNT_PKG package. (The Oracle declarations are included.) This example shows how a unique WCF client is generated for each overload and how the method generated for each client returns a record set in a unique namespace.  
  
```  
/* Procedure that takes account ID and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aid IN account.acctid%TYPE, acct OUT account%ROWTYPE) ;  
  
/* Procedure that takes account name and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aname IN account.name%TYPE, acct OUT account%ROWTYPE) ;  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1.ACCTRECORD GET_ACCOUNT(System.Nullable<decimal> AID);  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2.ACCTRECORD GET_ACCOUNT(string ANAME);  
}  
```  
  
## Invoking Functions and Procedures  
 To invoke a function or a procedure by using a WCF client, perform the following steps.  
  
1. Generate a WCF client class for the target function, procedure, or package. This class should contain methods for the operations that you will invoke on the target artifact.  
  
   > [!NOTE]
   >  In the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], overloaded functions and procedures appear in the **Available categories and operations** box as [NAME].1, [NAME].2, [NAME].3, and so on, where [NAME] is the name of the overloaded artifact and the numeric value is the overload ID on the Oracle database.  
  
2. Create an instance of the WCF client class and call its methods to invoke the function or procedure.  
  
   For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).  
  
   The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database.  
  
> [!IMPORTANT]
>  The classes that represent REF CURSOR and RECORD type parameters or return values in functions or procedures (and packages) are declared in a unique namespace for each function or procedure. This means, for example, that a PACKAGE REF CURSOR type that is used as a return value in two different functions will be declared in a unique namespace for each WCF client method. You must either declare separate variables to hold these different return values or appropriately cast the variable when you invoke one of the WCF client methods.  
  
 The following example demonstrates calling the overloaded /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT procedure to get account records from the /SCOTT/ACCOUNT table. First a new record is created by calling the /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT procedure. Then the new record is read back twice by calling different overloads of GET_ACCOUNT. This example uses three WCF clients, one for the CREATE_ACCOUNT procedure and one each for the GET_ACCOUNT overloads. Aliases are used to distinguish between namespaces used for the return value of GET_ACCOUNT. A full sample is available in the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// Alias client namespaces to shorten declarations of "shared" types   
using CREATE_ACCOUNTns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT;  
using GET_ACCOUNT_BY_IDns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1;  
using GET_ACCOUNT_BY_NAMEns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2;  
  
// This sample demonstrates calling overloaded packaged procedures on Oracle  
// First a new account is created by calling CREATE_ACCOUNT which takes two record parameters  
// Then the information for the new account is returned by calling an overloaded procedure GET_ACCOUNT  
// The first overload returns the account information by account ID  
// The second overload returns the account information by account name  
// Notice that different clients (and namespaces) are created for overloaded procedures and functions  
namespace OracleOverloadsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            decimal acctId;  
            string newAccountName = "Paula Bento";  
  
            Console.WriteLine("Creating clients");  
            // Create Client for CREATE_ACCOUNT Function  
            SCOTTPackageACCOUNT_PKGClient createAccountClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // NOTE: user name and password are case-sensitive  
            createAccountClient.ClientCredentials.UserName.UserName = "SCOTT";  
            createAccountClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 1 -- takes ACCOUNT ID parameter  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client getAccountByIdClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1");  
            // NOTE: user name and password are case-sensitive  
            getAccountByIdClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByIdClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 2 -- takes ACCOUNT NAME parameter  
            // NOTE: this client can be created from configuration; detail provided here  
            // for demonstration  
            OracleDBBinding overload2Binding = new OracleDBBinding();  
            EndpointAddress overload2EndpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client getAccountByNameClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client(overload2Binding, overload2EndpointAddress);  
            // NOTE: user name and password are case-sensitive  
            getAccountByNameClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByNameClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
                Console.WriteLine("Opening clients -- please wait");  
                // Open clients  
                createAccountClient.Open();  
                getAccountByIdClient.Open();  
                getAccountByNameClient.Open();  
  
                Console.WriteLine("Creating new account");  
                // Create an account record  
                // NOTE: ACCTRECORD is defined in all three namespaces so specify the definition  
                // that corresponds to the client.  
                CREATE_ACCOUNTns.ACCTRECORD acctRec = new CREATE_ACCOUNTns.ACCTRECORD();  
  
                // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
                acctRec.ACCTID = 0;  
                acctRec.NAME = newAccountName;  
                acctRec.BALANCE = 10537;  
  
                // Create address record  
                CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
                addrRec.STREET = "456 Valley Rd";  
                addrRec.CITY = "New York";  
                addrRec.STATE = "NY";  
  
                // Create account  
                acctId = (decimal)createAccountClient.CREATE_ACCOUNT(acctRec, addrRec);  
                Console.WriteLine("New Account Created: AccountId = {0}, Name = {1}, Balance = {2:C}",  
                   acctId, acctRec.NAME, acctRec.BALANCE);  
  
                /* Get new account by Id */  
                GET_ACCOUNT_BY_IDns.ACCTRECORD acctById = getAccountByIdClient.GET_ACCOUNT(acctId);  
                Console.WriteLine("Account Returned by Id: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctById.ACCTID, acctById.NAME, acctById.BALANCE);  
  
                /* Get new account by Name */  
                GET_ACCOUNT_BY_NAMEns.ACCTRECORD acctByName = getAccountByNameClient.GET_ACCOUNT(newAccountName);  
                Console.WriteLine("Account Returned by Name: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctByName.ACCTID, acctByName.NAME, acctByName.BALANCE);  
  
                Console.WriteLine("Hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close all the clients  
                createAccountClient.Close();  
                getAccountByIdClient.Close();  
                getAccountByNameClient.Close();  
            }  
  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)