---
title: "How to Code a Transaction Integrator Application2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 319669d1-6eed-4eba-8859-67d865ab47a8
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Code a Transaction Integrator Application
Once you have deployed a Transaction Integrator (TI) component, you can write code against that component. Once you are finished writing your code, you can test your code, and if necessary modify the interface to the TI component.  
  
### To code a TI application  
  
1.  Create an instance of the TI object.  
  
     The TI object contains the interfaces that you will write code against. When your application calls an interface on the TI object, TI Manager will pass the information on to your remote server.  
  
2.  Set up your data variables.  
  
     As with many applications that use Host Integration Server, it is important that you use a data type that can successfully translate to and from your remote server. For more information on data types and how they map between systems, see [Data Types](./data-types1.md) and [Host and Automation Data](./host-and-automation-data2.md).  
  
3.  Make calls against any relevant parameters in the TI object.  
  
     Perform any actions necessary to your application, which will likely include calling the interfaces described by your TI object. You may also have additional tasks necessary for your application. For more information, see [Programming Windows-Initiated Processing](../core/programming-windows-initiated-processing1.md).  
  
4.  When writing your application, be sure to consider the relevant security details of your environment.  
  
## Example  
 The following example is cut from the main program code from the Discriminated Union tutorial in the SDK sample directory. For the complete code sample, see \<Installation Directory>\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\WindowsInitiated\DiscrimiatedUnion.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using Banking;  
  
namespace DiscriminatedUnions  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Processing Output only Account Information");  
            AccountInformationOutOnly();  
  
            Console.WriteLine("\n\nProcessing Input and Output Account Information");  
            AccountInformationInOut();  
  
            Console.WriteLine("\nPress any key to continue...");  
            Console.Read();  
  
        }  
  
        #region Output Only Discriminated Union Processing  
        static void AccountInformationOutOnly()  
        {  
            // Define an instance of the TI Banking object  
            Banking.Accounts MyBankObj = new Banking.Accounts();  
  
            // Call the Get Account Information method on the TI Object  
            // passing it the array that contains the checking and saving   
            // account information   
            string AccountNumber = "BNK4566112";  
            string AccountType = " ";  
            Object AcctInfoUnionObj = null;  
            string FillerNotUsedByThisSample = " ";  
  
            MyBankObj.GetAInfoOutOnly("111223333", AccountNumber, out AccountType, out AcctInfoUnionObj, out FillerNotUsedByThisSample);  
            switch (AcctInfoUnionObj.GetType().ToString())  
            {  
                // check the type of the union that was returned to determine   
                // whether the array element  
                // is a checking or saving account so that the correct  
                // structure of the union can be used  
                case "Banking.CHECKING":  
                        Banking.CHECKING ChkInfo = (Banking.CHECKING)AcctInfoUnionObj;  
  
                        Console.WriteLine("Checking account number: {0}", AccountNumber);  
                        Console.WriteLine("\tOverdraft charge:\t {0,10:C2}", ChkInfo.CHK_OD_CHG);  
                        Console.WriteLine("\tOverdraft limit:\t {0,10:C2}", ChkInfo.CHK_OD_LIMIT);  
                        Console.WriteLine("\tLinked account:\t {0,18}", ChkInfo.CHK_OD_LINK_ACCT);  
                        Console.WriteLine("\tLast Statement:\t {0,18}", ChkInfo.CHK_LAST_STMT);  
                        Console.WriteLine("\tDetail Items:\t {0,18:F0}", ChkInfo.CHK_DETAIL_ITEMS);  
                        Console.WriteLine("\tBalance:\t {0,18:C2}\n", ChkInfo.CHK_BAL);  
                    break;  
  
                case "Banking.SAVINGS":  
                        Banking.SAVINGS SavInfo = (Banking.SAVINGS)AcctInfoUnionObj;  
  
                        Console.WriteLine("Savings account number: {0}", AccountNumber);  
                        Console.WriteLine("\tInterest rate:\t {0,20:P}", SavInfo.SAV_INT_RATE / 100);  
                        Console.WriteLine("\tService charge:\t {0,18:C2}", SavInfo.SAV_SVC_CHRG);  
                        Console.WriteLine("\tLast Statement:\t {0,18}", SavInfo.SAV_LAST_STMT);  
                        Console.WriteLine("\tDetail Items:\t {0,18:F0}", SavInfo.SAV_DETAIL_ITEMS);  
                        Console.WriteLine("\tBalance:\t {0,18:C2}\n", SavInfo.SAV_BAL);  
                    break;  
  
                default:  
                    break;  
            }  
        }  
        #endregion Output Only Discriminated Union Processing  
    }  
}  
```  
  
 Optional comments.  
  
## See Also  
 [How to Create a New Host Integration Server Designer Project](../core/how-to-create-a-new-host-integration-server-designer-project1.md)