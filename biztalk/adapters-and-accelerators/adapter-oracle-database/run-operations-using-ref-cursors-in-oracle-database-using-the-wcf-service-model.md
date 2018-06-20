---
title: "Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, performing operations using REF CURSORS"
  - "REF CURSORS, performing operations"
ms.assetid: b4cb9ede-eae1-44d7-8ba5-7e1261ccfa3b
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model
A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database. The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports REF CURSOR parameters in procedures, functions, and packages. REF CURSOR parameters can be strongly-typed or weakly-typed depending on how they are declared in the procedure or function. For a detailed explanation of how REF CURSOR parameters are represented by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for REF CURSORS](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).The following table summarizes how REF CURSOR parameters are represented in the WCF service model.  
  
|Parameter Direction|Strongly-typed REF CURSOR|Weakly-typed REF CURSOR|  
|-------------------------|--------------------------------|------------------------------|  
|IN|`string [PARAM_NAME]`<br /><br /> String that contains a PL/SQL block. The PL/SQL block must return an opened REF CURSOR either by executing an "OPEN FOR SELECT" statement or by invoking a function or procedure. A question mark (?) indicates the position of the REF CURSOR that returns the parameter. For example, "BEGIN OPEN ? FOR SELECT * FROM MY_TABLE; END", or "BEGIN MY_PROC(PARM1, ?, PARM2); END;".|Same as strongly-typed|  
|OUT|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> A strongly-typed record set.|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> A weakly-typed generic record set.|  
|IN OUT|IN OUT REF CURSOR parameters are split into an IN and an OUT parameter. The IN parameter is appended with "_IN" in the method signature to distinguish it from the OUT parameter. The OUT parameter is represented by a strongly-typed record set.<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|IN OUT REF CURSOR parameters are split into an IN and an OUT parameter. The IN parameter is appended with "_IN" to distinguish it from the OUT parameter. The OUT parameter is represented by a weakly-typed record set.<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 [PARAM_NAME] = the name of the parameter in the function or procedure definition on the Oracle database; for example, MYREFCURSOR.  
  
 [PROC_NS] = The unique namespace generated to contain parameters of the package, procedure, or function; for example, "microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY".  
  
 [GENERIC_NS] = The namespace in which the generic record set is defined, "microsoft.lobservices.oracledb._2007._03".  
  
## About the Examples Used in this Topic  
 The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG Oracle PACKAGE. The following procedure is used from ACCOUNT_PKG:  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 A script to generate this package is supplied with the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
## REF CURSOR Parameters in the WCF Service Model  
 The following examples show the classes and WCF client generated for the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure. This procedure has weakly-typed IN and OUT REF CURSOR parameters and a strongly-typed IN OUT REF CURSOR parameter.  
  
 Here is the signature of the method that is generated in the WCF client to invoke GET_ACTIVITY.  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 In the **GET_ACTIVITY** method, the IN OUT parameter INOUTRECS is split into two parameters:  
  
- INOUTRECS_IN is a string that represents an IN REF CURSOR parameter.  
  
- INOUTRECS is a strongly-typed record set that represents an OUT REF CURSOR parameter.  
  
  The weakly-typed OUT parameter, OUTRECS, is represented as a generic record set. The weakly-typed IN parameter, INRECS, is represented as a string.  
  
### Strongly-Typed OUT REF CURSOR Parameters  
 Strongly-typed OUT (or IN OUT) REF CURSOR parameters are generated in a unique namespace based on the SCHEMA, PACKAGE, and name of the procedure or function in which they are used. For the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure, this namespace is `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`. The class name is formed by appending the name of the parameter with "RECORD" and the class is composed of properties that represent the Oracle fields. The following shows a part of the class that represents the strongly-typed records generated for the INOUTRECS REF CURSOR parameter.  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class INOUTRECSRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private System.Nullable<decimal> TIDField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public System.Nullable<decimal> TID {  
            get {  
                return this.TIDField;  
            }  
            set {  
                this.TIDField = value;  
            }  
        }  
  
        ...  
  
    }  
}  
```  
  
### Weakly-Typed OUT REF CURSOR Parameters  
 Weakly-typed OUT (or IN OUT) REF CURSOR parameters are represented by the generic record class. The generic record set is always generated in the same namespace and with the same class name regardless of the function or procedure. The following code shows the generic record class, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, which represents the records for the OUTRECS OUT SYS_REFCURSOR parameter (weakly-typed).  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordRow : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumnField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumn {  
            get {  
                return this.GenRecordColumnField;  
            }  
            set {  
                this.GenRecordColumnField = value;  
            }  
        }  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordColumn : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private string ColumnNameField;  
  
        private string ColumnValueField;  
  
        private string ColumnTypeField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false)]  
        public string ColumnName {  
            get {  
                return this.ColumnNameField;  
            }  
            set {  
                this.ColumnNameField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public string ColumnValue {  
            get {  
                return this.ColumnValueField;  
            }  
            set {  
                this.ColumnValueField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false, Order=2)]  
        public string ColumnType {  
            get {  
                return this.ColumnTypeField;  
            }  
            set {  
                this.ColumnTypeField = value;  
            }  
        }  
    }  
}  
```  
  
## Using REF CURSOR Parameters with a WCF Client  
 To invoke a procedure or function with REF CURSOR parameters by using a WCF client, you do the following:  
  
1. Pass a string for each IN or IN OUT REF CURSOR parameter that contains the PL/SQL block to open the REF CURSOR. This block can either execute an OPEN FOR SELECT statement or invoke a function or procedure that returns an opened REF CURSOR in an OUT parameter.  
  
2. When the procedure or function returns, operate on the data in the record sets returned for any OUT or IN OUT REF CURSOR parameters. The record set will be a generic record set for weakly-typed REF CURSOR parameters or a strongly-typed record set for strongly-typed REF CURSOR parameters.  
  
   For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
   The following example calls the GET_ACTIVITY procedure. It demonstrates both ways of specifying an IN REF CURSOR parameter:  
  
- For the IN REF CURSOR parameter, an OPEN FOR SELECT statement is specified to return activity for ACCOUNT 100001.  
  
- For the IN OUT REF CURSOR parameter, the /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY procedure is invoked. This procedure opens a REF CURSOR that contains all of the activity in the ACCOUNTACTIVITY table and returns it as an OUT parameter.  
  
  The example also demonstrates how to read data from the record set returned for both strongly-typed and weakly-typed REF CURSOR parameters.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// namespaces for strongly-typed and weakly typed REF CURSOR records  
using GET_ACTIVITYns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY;  
using GENERICns = microsoft.lobservices.oracledb._2007._03;  
  
// In this sample, INRECS is opened by using an OPEN FOR statement, and  
// INOUTRECS_IN is opened by calling the GET_ALL_ACTIVITY procedure on Oracle.  
  
namespace OracleRefCursorsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the client  
            SCOTTPackageACCOUNT_PKGClient accountPkgClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // Set credentials  
            accountPkgClient.ClientCredentials.UserName.UserName = "SCOTT";  
            accountPkgClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
  
                GET_ACTIVITYns.INOUTRECSRECORD[] strongCursor;  
                GENERICns.GenRecordRow[] weakCursor;  
  
                Console.WriteLine("Opening client");  
                // Open the client  
                accountPkgClient.Open();  
  
                Console.WriteLine("Invoking ACCOUNT_PKG.GET_ACTIVITY");  
                // Get  ACCOUNTACTIVITY records  
                // The IN REF CURSOR is set to all activity for account 100001  
                // The input part of the IN OUT ref cursor calls GET_ALL_ACTIVITY  
                // The weakly-typed OUT REF CURSOR parameter returns a list of activity for account 100001  
                // The strongly-typed IN OUT REF CURSOR parameter returns a list of all activity  
                string inRecsString = "BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;";  
                string inoutRecsString = "BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;";  
  
                accountPkgClient.GET_ACTIVITY(  
                                inRecsString,  
                                inoutRecsString,  
                                out strongCursor,  
                                out weakCursor);  
  
                // Display strong ref cursor (all activity)  
                Console.WriteLine("\nList of all activity returned (strong ref cursor)");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < strongCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2:C}\t{3}\t{4}",strongCursor[i].TID,  
                        strongCursor[i].ACCOUNT,   
                        strongCursor[i].AMOUNT,   
                        strongCursor[1].TRANSDATE,  
                        strongCursor[i].DESCRIPTION);  
                }  
  
                // Display weak ref cursor (account 100001)  
                Console.WriteLine("\nList of activity for account 100001 returned (weak ref cursor)");  
                Console.WriteLine("Tx Id\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < weakCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1:C}\t{2}\t{3}", weakCursor[i].GenRecordColumn[0].ColumnValue,  
                        weakCursor[i].GenRecordColumn[2].ColumnValue,  
                        weakCursor[i].GenRecordColumn[4].ColumnValue,  
                        weakCursor[i].GenRecordColumn[3].ColumnValue);  
                }  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
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
                // Close the client  
                accountPkgClient.Close();  
            }  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database Application Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)